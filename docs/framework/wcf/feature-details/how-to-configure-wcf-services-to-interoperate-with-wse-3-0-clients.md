---
title: HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 24c44f415eff8518bcd73696c5cd9302371ad0c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177290"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
當 WCF 服務會設定為使用 August 2004 版本的 Ws-addressing 規格，Windows Communication Foundation (WCF) 服務將會與 Web Services Enhancements 3.0 for Microsoft.NET (WSE) 用戶端的連線層級相容性。  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>讓 WCF 服務與 WSE 3.0 用戶端相互操作  
  
1.  定義 WCF 服務的自訂繫結。  
  
     若要指定使用 WS-Addressing August 2004 版本規格進行訊息編碼，這時必須要建立自訂繫結。  
  
    1.  新增子系[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)服務的組態檔。  
  
    2.  指定繫結的名稱加上[\<繫結 >](../../../../docs/framework/misc/binding.md)要[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)並設定`name`屬性。  
  
    3.  指定驗證模式，以及用來保護藉由新增子系與 WSE 3.0 相容之訊息的 Ws-security 規格版本[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)到[ \<繫結 >](../../../../docs/framework/misc/binding.md)。  
  
         若要設定驗證模式，請設定`authenicationMode`的屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。 驗證模式約略相等於 WSE 3.0 中的組合安全性判斷提示 (Assertion)。 下表會對應到 WSE 3.0 通行安全性判斷提示的 WCF 中的驗證模式。  
  
        |WCF 驗證模式|WSE 3.0 組合安全性判斷提示|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* 其中一個主要差異`mutualCertificate10Security`和`mutualCertificate11Security`通行安全性判斷提示是 WSE 用來保護 SOAP 訊息安全的 Ws-security 規格版本。 若是 `mutualCertificate10Security` 會使用 WS-Security 1.0，若是 `mutualCertificate11Security` 則使用 WS-Security 1.1。 Wcf 中指定 Ws-security 規格版本`messageSecurityVersion`的屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。  
  
         若要設定用來保護 SOAP 訊息安全的 Ws-security 規格版本，設定`messageSecurityVersion`的屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。 為了與 WSE 3.0 進行相互操作，`messageSecurityVersion` 屬性的值要設定為 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。  
  
    4.  指定 August 2004 版本的 Ws-addressing 規格由 WCF 使用加上[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)並將`messageVersion`其值，以<xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>。  
  
        > [!NOTE]
        >  如果使用的是 SOAP 1.2，請將 `messageVersion` 屬性設為 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。  
  
2.  指定服務使用自訂繫結。  
  
    1.  設定`binding`的屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目`customBinding`。  
  
    2.  設定`bindingConfiguration`的屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)中指定之值的項目`name`屬性[\<繫結 >](../../../../docs/framework/misc/binding.md)自訂繫結。  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定 `Service.HelloWorldService` 使用自訂繫結來與 WSE 3.0 用戶端相互操作。 自訂繫結會指定使用 WS-Addressing August 2004 版本和 WS-Security 1.1 的規格組合來編碼已交換訊息。 這些訊息會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> 驗證模式來加以保護。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- [HOW TO：自訂系統提供的繫結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
