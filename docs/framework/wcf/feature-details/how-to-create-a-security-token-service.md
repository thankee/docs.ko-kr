---
title: "방법: 보안 토큰 서비스 만들기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "페더레이션"
  - "WCF, 페더레이션"
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
caps.latest.revision: 12
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# 방법: 보안 토큰 서비스 만들기
보안 토큰 서비스에서는 WS\-Trust 사양에 정의된 프로토콜을 구현합니다.이 프로토콜은 보안 토큰의 발행, 갱신, 취소 및 유효성 검사를 위한 메시지 형식 및 메시지 교환 패턴을 정의합니다.지정된 보안 토큰 서비스에서는 하나 이상의 이러한 기능을 제공합니다.이 항목에서는 가장 일반적인 시나리오인 토큰 발급 구현에 대해 살펴봅니다.  
  
## 토큰 발급  
 WS\-Trust는 `RequestSecurityToken` XSD\(XML 스키마 정의 언어\) 스키마 요소에 따라 메시지 형식을 정의하고, 토큰 발행을 수행하기 위한 `RequestSecurityTokenResponse` XSD 스키마 요소를 정의합니다.또한 연결된 동작 URI\(Uniform Resource Identifier\)도 정의합니다.`RequestSecurityToken` 메시지와 연결된 동작 URI는 http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/trust\/RST\/Issue입니다.`RequestSecurityTokenResponse` 메시지와 연결된 동작 URI는 http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/trust\/RSTR\/Issue입니다.  
  
### 요청 메시지 구조  
 일반적으로 발행 요청 메시지 구조는 다음과 같은 항목으로 구성됩니다.  
  
-   http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/trust\/Issue의 값이 있는 요청 형식 URI  
  
-   토큰 형식 URI.SAML\(Security Assertions Markup Language\) 1.1 토큰의 경우 이 URI의 값은 http:\/\/docs.oasis\-open.org\/wss\/oasis\-wss\-saml\-token\-profile\-1.1\#SAMLV1.1입니다.  
  
-   발행된 토큰과 연결될 키의 비트 수를 나타내는 키 크기 값  
  
-   키 형식 URI.대칭 키의 경우 이 URI의 값은 http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/trust\/SymmetricKey입니다.  
  
 또한 다음과 같은 몇 가지 다른 항목이 있을 수 있습니다.  
  
-   클라이언트에서 제공하는 키 자료  
  
-   발행된 토큰이 함께 사용될 대상 서비스를 나타내는 범위 정보  
  
 보안 토큰 서비스에서는 발행 응답 메시지를 만들 때 발행 요청 메시지의 정보를 사용합니다.  
  
## 응답 메시지 구조  
 일반적으로 발행 응답 메시지 구조는 다음과 같은 항목으로 구성됩니다.  
  
-   발행된 보안 토큰\(예: SAML 1.1 어설션\)  
  
-   보안 토큰에 연결된 증명 토큰.대칭 키의 경우 이 토큰이 키 자료의 암호화된 형식인 경우가 있습니다.  
  
-   발행된 보안 토큰에 대한 참조.일반적으로 보안 토큰 서비스에서는 발행된 토큰이 클라이언트가 보낸 다음 메시지에 나타나는 경우 사용할 수 있는 참조 및 해당 토큰이 다음 메시지에 나타나지 않는 경우 사용할 수 있는 다른 참조를 반환합니다.  
  
 또한 다음과 같은 몇 가지 다른 항목이 있을 수 있습니다.  
  
-   보안 토큰 서비스에서 제공한 키 자료  
  
-   공유 키를 계산하는 데 필요한 알고리즘  
  
-   발행된 토큰에 대한 수명 정보  
  
## 요청 메시지 처리  
 보안 토큰 서비스에서는 여러 요청 메시지를 조사하고 이 메시지에서 요청을 만족하는 토큰을 발행할 수 있음을 확인하여 발행 요청을 처리합니다.보안 토큰 서비스는 발행할 토큰을 만들기 전에 다음 사항을 결정해야 합니다.  
  
