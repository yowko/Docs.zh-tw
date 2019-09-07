---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: fc86a97ebae160f5bf2c8fcb2df9295ed7803963
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399021"
---
# <a name="wshttpbinding"></a><span data-ttu-id="4ad85-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4ad85-101">\<wsHttpBinding></span></span>
<span data-ttu-id="4ad85-102">為非雙工服務合約定義安全、可靠且互通的繫結。</span><span class="sxs-lookup"><span data-stu-id="4ad85-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="4ad85-103">系結會實行下列規格：適用于可靠性的 WS-可靠訊息，以及訊息安全性和驗證的安全性。</span><span class="sxs-lookup"><span data-stu-id="4ad85-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="4ad85-104">傳輸是 HTTP，而訊息編碼是 Text/XML 編碼。</span><span class="sxs-lookup"><span data-stu-id="4ad85-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
<span data-ttu-id="4ad85-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4ad85-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4ad85-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4ad85-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4ad85-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4ad85-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4ad85-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="4ad85-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad85-109">語法</span><span class="sxs-lookup"><span data-stu-id="4ad85-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ad85-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4ad85-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4ad85-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="4ad85-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ad85-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4ad85-112">Attributes</span></span>  
  
|<span data-ttu-id="4ad85-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4ad85-113">Attribute</span></span>|<span data-ttu-id="4ad85-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ad85-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ad85-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="4ad85-115">allowCookies</span></span>|<span data-ttu-id="4ad85-116">布林值，表示用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。</span><span class="sxs-lookup"><span data-stu-id="4ad85-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="4ad85-117">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="4ad85-117">The default is false.</span></span><br /><br /> <span data-ttu-id="4ad85-118">當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="4ad85-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="4ad85-119">如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="4ad85-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="4ad85-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="4ad85-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="4ad85-121">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4ad85-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="4ad85-122">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4ad85-122">The default is `false`.</span></span>|  
|<span data-ttu-id="4ad85-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="4ad85-123">closeTimeout</span></span>|<span data-ttu-id="4ad85-124"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="4ad85-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4ad85-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad85-126">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad85-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4ad85-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4ad85-127">hostnameComparisonMode</span></span>|<span data-ttu-id="4ad85-128">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="4ad85-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4ad85-129">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="4ad85-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4ad85-130">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="4ad85-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="4ad85-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4ad85-131">maxBufferPoolSize</span></span>|<span data-ttu-id="4ad85-132">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="4ad85-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4ad85-133">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="4ad85-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="4ad85-134">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4ad85-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4ad85-135">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="4ad85-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4ad85-136">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="4ad85-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4ad85-137">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="4ad85-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4ad85-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4ad85-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="4ad85-139">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="4ad85-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4ad85-140">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4ad85-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4ad85-141">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="4ad85-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4ad85-142">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="4ad85-142">The default is 65536.</span></span>|  
|<span data-ttu-id="4ad85-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="4ad85-143">messageEncoding</span></span>|<span data-ttu-id="4ad85-144">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="4ad85-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="4ad85-145">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="4ad85-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4ad85-146">文字使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="4ad85-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="4ad85-147">Mtom使用訊息傳輸組織機制1.0 （MTOM）編碼器。</span><span class="sxs-lookup"><span data-stu-id="4ad85-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="4ad85-148">-預設值為 Text。</span><span class="sxs-lookup"><span data-stu-id="4ad85-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="4ad85-149">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="4ad85-150">NAME</span><span class="sxs-lookup"><span data-stu-id="4ad85-150">name</span></span>|<span data-ttu-id="4ad85-151">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="4ad85-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4ad85-152">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="4ad85-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4ad85-153">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="4ad85-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4ad85-154">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="4ad85-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="4ad85-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4ad85-155">openTimeout</span></span>|<span data-ttu-id="4ad85-156"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="4ad85-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4ad85-157">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad85-158">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad85-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4ad85-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="4ad85-159">proxyAddress</span></span>|<span data-ttu-id="4ad85-160">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="4ad85-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="4ad85-161">如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="4ad85-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="4ad85-162">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="4ad85-162">The default is `null`.</span></span>|  
|<span data-ttu-id="4ad85-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4ad85-163">receiveTimeout</span></span>|<span data-ttu-id="4ad85-164"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="4ad85-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4ad85-165">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad85-166">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad85-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4ad85-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="4ad85-167">sendTimeout</span></span>|<span data-ttu-id="4ad85-168"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="4ad85-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4ad85-169">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad85-170">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad85-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4ad85-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="4ad85-171">textEncoding</span></span>|<span data-ttu-id="4ad85-172">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4ad85-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4ad85-173">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="4ad85-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4ad85-174">UnicodeFffeTextEncodingUnicode BigEndian 編碼。</span><span class="sxs-lookup"><span data-stu-id="4ad85-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="4ad85-175">Utf16TextEncoding16位編碼。</span><span class="sxs-lookup"><span data-stu-id="4ad85-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="4ad85-176">Utf8TextEncoding8位編碼。</span><span class="sxs-lookup"><span data-stu-id="4ad85-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="4ad85-177">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="4ad85-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="4ad85-178">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="4ad85-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="4ad85-179">transactionFlow</span></span>|<span data-ttu-id="4ad85-180">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="4ad85-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="4ad85-181">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4ad85-181">The default is `false`.</span></span>|  
|<span data-ttu-id="4ad85-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="4ad85-182">useDefaultWebProxy</span></span>|<span data-ttu-id="4ad85-183">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="4ad85-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="4ad85-184">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4ad85-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ad85-185">子元素</span><span class="sxs-lookup"><span data-stu-id="4ad85-185">Child Elements</span></span>  
  
