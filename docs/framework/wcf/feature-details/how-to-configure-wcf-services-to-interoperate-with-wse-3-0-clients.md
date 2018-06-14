---
title: HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 174ecd279f9380136532ce0d5105b7a71b6d88da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495105"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
Windows Communication Foundation (WCF) 服務是與 Web Services Enhancements 3.0 for Microsoft.NET (WSE) 用戶端的連線層級相容，當 WCF 服務會設定為使用 August 2004 Ws-addressing 規格版本。  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>讓 WCF 服務與 WSE 3.0 用戶端相互操作  
  
1.  定義自訂繫結的 WCF 服務。  
  
     若要指定使用 WS-Addressing August 2004 版本規格進行訊息編碼，這時必須要建立自訂繫結。  
  
    1.  新增子系[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)至[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)服務的組態檔。  
  
    2.  加入指定的繫結，名稱[\<繫結 >](../../../../docs/framework/misc/binding.md)至[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)和設定`name`屬性。  
  
    3.  指定驗證模式和 Ws-security 規格，可用來保護訊息藉由新增子系與 WSE 3.0 相容的新版[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)至[ \<繫結 >](../../../../docs/framework/misc/binding.md)。  
  
         若要設定驗證模式，請設定`authenicationMode`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。 驗證模式約略相等於 WSE 3.0 中的組合安全性判斷提示 (Assertion)。 下表會將驗證模式，在 WCF 中的對應至在 WSE 3.0 通行安全性判斷提示。  
  
        |WCF 驗證模式|WSE 3.0 組合安全性判斷提示|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* 其中一個主要差異`mutualCertificate10Security`和`mutualCertificate11Security`通行安全性判斷提示是 WSE 用來保護 SOAP 訊息安全的 Ws-security 規格的版本。 若是 `mutualCertificate10Security` 會使用 WS-Security 1.0，若是 `mutualCertificate11Security` 則使用 WS-Security 1.1。 WCF，Ws-security 規格的版本以指定`messageSecurityVersion`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。  
  
         若要設定用來保護 SOAP 訊息安全的 Ws-security 規格的版本，設定`messageSecurityVersion`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。 為了與 WSE 3.0 進行相互操作，`messageSecurityVersion` 屬性的值要設定為 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。  
  
    4.  指定 August 2004 版本的 Ws-addressing 規格會由 WCF 藉由新增[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)並設定`messageVersion`為其值，以<xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>。  
  
        > [!NOTE]
        >  如果使用的是 SOAP 1.2，請將 `messageVersion` 屬性設為 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。  
  
2.  指定服務使用自訂繫結。  
  
    1.  設定`binding`屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)元素`customBinding`。  
  
    2.  設定`bindingConfiguration`屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目中指定的值`name`屬性[\<繫結 >](../../../../docs/framework/misc/binding.md)自訂繫結。  
  
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
 [如何：自訂系統提供的繫結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
