---
title: HOW TO：建立雙面同盟繫結
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972065"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>HOW TO：建立雙面同盟繫結

<xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求/回覆訊息交換合約。 若要使用雙工訊息交換合約，必須建立自訂繫結。 下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。 這三種繫結方式的完整程式碼範例會列於本主題的結尾。

您也可以撰寫程式碼建立繫結。 如需要建立之繫結項目堆疊的說明, 請[參閱如何:使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)建立自訂系結。

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>若要以 HTTP 建立雙工聯合自訂繫結

1. 在配置[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [檔的[系結>]節點中,建立customBinding>元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

2. `name` `FederationDuplexHttpMessageSecurityBinding`[在 customBinding > 元素內, 建立系結 > 專案, 並將屬性設定為。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \< ](../../../../docs/framework/misc/binding.md)

3. 在系結 > 專案內, 建立[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案, 並`authenticationMode`將屬性設定`SecureConversation`為。 [ \< ](../../../../docs/framework/misc/binding.md)

4. `IssuedTokenForSslNegotiated` `IssuedTokenForCertificate` `authenticationMode` [在安全性>專案中,建立secureConversationBootstrap>元素,並將屬性設定為或。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)

5. [在\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面, 建立空[ \<的 compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)元素。

6. [在\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)元素後面, 建立空白[ \<的單向 >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)元素。

7. 在 [ [ \<單向 >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) ] 元素後面, 建立空[ \<的 HTTPTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)元素。

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結

1. 在配置[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [檔的[系結>]節點中,建立customBinding>元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

2. `name` `FederationDuplexTcpMessageSecurityBinding`[在 customBinding > 元素內, 建立系結 > 專案, 並將屬性設定為。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \< ](../../../../docs/framework/misc/binding.md)

3. 在系結 > 專案內, 建立[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案, 並`authenticationMode`將屬性設定`SecureConversation`為。 [ \< ](../../../../docs/framework/misc/binding.md)

4. `IssuedTokenForSslNegotiated` `IssuedTokenForCertificate` `authenticationMode` [在安全性>專案中,建立secureConversationBootstrap>元素,並將屬性設定為或。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)

5. [在\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面, 建立空[ \<的 tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)元素。

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>若要以 TCP 混合安全性模式建立雙工聯合自訂繫結

1. 在配置[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [檔的[系結>]節點中,建立customBinding>元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

2. `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`[在 customBinding > 元素內, 建立系結 > 專案, 並將屬性設定為。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \< ](../../../../docs/framework/misc/binding.md)

3. 在系結 > 專案內, 建立[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案, 並`authenticationMode`將屬性設定`SecureConversation`為。 [ \< ](../../../../docs/framework/misc/binding.md)

4. `IssuedTokenForSslNegotiated` `IssuedTokenForCertificate` `authenticationMode` [在安全性>專案中,建立secureConversationBootstrap>元素,並將屬性設定為或。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)

5. [在\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面, 建立空[ \<的 sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)元素。

6. [在\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)元素後面, 建立空[ \<的 tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)元素。

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