|<span data-ttu-id="4ad85-186">項目</span><span class="sxs-lookup"><span data-stu-id="4ad85-186">Element</span></span>|<span data-ttu-id="4ad85-187">描述</span><span class="sxs-lookup"><span data-stu-id="4ad85-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad85-188">\<security></span><span class="sxs-lookup"><span data-stu-id="4ad85-188">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="4ad85-189">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="4ad85-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="4ad85-190">此項目的型別為 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="4ad85-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4ad85-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4ad85-192">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="4ad85-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4ad85-193">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="4ad85-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="4ad85-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4ad85-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="4ad85-195">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4ad85-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ad85-196">父項目</span><span class="sxs-lookup"><span data-stu-id="4ad85-196">Parent Elements</span></span>  
  
|<span data-ttu-id="4ad85-197">項目</span><span class="sxs-lookup"><span data-stu-id="4ad85-197">Element</span></span>|<span data-ttu-id="4ad85-198">說明</span><span class="sxs-lookup"><span data-stu-id="4ad85-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad85-199">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4ad85-199">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4ad85-200">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="4ad85-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad85-201">備註</span><span class="sxs-lookup"><span data-stu-id="4ad85-201">Remarks</span></span>  
 <span data-ttu-id="4ad85-202">`WSHttpBinding` 與 `BasicHttpBinding` 類似，不過前者提供更多的 Web 服務功能。</span><span class="sxs-lookup"><span data-stu-id="4ad85-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="4ad85-203">它使用 HTTP 傳輸並提供訊息安全性，如同 BasicHttpBinding，不過它也提供交易、可靠傳訊以及 WS-Addressing，可能預設就啟用，或是透過單一控制設定提供使用。</span><span class="sxs-lookup"><span data-stu-id="4ad85-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ad85-204">範例</span><span class="sxs-lookup"><span data-stu-id="4ad85-204">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="4ad85-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad85-205">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="4ad85-206">繫結</span><span class="sxs-lookup"><span data-stu-id="4ad85-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4ad85-207">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="4ad85-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4ad85-208">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="4ad85-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4ad85-209">\<binding></span><span class="sxs-lookup"><span data-stu-id="4ad85-209">\<binding></span></span>](../../../misc/binding.md)
