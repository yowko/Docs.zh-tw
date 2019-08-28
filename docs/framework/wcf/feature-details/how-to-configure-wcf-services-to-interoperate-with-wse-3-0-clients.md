---
title: HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 0349c9ba76b3f240bf98daa0e095b415bc98a87c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045942"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>作法：將 WCF 服務設為與 WSE 3.0 用戶端相互操作

當 WCF 服務設定為使用 WS-ADDRESSING 規格的8月2004版時, Windows Communication Foundation (WCF) 服務的連線層級與 Microsoft .NET (WSE) 用戶端的 Web 服務增強3.0 相容。

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>讓 WCF 服務與 WSE 3.0 用戶端相互操作

1. 定義 WCF 服務的自訂系結。

    若要指定使用 WS-Addressing August 2004 版本規格進行訊息編碼，這時必須要建立自訂繫結。

    1. 將子[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)新增至服務[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)設定檔的系結 >。

    2. 藉由將系結`name` [ \< ](../../../../docs/framework/misc/binding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) > 新增至 customBinding > 並設定屬性, 來指定系結的名稱。

    3. 藉由將子[ \< ](../../../../docs/framework/misc/binding.md) [ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)新增至系結 >, 指定用來保護與 WSE 3.0 相容之訊息的驗證模式和版本的 WS-安全性規格。

        若要設定驗證模式, 請設定`authenticationMode` [ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的屬性。 驗證模式約略相等於 WSE 3.0 中的組合安全性判斷提示 (Assertion)。 下表將 WCF 中的驗證模式對應到 WSE 3.0 中的安全判斷提示。

        |WCF 驗證模式|WSE 3.0 組合安全性判斷提示|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*`mutualCertificate10Security` 和`mutualCertificate11Security`通行安全性判斷提示之間的主要差異之一, 是 WSE 用來保護 SOAP 訊息安全的 WS-安全性規格版本。 若是 `mutualCertificate10Security` 會使用 WS-Security 1.0，若是 `mutualCertificate11Security` 則使用 WS-Security 1.1。 在 WCF 中, 會在`messageSecurityVersion` [ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的屬性中指定 WS-security 規格的版本。

        若要設定用來保護 SOAP 訊息安全的 WS-security 規格版本, 請設定`messageSecurityVersion` [ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的屬性。 為了與 WSE 3.0 進行相互操作，`messageSecurityVersion` 屬性的值要設定為 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。

    4. 藉由新增[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)並將設`messageVersion`為其值<xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>, 指定 WCF 使用的 ws-addressing 規格2004年8月版本。

        > [!NOTE]
        > 如果使用的是 SOAP 1.2，請將 `messageVersion` 屬性設為 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。

2. 指定服務使用自訂繫結。

    1. 將端點 > 元素的`binding`屬性`customBinding`設定為。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)

    2. [ \<](../../../../docs/framework/misc/binding.md)將端點 > `bindingConfiguration` 元素的屬性設定為自訂系結之系結>的屬性中`name`指定的值。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)

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

- [如何：自訂系統提供的系結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
