---
title: HOW TO：建立雙工聯合繫結
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141713"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>HOW TO：建立雙工聯合繫結

<xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求/回覆訊息交換合約。 若要使用雙工訊息交換合約，必須建立自訂繫結。 下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。 這三種繫結方式的完整程式碼範例會列於本主題的結尾。

您也可以撰寫程式碼建立繫結。 For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>若要以 HTTP 建立雙工聯合自訂繫結

1. In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.

2. Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.

3. 在\<系結[>](../../configure-apps/file-schema/wcf/bindings.md)元素內，建立[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案，並將 `authenticationMode` 屬性設定為 [`SecureConversation`]。

4. 在[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素內，建立[\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)專案，並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated`。

5. Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.

6. Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.

7. Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結

1. In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.

2. Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.

3. 在\<系結[>](../../configure-apps/file-schema/wcf/bindings.md)元素內，建立[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案，並將 `authenticationMode` 屬性設定為 [`SecureConversation`]。

4. 在[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素內，建立[\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)專案，並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated`。

5. Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>若要以 TCP 混合安全性模式建立雙工聯合自訂繫結

1. In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.

2. 在[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)元素內，建立\<系結[>](../../configure-apps/file-schema/wcf/bindings.md)專案，並將 `name` 屬性設定為 `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`。

3. 在\<系結[>](../../configure-apps/file-schema/wcf/bindings.md)元素內，建立[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案，並將 `authenticationMode` 屬性設定為 [`SecureConversation`]。

4. 在[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素內，建立[\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)專案，並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated`。

5. 在[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面，建立空的[\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)元素。

6. 在[\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)元素後面，建立空的[\<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)元素。

## <a name="code-sample"></a>範例程式碼

### <a name="sample-with-3-bindings"></a>3 個繫結的範例

1. 將下列程式碼插入組態檔。

## <a name="example"></a>範例

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
