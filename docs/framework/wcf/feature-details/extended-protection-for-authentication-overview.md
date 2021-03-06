---
title: "인증에 대한 확장된 보호 개요"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d8dadf09434778bc32bb75c5eff5ff4cb0494373
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2017
---
# <a name="extended-protection-for-authentication-overview"></a>인증에 대한 확장된 보호 개요
인증에 대한 보호를 강화하면 공격자가 클라이언트의 자격 증명을 가로채서 서버로 전달하는 MITM(Man-In-The-Middle) 공격을 방지할 수 있습니다.  
  
 클라이언트, 서버, 공격자의 세 참가자가 있는 시나리오를 가정해 보겠습니다. 서버의 URL은 `https://server`이고 공격자의 URL은 `https://attacker`입니다. 공격자는 자신의 URL을 서버인 것처럼 가장하여 클라이언트가 액세스하도록 한 다음 서버로 요청을 보냅니다. 공격자가 보안 리소스에 액세스하려고 하면 서버에서는 WWW-Authenticate 헤더를 사용해 공격자에게 회신을 보냅니다. 공격자에게는 인증 정보가 없으므로 서버는 WWW-Authenticate 헤더를 클라이언트에게 보냅니다. 그러면 클라이언트가 Authorization 헤더를 공격자에게 보내고, 공격자는 이 헤더를 서버로 보내 클라이언트의 자격 증명으로 보안 리소스에 액세스하게 됩니다.  
  
 현재는 클라이언트 응용 프로그램이 Kerberos, 다이제스트 또는 NTLM(HTTPS 사용)을 통해 서버에 인증할 때 TLS(전송 수준 보안) 채널이 먼저 설정되며 이 채널을 사용해 인증이 진행됩니다. 그러나 SSL(Secure Sockets Layer)을 통해 생성되는 세션 키와 인증 중에 생성되는 세션 키는 서로 바인딩되지 않습니다. 따라서 위의 시나리오에서 HTTPS 채널 등의 TLS를 통해 통신이 수행되는 경우 SSL 채널이 두 개(클라이언트와 공격자 간에 하나, 공격자와 서버 간에 하나) 만들어집니다. 클라이언트의 자격 증명은 클라이언트에서 서버로 전송될 때 먼저 클라이언트와 공격자 간의 SSL 채널을 통해 전송된 다음, 공격자와 서버 간의 채널을 통해 전송됩니다. 클라이언트의 자격 증명이 서버에 도달하면 서버는 해당 자격 증명을 보내는 데 사용된 채널이 클라이언트의 채널이 아닌 공격자의 채널임을 검색하지 않고 자격 증명을 확인합니다.  
  
 이러한 공격을 방지하려면 TLS로 보호되는 외부 채널과 클라이언트가 인증한 내부 채널을 사용하고 서버로 CBT(채널 바인딩 토큰)를 전달합니다. CBT는 TLS로 보호되는 외부 채널의 속성으로, 클라이언트가 인증한 내부 채널을 통한 대화에 외부 채널을 바인딩하는 데 사용됩니다.  
  
 위의 시나리오에서 클라이언트와 공격자 간 TLS 채널의 CBT는 서버로 전송되는 권한 부여 정보에 병합됩니다. CBT를 인식하는 서버는 클라이언트 권한 부여 정보에 포함된 CBT(클라이언트와 공격자 간 채널에 해당함)를 공격자와 서버 간 채널에 연결된 CBT와 비교합니다. CBT는 채널 대상별로 다르므로 클라이언트와 공격자 간 CBT는 공격자와 서버 간 CBT와 일치하지 않습니다. 따라서 서버가 MITM 공격을 검색하여 인증 요청을 거부할 수 있습니다.  
  
 클라이언트측은 구성 설정이 필요하지 않습니다. 클라이언트는 CBT를 서버로 전달하도록 업데이트되면 항상 CBT를 서버로 전달합니다. 서버도 업데이트된 경우에는 CBT를 사용하거나 무시하도록 구성할 수 있습니다. 서버가 업데이트되지 않은 경우에는 CBT가 무시됩니다.  
  
 서버는 다음과 같은 보호 수준을 사용할 수 있습니다.  
  
-   없음 채널 바인딩 유효성 검사가 수행되지 않습니다. 업데이트되지 않은 모든 서버의 기본 동작입니다.  
  
-   부분. 업데이트된 모든 클라이언트는 채널 바인딩 정보를 서버에 제공해야 합니다. 업데이트되지 않은 클라이언트는 해당 정보를 제공하지 않아도 됩니다. 응용 프로그램 호환성을 허용하는 중간 옵션입니다.  
  
-   전체. 모든 클라이언트는 채널 바인딩 정보를 제공해야 합니다. 서버는 채널 바인딩 정보를 제공하지 않는 클라이언트의 인증 요청을 거부합니다.  
  
 자세한 내용은 Win7 CBT/Extended Protection 샘플을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Server App Fabric에 대 한 보안 모델](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
