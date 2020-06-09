---
title: HOW TO：建立雙工聯合繫結
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598966"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>HOW TO：建立雙工聯合繫結

<xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求/回覆訊息交換合約。 若要使用雙工訊息交換合約，必須建立自訂繫結。 下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。 這三種繫結方式的完整程式碼範例會列於本主題的結尾。

您也可以撰寫程式碼建立繫結。 如需要建立之繫結項目堆疊的說明，請參閱[如何：使用 SecurityBindingElement 建立自訂](how-to-create-a-custom-binding-using-the-securitybindingelement.md)系結。

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>若要以 HTTP 建立雙工聯合自訂繫結

1. 在 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的節點中，建立 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素。

2. 在 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素內，建立專案， [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 並將 `name` 屬性設定為 `FederationDuplexHttpMessageSecurityBinding` 。

3. 在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素內，建立專案， [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 並將 `authenticationMode` 屬性設定為 `SecureConversation` 。

4. 在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素內，建立專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated` 。

5. 在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素後面，建立空的專案 [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 。

6. 在 [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 元素後面，建立空的專案 [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) 。

7. 在 [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) 元素後面，建立空的專案 [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) 。

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結

1. 在 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的節點中，建立 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素。

2. 在 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素內，建立專案， [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 並將 `name` 屬性設定為 `FederationDuplexTcpMessageSecurityBinding` 。

3. 在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素內，建立專案， [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 並將 `authenticationMode` 屬性設定為 `SecureConversation` 。

4. 在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素內，建立專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated` 。

5. 在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素後面，建立空的專案 [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 。

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>若要以 TCP 混合安全性模式建立雙工聯合自訂繫結

1. 在 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的節點中，建立 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素。

2. 在 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素內，建立專案， [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 並將 `name` 屬性設定為 `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` 。

3. 在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素內，建立專案， [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 並將 `authenticationMode` 屬性設定為 `SecureConversation` 。

4. 在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素內，建立專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated` 。

5. 在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素後面，建立空的專案 [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) 。

6. 在 [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) 元素後面，建立空的專案 [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 。

## <a name="code-sample"></a>程式碼範例

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
