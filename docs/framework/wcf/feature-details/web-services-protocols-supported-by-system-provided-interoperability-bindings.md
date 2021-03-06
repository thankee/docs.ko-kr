---
title: "시스템 제공 상호 운용성 바인딩에서 지원하는 웹 서비스 프로토콜"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1cc61b1b777de7149b8f12c0b2f6030b305a73c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2017
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>시스템 제공 상호 운용성 바인딩에서 지원하는 웹 서비스 프로토콜
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]는 웹 서비스 사양으로 알려진 일련의 사양을 지원하는 웹 서비스와 상호 운용되도록 만들어졌습니다. 최선의 상호 운용성 방법을 위해 서비스 구성을 단순화하기 위해 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 상호 운용 가능한 시스템 제공 바인딩인 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> 및 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>을 도입했습니다. OASIS(Organization for the Advancement of Structured Information Standards) 표준과의 상호 운용성을 위해 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에는 <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>이라는 하나의 상호 운용 가능한 시스템 제공 바인딩이 포함되어 있습니다. 메타 데이터 게시에 대 한 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 두 개의 상호 운용 가능한 시스템 제공 바인딩이 포함 되어 있습니다: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) 및 [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)합니다. 이 항목에서는 시스템에서 제공하는 상호 운용 가능한 바인딩이 지원하는 사양을 나열합니다.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>basicHttpBinding, wsHttpBinding, ws2007HttpBinding 및 wsDualHttpBinding Bindings에서 지원하는 웹 서비스 프로토콜  
  
### <a name="all-bindings"></a>모든 바인딩  
 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), 및 [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) 바인딩 지원의 다음 프로토콜입니다.  
  
> [!NOTE]
>  메타데이터 게시에 사용하는 바인딩에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 "시스템 제공 메타데이터 바인딩" 단원을 참조하십시오.  
  