-   요청이 발행할 토큰에 대한 요청이 맞는지 여부  
  
-   보안 토큰 서비스에서 요청된 토큰 형식을 지원하는지 여부  
  
-   요청자가 요청을 할 수 있는 권한이 있는지 여부  
  
-   보안 토큰 서비스가 키 자료에 대한 요청자의 기대치를 충족할 수 있는지 여부  
  
 토큰을 만드는 데 있어 중요한 두 가지 사항은 토큰을 서명할 때 사용할 키와 공유 키를 암호화할 때 사용할 키를 결정하는 것입니다.클라이언트가 대상 서비스에 토큰을 제공하는 경우 해당 서비스가 신뢰하는 보안 토큰 서비스에서 토큰을 발행했음을 확인할 수 있도록 토큰에 서명해야 합니다.키 자료는 대상 서비스에서 해당 키 자료를 해독할 수 있는 방식으로 암호화해야 합니다.  
  
 SAML 어설션에 서명하려면 <xref:System.IdentityModel.Tokens.SigningCredentials> 인스턴스를 만들어야 합니다.이 클래스의 생성자는 다음 항목이 필요합니다.  
  
-   SAML 어설션에 서명하는 데 사용할 키에 대한 <xref:System.IdentityModel.Tokens.SecurityKey>  
  
-   사용할 서명 알고리즘을 식별하는 문자열  
  
-   사용할 다이제스트 알고리즘을 식별하는 문자열  
  
-   필요한 경우 어설션을 서명하는 데 사용할 키를 식별하는 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 공유 키를 암호화하려면 키 자료가 필요하며, 대상 서비스에서 공유 키를 해독하는 데 사용할 수 있는 키를 사용하여 공유 키를 암호화해야 합니다.일반적으로 대상 서비스의 공개 키가 사용됩니다.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 또한 암호화된 키에 대한 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>가 필요합니다.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 이 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>는 `SamlSubject`를 만드는 데 `SamlToken`의 일부로 사용됩니다.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Federation 샘플](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## 응답 메시지 만들기  
 보안 토큰 서비스에서 발행 요청을 처리하고 증명 키와 함께 발행될 토큰을 만들면 적어도 요청된 토큰, 증명 토큰 및 발행된 토큰 참조를 포함하여 응답 메시지를 만들어야 합니다.일반적으로 발행된 토큰은 다음 예제에서처럼 <xref:System.IdentityModel.Tokens.SamlAssertion>에서 만들어진 <xref:System.IdentityModel.Tokens.SamlSecurityToken>입니다.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 보안 토큰 서비스에서 공유 키 자료를 제공하는 경우에는 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>을 만들어 증명 토큰을 만듭니다.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 클라이언트와 보안 토큰 서비스에서 모두 공유 키 자료를 제공하는 경우 증명 토큰을 만드는 방법[!INCLUDE[crabout](../../../../includes/crabout-md.md)][Federation 샘플](../../../../docs/framework/wcf/samples/federation-sample.md)을 참조하십시오.  
  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> 클래스의 인스턴스를 만들어 발행된 토큰 참조를 만듭니다.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 이러한 여러 값은 클라이언트에 반환되는 응답 메시지로 serialize됩니다.  
  
## 예제  
 보안 토큰 서비스의 전체 코드를 보려면 [Federation 샘플](../../../../docs/framework/wcf/samples/federation-sample.md)을 참조하십시오.  
  
## 참고 항목  
 <xref:System.IdentityModel.Tokens.SigningCredentials>   
 <xref:System.IdentityModel.Tokens.SecurityKey>   
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>   
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>   
 <xref:System.IdentityModel.Tokens.SamlAssertion>   
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>   
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>   
 [Federation 샘플](../../../../docs/framework/wcf/samples/federation-sample.md)