---
title: '&lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 1c03dd0a38264b75b31c9638cf5985a4375aea67
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846015"
---
# <a name="ltwsdualhttpbindinggt"></a><span data-ttu-id="7ed8b-102">&lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7ed8b-102">&lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="7ed8b-103">定義安全、可靠且互通的繫結，且這個繫結適用於雙工服務合約或透過 SOAP 媒介的通訊。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-103">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="7ed8b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7ed8b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ed8b-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7ed8b-105">\<bindings></span></span>  
<span data-ttu-id="7ed8b-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7ed8b-106">\<wsDualHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed8b-107">語法</span><span class="sxs-lookup"><span data-stu-id="7ed8b-107">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ed8b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ed8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7ed8b-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="7ed8b-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ed8b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7ed8b-110">Attributes</span></span>  
  
|<span data-ttu-id="7ed8b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7ed8b-111">Attribute</span></span>|<span data-ttu-id="7ed8b-112">描述</span><span class="sxs-lookup"><span data-stu-id="7ed8b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ed8b-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="7ed8b-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="7ed8b-114">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="7ed8b-115">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-115">The default is `false`.</span></span>|  
|<span data-ttu-id="7ed8b-116">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="7ed8b-116">clientBaseAddress</span></span>|<span data-ttu-id="7ed8b-117">URI，設定用戶端在上面接聽以接收來自服務之回應訊息的基底位址。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-117">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="7ed8b-118">如果指定，便會使用這個位址 (再加上每個通道的 GUID) 來接聽。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-118">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="7ed8b-119">如果未指定值，則會以傳輸特定的方式來產生用戶端基底位址。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-119">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="7ed8b-120">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-120">The default is `null`.</span></span>|  
|<span data-ttu-id="7ed8b-121">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="7ed8b-121">closeTimeout</span></span>|<span data-ttu-id="7ed8b-122"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7ed8b-123">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ed8b-124">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-124">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7ed8b-125">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="7ed8b-125">hostnameComparisonMode</span></span>|<span data-ttu-id="7ed8b-126">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-126">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="7ed8b-127">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-127">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7ed8b-128">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-128">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="7ed8b-129">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7ed8b-129">maxBufferPoolSize</span></span>|<span data-ttu-id="7ed8b-130">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-130">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7ed8b-131">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-131">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="7ed8b-132">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-132">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7ed8b-133">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-133">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7ed8b-134">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="7ed8b-134">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7ed8b-135">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-135">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="7ed8b-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7ed8b-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="7ed8b-137">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7ed8b-138">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="7ed8b-139">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7ed8b-140">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-140">The default is 65536.</span></span>|  
|<span data-ttu-id="7ed8b-141">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="7ed8b-141">messageEncoding</span></span>|<span data-ttu-id="7ed8b-142">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-142">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="7ed8b-143">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="7ed8b-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7ed8b-144">文字： 使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-144">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="7ed8b-145">Mtom： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-145">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="7ed8b-146">-預設值為文字。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-146">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="7ed8b-147">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-147">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="7ed8b-148">name</span><span class="sxs-lookup"><span data-stu-id="7ed8b-148">name</span></span>|<span data-ttu-id="7ed8b-149">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7ed8b-150">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7ed8b-151">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-151">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7ed8b-152">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="7ed8b-153">openTimeout</span><span class="sxs-lookup"><span data-stu-id="7ed8b-153">openTimeout</span></span>|<span data-ttu-id="7ed8b-154"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7ed8b-155">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ed8b-156">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-156">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7ed8b-157">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="7ed8b-157">proxyAddress</span></span>|<span data-ttu-id="7ed8b-158">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-158">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="7ed8b-159">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-159">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="7ed8b-160">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-160">The default is `null`.</span></span>|  
|<span data-ttu-id="7ed8b-161">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7ed8b-161">receiveTimeout</span></span>|<span data-ttu-id="7ed8b-162"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7ed8b-163">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ed8b-164">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7ed8b-165">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="7ed8b-165">sendTimeout</span></span>|<span data-ttu-id="7ed8b-166"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7ed8b-167">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ed8b-168">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-168">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7ed8b-169">textEncoding</span><span class="sxs-lookup"><span data-stu-id="7ed8b-169">textEncoding</span></span>|<span data-ttu-id="7ed8b-170">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7ed8b-171">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="7ed8b-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7ed8b-172">-BigEndianUnicode: Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7ed8b-173">Unicode: 16 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7ed8b-174">-UTF8: 8 位元編碼方式</span><span class="sxs-lookup"><span data-stu-id="7ed8b-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7ed8b-175">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-175">The default is UTF8.</span></span> <span data-ttu-id="7ed8b-176">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="7ed8b-177">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="7ed8b-177">transactionFlow</span></span>|<span data-ttu-id="7ed8b-178">指定繫結是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-178">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="7ed8b-179">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-179">The default is `false`.</span></span>|  
|<span data-ttu-id="7ed8b-180">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="7ed8b-180">useDefaultWebProxy</span></span>|<span data-ttu-id="7ed8b-181">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-181">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="7ed8b-182">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-182">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="7ed8b-183">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ed8b-184">子元素</span><span class="sxs-lookup"><span data-stu-id="7ed8b-184">Child Elements</span></span>  
  