|범주|프로토콜|사양 및 사용|  
|--------------|--------------|-----------------------------|  
|전송|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` 및 `WS2007HttpBinding`은 HTTP 및 HTTPS 전송을 사용합니다.|  
|메시징|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding` 및 `ws2007HttpBinding`은 MTOM(Message-Transmission Optimization Mechanism)을 지원합니다. 기본적으로 사용되지 않으며 MTOM을 사용하려면 `messageEncoding` 특성을 `"Mtom"`으로 설정하십시오.<br /><br /> 예제:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|메타데이터|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WSDL(웹 서비스 기술 언어)을 사용하여 서비스를 설명합니다.|  
|메타데이터|WS-Policy|[Ws-policy](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WS-Policy 사양을 도메인별 어설션과 함께 사용하여 서비스 요구 사항 및 기능에 대해 설명합니다.|  
|메타데이터|WS-Policy 1.5|[Ws-policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WS-Policy 사양을 도메인별 어설션과 함께 사용하여 서비스 요구 사항 및 기능에 대해 설명합니다.|  
|메타데이터|WS-PolicyAttachment|[Ws-policyattachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WS-PolicyAttachment를 구현하여 WSDL(웹 서비스 기술 언어)에서 다양한 범위의 정책 식을 연결합니다.|  
|메타데이터|WS-MetadataExchange|[Ws-metadataexchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WS-MetadataExchange를 구현하여 XML 스키마, WSDL 및 WS-Policy를 검색합니다.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|범주|프로토콜|사양 및 사용|  
|--------------|--------------|-----------------------------|  
|메시징|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Basic Profile 1.1에 따라 `basicHttpBinding` 요소는 SOAP 1.1 메시지 프로토콜을 구현합니다.|  
|보안|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> 기본 보안 프로필에 따라 `basicHttpBinding` 요소는 사용자 이름/암호 및 X.509 기반 보안을 위해 WSS(Web Services Security) SOAP Message Security 1.0 사양을 구현합니다.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|보안|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP 메시지 보안 프로필 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|보안|WSS SOAP 메시지 보안 X.509 인증서 토큰 프로필 1.0|[WSS SOAP 메시지 보안 X.509 인증서 토큰 프로필 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding 및 wsDualHttpBinding  
  
|범주|프로토콜|사양 및 사용|  
|--------------|--------------|-----------------------------|  
|메시징|SOAP 1.2|[입문](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [메시징 프레임 워크](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP 바인딩을 포함)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|메시징|Ws-addressing 2005/08|[웹 서비스 주소 지정 1.0-코어](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [웹 서비스 주소 지정 1.0-SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding` 및 `wsDualHttpBinding`은 W3C(World Wide Web Consortium) WS-Addressing 권장 사항을 구현하여 비동기 메시징, 메시지 상관 관계 및 전송 중립적 주소 지정 메커니즘을 사용할 수 있습니다.<br /><br /> WS-* 규격에서 WS-Addressing 헤더의 암호화를 허용하지만 WCF는 이를 지원하지 않습니다.|  
|메시징|WS-Addressing 1.0 - Metadata|[Ws-addressing 1.0 메타 데이터](http://www.w3.org/2007/05/addressing/metadata) ServiceMetadata 동작이-policyversion 1.2 (기본값)로 설정 된 정책 버전을 설정 하 여이 프로토콜에 대 한 지원을 사용 하면, wsdl 설명 Ws-addressing wsdl에 맞습니다.와 1.5로 설정 policyversion, wsdl 설명 ws-addressing 활성화 메타 데이터와 호환 됩니다.<br /><br /> WS-* 규격에서 WS-Addressing 헤더의 암호화를 허용하지만 WCF는 이를 지원하지 않습니다.|  
|보안|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> `securityMode` 특성이 "wsSecurityOverHttp"(기본값)로 설정되어 있고 매개 변수가 `wsSecurity` 자식 요소를 사용하여 구성되어 있을 경우 사용합니다.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|보안|WSS SOAP 메시지 보안 UsernameToken Profile 1.1|[WSS SOAP 메시지 보안 프로필 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> `wsSecurity` 요소의 `authenticationMode` 특성이 "Username"으로 설정된 경우 사용합니다.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|보안|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP 메시지 보안 X.509 인증서 토큰 프로필 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> `wsSecurity` 요소의 `authenticationMode` 특성이 "Username", "Certificate" 또는 "None"으로 설정된 경우 메시지 보호를 위해 사용합니다. 또한 `wsSecurity` 요소의 `authenticationMode` 특성이 "Certificate"으로 설정된 경우 클라이언트 인증을 위해 이를 사용합니다.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|보안|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP 메시지 보안 Kerberos 토큰 프로필 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> `wsSecurity` 요소의 `authenticationMode` 특성이 "Windows"로 설정된 경우 인증 및 메시지 보호를 위해 사용합니다.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|보안|WS-SecureConversation|[Ws-secureconversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> `security/@mode` 특성이 "Message"로 설정되어 있고 `message/@establishSecurityContext` 특성이 "true"(기본값)로 설정된 경우 보안 세션을 제공하기 위해 사용합니다.|  
|보안|WS-Trust|[WS-트러스트](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation에 의해 사용됩니다(위 참조).|  
|신뢰할 수 있는 메시징|WS-ReliableMessaging|[WS-RELIABLE Messaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> `reliableSession` 사용을 위해 바인딩을 구성할 때 사용합니다.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|트랜잭션|WS-AtomicTransaction|[Ws-atomictransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> 트랜잭션 관리자간 통신에 사용합니다. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 클라이언트와 서비스는 항상 로컬 트랜잭션 관리자를 사용합니다.|  
|트랜잭션|WS-Coordination|[Ws-coordination](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> `flowTransactions` 특성이 "Allowed" 또는 "Required"로 설정된 경우 트랜잭션 컨텍스트 이동을 위해 사용합니다.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding 및 ws2007FederationHttpBinding  
 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 및 [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) 지원을 제공 하기 위해 페더레이션된 시나리오에 대 한 여기서는 세 번째 요소 도입 파티는 클라이언트를 인증 하는 데 사용 되는 토큰을 발급 합니다. `wsHttpBinding`에서 사용하는 프로토콜과 함께 `wsFederationHttpBinding`에서 사용합니다.  
  
-   토큰 발급에 대한 `WS-Trust`입니다.  
  
-   가장 일반적으로 발급되는 토큰 형식에 대한 WSS SAML(Security Assertions Markup Language) Token Profile 1.0 및 1.1입니다.  
  
 예제:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][페더레이션](../../../../docs/framework/wcf/feature-details/federation.md) 합니다.  
  
## <a name="system-provided-metadata-bindings"></a>시스템 제공 메타데이터 바인딩  
 다음 표에서는 <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> 클래스에 의해 노출된, 시스템에서 제공하는 상호 운용 가능 메타데이터 바인딩에서 지원하는 프로토콜에 대해 설명합니다.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) 바인딩은 다음과 같은 프로토콜을 지원 합니다. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]이 바인딩을 사용 하 여 참조 [메타 데이터 게시](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)합니다.  
  
|범주|프로토콜|사양 및 사용|  
|--------------|--------------|-----------------------------|  
|전송|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|메시징|SOAP 1.2|[입문](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [메시징 프레임 워크](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP 바인딩을 포함)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|메시징|Ws-addressing 2005/08|[웹 서비스 주소 지정 1.0-코어](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [웹 서비스 주소 지정 1.0-SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|메타데이터|WS-MetadataExchange|[Ws-metadataexchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WS-MetadataExchange를 구현하여 XML 스키마, WSDL 및 WS-Policy를 검색합니다.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) 다음 프로토콜을 지원 합니다. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]이 바인딩을 사용 하 여 참조 [메타 데이터 게시](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)합니다.  
  
|범주|프로토콜|사양 및 사용|  
|--------------|--------------|-----------------------------|  
|전송|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> 전송 보안을 사용합니다.|  
|메시징|SOAP 1.2|[입문](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [메시징 프레임 워크](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP 바인딩을 포함)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|메시징|Ws-addressing 2005/08|[웹 서비스 주소 지정 1.0-코어](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [웹 서비스 주소 지정 1.0-SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|메타데이터|WS-MetadataExchange|[Ws-metadataexchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 WS-MetadataExchange를 구현하여 XML 스키마, WSDL 및 WS-Policy를 검색합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [시스템 제공 바인딩](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
