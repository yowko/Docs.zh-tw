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
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="3dbd4-102">HOW TO：建立雙工聯合繫結</span><span class="sxs-lookup"><span data-stu-id="3dbd4-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="3dbd4-103"><xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求/回覆訊息交換合約。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="3dbd4-104">若要使用雙工訊息交換合約，必須建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="3dbd4-105">下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="3dbd4-106">這三種繫結方式的完整程式碼範例會列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="3dbd4-107">您也可以撰寫程式碼建立繫結。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-107">You can also create the binding in code.</span></span> <span data-ttu-id="3dbd4-108">如需要建立之繫結項目堆疊的說明，請參閱[如何：使用 SecurityBindingElement 建立自訂](how-to-create-a-custom-binding-using-the-securitybindingelement.md)系結。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="3dbd4-109">若要以 HTTP 建立雙工聯合自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3dbd4-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="3dbd4-110">在 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的節點中，建立 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-110">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="3dbd4-111">在 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素內，建立專案， [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 並將 `name` 屬性設定為 `FederationDuplexHttpMessageSecurityBinding` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-111">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="3dbd4-112">在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素內，建立專案， [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 並將 `authenticationMode` 屬性設定為 `SecureConversation` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="3dbd4-113">在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素內，建立專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-113">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="3dbd4-114">在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素後面，建立空的專案 [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-114">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="3dbd4-115">在 [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 元素後面，建立空的專案 [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-115">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="3dbd4-116">在 [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) 元素後面，建立空的專案 [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-116">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="3dbd4-117">若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3dbd4-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="3dbd4-118">在 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的節點中，建立 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-118">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="3dbd4-119">在 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素內，建立專案， [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 並將 `name` 屬性設定為 `FederationDuplexTcpMessageSecurityBinding` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-119">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="3dbd4-120">在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素內，建立專案， [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 並將 `authenticationMode` 屬性設定為 `SecureConversation` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="3dbd4-121">在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素內，建立專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-121">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="3dbd4-122">在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素後面，建立空的專案 [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-122">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="3dbd4-123">若要以 TCP 混合安全性模式建立雙工聯合自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3dbd4-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="3dbd4-124">在 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的節點中，建立 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-124">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="3dbd4-125">在 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 元素內，建立專案， [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 並將 `name` 屬性設定為 `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-125">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="3dbd4-126">在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素內，建立專案， [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 並將 `authenticationMode` 屬性設定為 `SecureConversation` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="3dbd4-127">在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素內，建立專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate` 或 `IssuedTokenForSslNegotiated` 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-127">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="3dbd4-128">在 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 元素後面，建立空的專案 [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-128">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="3dbd4-129">在 [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) 元素後面，建立空的專案 [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-129">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3dbd4-130">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="3dbd4-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="3dbd4-131">3 個繫結的範例</span><span class="sxs-lookup"><span data-stu-id="3dbd4-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="3dbd4-132">將下列程式碼插入組態檔。</span><span class="sxs-lookup"><span data-stu-id="3dbd4-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="3dbd4-133">範例</span><span class="sxs-lookup"><span data-stu-id="3dbd4-133">Example</span></span>

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