|<span data-ttu-id="7ed8b-185">項目</span><span class="sxs-lookup"><span data-stu-id="7ed8b-185">Element</span></span>|<span data-ttu-id="7ed8b-186">描述</span><span class="sxs-lookup"><span data-stu-id="7ed8b-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ed8b-187">\<security></span><span class="sxs-lookup"><span data-stu-id="7ed8b-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="7ed8b-188">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="7ed8b-189">此項目的型別為 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-189">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="7ed8b-190">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="7ed8b-190">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7ed8b-191">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7ed8b-192">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="7ed8b-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="7ed8b-193">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="7ed8b-194">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ed8b-195">父項目</span><span class="sxs-lookup"><span data-stu-id="7ed8b-195">Parent Elements</span></span>  
  
|<span data-ttu-id="7ed8b-196">項目</span><span class="sxs-lookup"><span data-stu-id="7ed8b-196">Element</span></span>|<span data-ttu-id="7ed8b-197">描述</span><span class="sxs-lookup"><span data-stu-id="7ed8b-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ed8b-198">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7ed8b-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7ed8b-199">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ed8b-200">備註</span><span class="sxs-lookup"><span data-stu-id="7ed8b-200">Remarks</span></span>  
 <span data-ttu-id="7ed8b-201">`WSDualHttpBinding` 提供與 `WSHttpBinding` 相同的 Web 服務通訊協定支援，但是要搭配雙工合約使用。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-201">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="7ed8b-202">`WSDualHttpBinding` 只支援 SOAP 安全性，而且需要可靠傳訊。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-202">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="7ed8b-203">這個繫結要求用戶端擁有針對服務提供回呼端點的公用 URI，</span><span class="sxs-lookup"><span data-stu-id="7ed8b-203">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="7ed8b-204">這是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-204">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="7ed8b-205">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="7ed8b-205">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="7ed8b-206">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-206">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="7ed8b-207">這個繫結可透過一個或多個 SOAP 媒介可靠地進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-207">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="7ed8b-208">根據預設，這個繫結在產生執行階段堆疊時會搭配 WS-ReliableMessaging (可靠性)、WS-Security (訊息安全性和驗證)、HTTP (訊息傳遞) 以及 Text/XML (訊息編碼)。</span><span class="sxs-lookup"><span data-stu-id="7ed8b-208">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ed8b-209">範例</span><span class="sxs-lookup"><span data-stu-id="7ed8b-209">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ed8b-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed8b-210">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [<span data-ttu-id="7ed8b-211">繫結</span><span class="sxs-lookup"><span data-stu-id="7ed8b-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7ed8b-212">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7ed8b-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7ed8b-213">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="7ed8b-213">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="7ed8b-214">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7ed8b-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
