---
title: "HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務設定為使用 WS\-Addressing August 2004 版本規格時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的連線層級與 Microsoft .NET 用戶端的 Web Services Enhancements \(WSE\) 3.0 相容。  
  
### 讓 WCF 服務與 WSE 3.0 用戶端相互操作  
  
1.  定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的自訂繫結。  
  
     若要指定使用 WS\-Addressing August 2004 版本規格進行訊息編碼，這時必須要建立自訂繫結。  
  
    1.  將子系 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)新增到服務組態檔的 [\<繫結\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)。  
  
    2.  藉由將 [\<繫結\>](../../../../docs/framework/misc/binding.md)新增到 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)，並設定 `name` 屬性以指定繫結的名稱。  
  
    3.  藉由將子 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)新增到[\<繫結\>](../../../../docs/framework/misc/binding.md)，指定用來保護與 WSE 3.0 相容之訊息的驗證模式和 WS\-Security 規格版本。  
  
         若要設定驗證模式，請設定 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `authenicationMode` 屬性。驗證模式約略相等於 WSE 3.0 中的組合安全性判斷提示 \(Assertion\)。下表會將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的驗證模式對應到 WSE 3.0 中的組合安全性判斷提示。  
  
        |WCF 驗證模式|WSE 3.0 組合安全性判斷提示|  
        |--------------|-----------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`mutualCertificate10Security`\*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`mutualCertificate11Security`\*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`usernameForCertificateSecurity`|  
  
         \* `mutualCertificate10Security` 與 `mutualCertificate11Security` 組合安全性判斷提示之間的一項主要差異，在於 WSE 用來保護 SOAP 訊息安全的 WS\-Security 規格的版本。若是 `mutualCertificate10Security` 會使用 WS\-Security 1.0，若是 `mutualCertificate11Security` 則使用 WS\-Security 1.1。若是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，則會在[\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `messageSecurityVersion` 屬性中指定 WS\-Security 規格版本。  
  
         若要設定用來保護 SOAP 訊息安全的 WS\-Security 規格版本，請設定 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `messageSecurityVersion` 屬性。為了與 WSE 3.0 進行相互操作，`messageSecurityVersion` 屬性的值要設定為 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。  
  
    4.  藉由新增 [\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)，並將 `messageVersion` 的值設定為 <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>，以指定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 WS\-Addressing August 2004 版本規格。  
  
        > [!NOTE]
        >  如果使用的是 SOAP 1.2，請將 `messageVersion` 屬性設為 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。  
  
2.  指定服務使用自訂繫結。  
  
    1.  將[\<endpoint\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目的 `binding` 屬性設定為 `customBinding`。  
  
    2.  將自訂繫結的[\<endpoint\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目 `bindingConfiguration` 屬性，設定為[\<繫結\>](../../../../docs/framework/misc/binding.md)之 `name` 屬性中的指定值。  
  
## 範例  
 下列程式碼範例會指定 `Service.HelloWorldService` 使用自訂繫結來與 WSE 3.0 用戶端相互操作。自訂繫結會指定使用 WS\-Addressing August 2004 版本和 WS\-Security 1.1 的規格組合來編碼已交換訊息。這些訊息會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode> 驗證模式來加以保護。  
  
```  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        behaviorConfiguration="ServiceBehavior"   
        name="Service.HelloWorldService">  
        <endpoint binding="customBinding" address=""  
          bindingConfiguration="ServiceBinding"  
          contract="Service.IHelloWorld"></endpoint>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="ServiceBinding">  
          <security authenticationMode="AnonymousForCertificate"  
                  messageProtectionOrder="SignBeforeEncrypt"  
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"  
                  requireDerivedKeys="false">  
          </security>  
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">  
        <serviceCredentials>  
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>  
        </serviceCredentials>  
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## 請參閱  
 [HOW TO：自訂系統提供的繫結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)