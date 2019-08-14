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
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="9adc9-102">HOW TO：建立雙面同盟繫結</span><span class="sxs-lookup"><span data-stu-id="9adc9-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="9adc9-103"><xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求/回覆訊息交換合約。</span><span class="sxs-lookup"><span data-stu-id="9adc9-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="9adc9-104">若要使用雙工訊息交換合約，必須建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="9adc9-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="9adc9-105">下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="9adc9-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="9adc9-106">這三種繫結方式的完整程式碼範例會列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="9adc9-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="9adc9-107">您也可以撰寫程式碼建立繫結。</span><span class="sxs-lookup"><span data-stu-id="9adc9-107">You can also create the binding in code.</span></span> <span data-ttu-id="9adc9-108">如需要建立之繫結項目堆疊的說明, 請[參閱如何:使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)建立自訂系結。</span><span class="sxs-lookup"><span data-stu-id="9adc9-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="9adc9-109">若要以 HTTP 建立雙工聯合自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9adc9-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="9adc9-110">在配置[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [檔的[系結>]節點中,建立customBinding>元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="9adc9-111">`name` `FederationDuplexHttpMessageSecurityBinding`[在 customBinding > 元素內, 建立系結 > 專案, 並將屬性設定為。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \< ](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="9adc9-112">在系結 > 專案內, 建立[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案, 並`authenticationMode`將屬性設定`SecureConversation`為。 [ \< ](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="9adc9-113">`IssuedTokenForSslNegotiated` `IssuedTokenForCertificate` `authenticationMode` [在安全性>專案中,建立secureConversationBootstrap>元素,並將屬性設定為或。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="9adc9-114">[在\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面, 建立空[ \<的 compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9adc9-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="9adc9-115">[在\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)元素後面, 建立空白[ \<的單向 >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9adc9-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="9adc9-116">在 [ [ \<單向 >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) ] 元素後面, 建立空[ \<的 HTTPTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9adc9-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="9adc9-117">若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9adc9-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="9adc9-118">在配置[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [檔的[系結>]節點中,建立customBinding>元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="9adc9-119">`name` `FederationDuplexTcpMessageSecurityBinding`[在 customBinding > 元素內, 建立系結 > 專案, 並將屬性設定為。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \< ](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="9adc9-120">在系結 > 專案內, 建立[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案, 並`authenticationMode`將屬性設定`SecureConversation`為。 [ \< ](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="9adc9-121">`IssuedTokenForSslNegotiated` `IssuedTokenForCertificate` `authenticationMode` [在安全性>專案中,建立secureConversationBootstrap>元素,並將屬性設定為或。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="9adc9-122">[在\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面, 建立空[ \<的 tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9adc9-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="9adc9-123">若要以 TCP 混合安全性模式建立雙工聯合自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9adc9-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="9adc9-124">在配置[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [檔的[系結>]節點中,建立customBinding>元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="9adc9-125">`name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`[在 customBinding > 元素內, 建立系結 > 專案, 並將屬性設定為。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \< ](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="9adc9-126">在系結 > 專案內, 建立[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)專案, 並`authenticationMode`將屬性設定`SecureConversation`為。 [ \< ](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="9adc9-127">`IssuedTokenForSslNegotiated` `IssuedTokenForCertificate` `authenticationMode` [在安全性>專案中,建立secureConversationBootstrap>元素,並將屬性設定為或。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)</span><span class="sxs-lookup"><span data-stu-id="9adc9-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="9adc9-128">[在\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素後面, 建立空[ \<的 sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9adc9-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="9adc9-129">[在\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)元素後面, 建立空[ \<的 tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9adc9-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9adc9-130">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="9adc9-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="9adc9-131">3 個繫結的範例</span><span class="sxs-lookup"><span data-stu-id="9adc9-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="9adc9-132">將下列程式碼插入組態檔。</span><span class="sxs-lookup"><span data-stu-id="9adc9-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="9adc9-133">範例</span><span class="sxs-lookup"><span data-stu-id="9adc9-133">Example</span></span>

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
