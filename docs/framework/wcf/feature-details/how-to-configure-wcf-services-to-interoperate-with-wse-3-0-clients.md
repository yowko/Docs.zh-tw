---
title: HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 600b9c28d92f9e2b6e4d586b052cc5762d591521
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599057"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作

當 WCF 服務設定為使用 WS-ADDRESSING 規格的8月2004版時，Windows Communication Foundation （WCF）服務的連線層級與 Microsoft .NET （WSE）用戶端的 Web 服務增強3.0 相容。

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>讓 WCF 服務與 WSE 3.0 用戶端相互操作

1. 定義 WCF 服務的自訂系結。

    若要指定使用 WS-Addressing August 2004 版本規格進行訊息編碼，這時必須要建立自訂繫結。

    1. 將子系新增 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 至 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 服務設定檔的。

    2. 將加入 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 至， [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 並設定屬性，以指定系結的名稱 `name` 。

    3. 將子系新增至，以指定用來保護與 WSE 3.0 相容之訊息的驗證模式和版本的 WS-安全性規格 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 。

        若要設定驗證模式，請設定的 `authenticationMode` 屬性 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 。 驗證模式約略相等於 WSE 3.0 中的組合安全性判斷提示 (Assertion)。 下表將 WCF 中的驗證模式對應到 WSE 3.0 中的安全判斷提示。

        |WCF 驗證模式|WSE 3.0 組合安全性判斷提示|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*和通行安全性判斷提示之間的主要差異之一， `mutualCertificate10Security` `mutualCertificate11Security` 是 WSE 用來保護 SOAP 訊息安全的 WS-安全性規格版本。 若是 `mutualCertificate10Security` 會使用 WS-Security 1.0，若是 `mutualCertificate11Security` 則使用 WS-Security 1.1。 針對 WCF，會在的屬性中指定 WS-Security 規格的版本 `messageSecurityVersion` [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 。

        若要設定用來保護 SOAP 訊息安全的 WS-Security 規格版本，請設定的 `messageSecurityVersion` 屬性 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 。 為了與 WSE 3.0 進行相互操作，`messageSecurityVersion` 屬性的值要設定為 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。

    4. 藉由加入 [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) ，並將設 `messageVersion` 為其值，以指定由 WCF 使用 ws-addressing 規格的2004年8月版本 <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> 。

        > [!NOTE]
        > 如果使用的是 SOAP 1.2，請將 `messageVersion` 屬性設為 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。

2. 指定服務使用自訂繫結。

    1. 將 `binding` 元素的屬性設定 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) 為 `customBinding` 。

    2. 將 `bindingConfiguration` 元素的屬性設定 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) 為 `name` 自訂系結之的屬性中所指定的值 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 。

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

## <a name="see-also"></a>請參閱

- [HOW TO：自訂系統提供的繫結](../extending/how-to-customize-a-system-provided-binding.md)
