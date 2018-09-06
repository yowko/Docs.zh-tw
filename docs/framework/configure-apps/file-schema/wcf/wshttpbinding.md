---
title: '&lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 480e10b9667712fbd2a3ffa95e1373d72ee1a9df
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875998"
---
# <a name="ltwshttpbindinggt"></a><span data-ttu-id="26552-102">&lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="26552-102">&lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="26552-103">為非雙工服務合約定義安全、可靠且互通的繫結。</span><span class="sxs-lookup"><span data-stu-id="26552-103">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="26552-104">此繫結會實作下列規格：WS-Reliable 訊息用於可靠性以及 WS-Security 用於訊息安全性和驗證。</span><span class="sxs-lookup"><span data-stu-id="26552-104">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="26552-105">傳輸是 HTTP，而訊息編碼是 Text/XML 編碼。</span><span class="sxs-lookup"><span data-stu-id="26552-105">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="26552-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="26552-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="26552-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="26552-107">\<bindings></span></span>  
<span data-ttu-id="26552-108">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="26552-108">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26552-109">語法</span><span class="sxs-lookup"><span data-stu-id="26552-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding   
        allowCookies="Boolean"  
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
          <message   
             algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                          clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
             establishSecurityContext="Boolean"  
             negotiateServiceCredential="Boolean" />  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26552-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="26552-110">Attributes and Elements</span></span>  
 <span data-ttu-id="26552-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="26552-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26552-112">屬性</span><span class="sxs-lookup"><span data-stu-id="26552-112">Attributes</span></span>  
  
|<span data-ttu-id="26552-113">屬性</span><span class="sxs-lookup"><span data-stu-id="26552-113">Attribute</span></span>|<span data-ttu-id="26552-114">描述</span><span class="sxs-lookup"><span data-stu-id="26552-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26552-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="26552-115">allowCookies</span></span>|<span data-ttu-id="26552-116">布林值，表示用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。</span><span class="sxs-lookup"><span data-stu-id="26552-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="26552-117">預設為 false。</span><span class="sxs-lookup"><span data-stu-id="26552-117">The default is false.</span></span><br /><br /> <span data-ttu-id="26552-118">當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="26552-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="26552-119">如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="26552-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="26552-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="26552-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="26552-121">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="26552-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="26552-122">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26552-122">The default is `false`.</span></span>|  
|<span data-ttu-id="26552-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="26552-123">closeTimeout</span></span>|<span data-ttu-id="26552-124"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26552-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="26552-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="26552-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="26552-126">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="26552-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="26552-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="26552-127">hostnameComparisonMode</span></span>|<span data-ttu-id="26552-128">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="26552-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="26552-129">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="26552-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="26552-130">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="26552-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="26552-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="26552-131">maxBufferPoolSize</span></span>|<span data-ttu-id="26552-132">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="26552-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="26552-133">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="26552-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="26552-134">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="26552-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="26552-135">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="26552-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="26552-136">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="26552-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="26552-137">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="26552-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="26552-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="26552-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="26552-139">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="26552-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="26552-140">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="26552-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="26552-141">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="26552-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="26552-142">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="26552-142">The default is 65536.</span></span>|  
|<span data-ttu-id="26552-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="26552-143">messageEncoding</span></span>|<span data-ttu-id="26552-144">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="26552-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="26552-145">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="26552-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="26552-146">文字： 使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="26552-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="26552-147">Mtom： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="26552-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="26552-148">-預設值為文字。</span><span class="sxs-lookup"><span data-stu-id="26552-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="26552-149">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="26552-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="26552-150">name</span><span class="sxs-lookup"><span data-stu-id="26552-150">name</span></span>|<span data-ttu-id="26552-151">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="26552-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="26552-152">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="26552-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="26552-153">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="26552-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="26552-154">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="26552-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="26552-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="26552-155">openTimeout</span></span>|<span data-ttu-id="26552-156"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26552-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="26552-157">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="26552-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="26552-158">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="26552-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="26552-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="26552-159">proxyAddress</span></span>|<span data-ttu-id="26552-160">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="26552-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="26552-161">如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="26552-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="26552-162">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="26552-162">The default is `null`.</span></span>|  
|<span data-ttu-id="26552-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="26552-163">receiveTimeout</span></span>|<span data-ttu-id="26552-164"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26552-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="26552-165">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="26552-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="26552-166">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="26552-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="26552-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="26552-167">sendTimeout</span></span>|<span data-ttu-id="26552-168"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26552-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="26552-169">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="26552-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="26552-170">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="26552-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="26552-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="26552-171">textEncoding</span></span>|<span data-ttu-id="26552-172">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="26552-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="26552-173">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="26552-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="26552-174">-UnicodeFffeTextEncoding: Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="26552-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="26552-175">-Utf16textencoding:unicode 16 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="26552-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="26552-176">-Utf8TextEncoding: 8 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="26552-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="26552-177">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="26552-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="26552-178">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="26552-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="26552-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="26552-179">transactionFlow</span></span>|<span data-ttu-id="26552-180">指定繫結是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="26552-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="26552-181">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26552-181">The default is `false`.</span></span>|  
|<span data-ttu-id="26552-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="26552-182">useDefaultWebProxy</span></span>|<span data-ttu-id="26552-183">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="26552-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="26552-184">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="26552-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26552-185">子元素</span><span class="sxs-lookup"><span data-stu-id="26552-185">Child Elements</span></span>  
  
|<span data-ttu-id="26552-186">項目</span><span class="sxs-lookup"><span data-stu-id="26552-186">Element</span></span>|<span data-ttu-id="26552-187">描述</span><span class="sxs-lookup"><span data-stu-id="26552-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26552-188">\<security></span><span class="sxs-lookup"><span data-stu-id="26552-188">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="26552-189">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="26552-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="26552-190">此項目的型別為 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="26552-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="26552-191">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="26552-191">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="26552-192">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="26552-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="26552-193">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="26552-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="26552-194">reliableSession</span><span class="sxs-lookup"><span data-stu-id="26552-194">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="26552-195">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="26552-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26552-196">父項目</span><span class="sxs-lookup"><span data-stu-id="26552-196">Parent Elements</span></span>  
  
|<span data-ttu-id="26552-197">項目</span><span class="sxs-lookup"><span data-stu-id="26552-197">Element</span></span>|<span data-ttu-id="26552-198">描述</span><span class="sxs-lookup"><span data-stu-id="26552-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26552-199">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="26552-199">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="26552-200">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="26552-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26552-201">備註</span><span class="sxs-lookup"><span data-stu-id="26552-201">Remarks</span></span>  
 <span data-ttu-id="26552-202">`WSHttpBinding` 與 `BasicHttpBinding` 類似，不過前者提供更多的 Web 服務功能。</span><span class="sxs-lookup"><span data-stu-id="26552-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="26552-203">它使用 HTTP 傳輸並提供訊息安全性，如同 BasicHttpBinding，不過它也提供異動、可靠傳訊以及 WS-Addressing，可能預設就啟用，或是透過單一控制設定提供使用。</span><span class="sxs-lookup"><span data-stu-id="26552-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26552-204">範例</span><span class="sxs-lookup"><span data-stu-id="26552-204">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
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
  
## <a name="see-also"></a><span data-ttu-id="26552-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26552-205">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement>  
 [<span data-ttu-id="26552-206">繫結</span><span class="sxs-lookup"><span data-stu-id="26552-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="26552-207">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="26552-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="26552-208">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="26552-208">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="26552-209">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="26552-209">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
