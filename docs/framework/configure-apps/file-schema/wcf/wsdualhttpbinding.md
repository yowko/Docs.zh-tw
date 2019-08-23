---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 8fd758258a34fd63882c3d06b49cbe53bd2d105d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915117"
---
# <a name="wsdualhttpbinding"></a><span data-ttu-id="6b059-101">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6b059-101">\<wsDualHttpBinding></span></span>
<span data-ttu-id="6b059-102">定義安全、可靠且互通的繫結，且這個繫結適用於雙工服務合約或透過 SOAP 媒介的通訊。</span><span class="sxs-lookup"><span data-stu-id="6b059-102">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="6b059-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b059-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b059-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6b059-104">\<bindings></span></span>  
<span data-ttu-id="6b059-105">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6b059-105">\<wsDualHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b059-106">語法</span><span class="sxs-lookup"><span data-stu-id="6b059-106">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
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
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b059-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6b059-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6b059-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6b059-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b059-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6b059-109">Attributes</span></span>  
  
|<span data-ttu-id="6b059-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6b059-110">Attribute</span></span>|<span data-ttu-id="6b059-111">說明</span><span class="sxs-lookup"><span data-stu-id="6b059-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b059-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="6b059-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="6b059-113">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6b059-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="6b059-114">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6b059-114">The default is `false`.</span></span>|  
|<span data-ttu-id="6b059-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="6b059-115">clientBaseAddress</span></span>|<span data-ttu-id="6b059-116">URI，設定用戶端在上面接聽以接收來自服務之回應訊息的基底位址。</span><span class="sxs-lookup"><span data-stu-id="6b059-116">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="6b059-117">如果指定，便會使用這個位址 (再加上每個通道的 GUID) 來接聽。</span><span class="sxs-lookup"><span data-stu-id="6b059-117">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="6b059-118">如果未指定值，則會以傳輸特定的方式來產生用戶端基底位址。</span><span class="sxs-lookup"><span data-stu-id="6b059-118">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="6b059-119">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="6b059-119">The default is `null`.</span></span>|  
|<span data-ttu-id="6b059-120">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="6b059-120">closeTimeout</span></span>|<span data-ttu-id="6b059-121"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6b059-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6b059-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6b059-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b059-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6b059-123">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b059-124">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="6b059-124">hostnameComparisonMode</span></span>|<span data-ttu-id="6b059-125">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="6b059-125">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="6b059-126">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="6b059-126">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6b059-127">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="6b059-127">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="6b059-128">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6b059-128">maxBufferPoolSize</span></span>|<span data-ttu-id="6b059-129">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="6b059-129">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="6b059-130">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="6b059-130">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="6b059-131">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6b059-131">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="6b059-132">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="6b059-132">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6b059-133">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="6b059-133">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6b059-134">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="6b059-134">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6b059-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6b059-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="6b059-136">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="6b059-136">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6b059-137">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b059-137">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="6b059-138">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="6b059-138">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6b059-139">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="6b059-139">The default is 65536.</span></span>|  
|<span data-ttu-id="6b059-140">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="6b059-140">messageEncoding</span></span>|<span data-ttu-id="6b059-141">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="6b059-141">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="6b059-142">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="6b059-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6b059-143">文字使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="6b059-143">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="6b059-144">Mtom使用訊息傳輸組織機制 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="6b059-144">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="6b059-145">-預設值為 Text。</span><span class="sxs-lookup"><span data-stu-id="6b059-145">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="6b059-146">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="6b059-146">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="6b059-147">NAME</span><span class="sxs-lookup"><span data-stu-id="6b059-147">name</span></span>|<span data-ttu-id="6b059-148">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="6b059-148">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6b059-149">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="6b059-149">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6b059-150">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="6b059-150">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6b059-151">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="6b059-151">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="6b059-152">openTimeout</span><span class="sxs-lookup"><span data-stu-id="6b059-152">openTimeout</span></span>|<span data-ttu-id="6b059-153"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6b059-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6b059-154">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6b059-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b059-155">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6b059-155">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b059-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="6b059-156">proxyAddress</span></span>|<span data-ttu-id="6b059-157">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="6b059-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="6b059-158">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="6b059-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="6b059-159">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="6b059-159">The default is `null`.</span></span>|  
|<span data-ttu-id="6b059-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6b059-160">receiveTimeout</span></span>|<span data-ttu-id="6b059-161"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6b059-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6b059-162">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6b059-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b059-163">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6b059-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b059-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="6b059-164">sendTimeout</span></span>|<span data-ttu-id="6b059-165"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6b059-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6b059-166">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6b059-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b059-167">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6b059-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b059-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="6b059-168">textEncoding</span></span>|<span data-ttu-id="6b059-169">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6b059-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6b059-170">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="6b059-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6b059-171">BigEndianUnicodeUnicode BigEndian 編碼。</span><span class="sxs-lookup"><span data-stu-id="6b059-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="6b059-172">消除16位編碼。</span><span class="sxs-lookup"><span data-stu-id="6b059-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="6b059-173">UTF88位編碼</span><span class="sxs-lookup"><span data-stu-id="6b059-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6b059-174">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="6b059-174">The default is UTF8.</span></span> <span data-ttu-id="6b059-175">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="6b059-175">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="6b059-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="6b059-176">transactionFlow</span></span>|<span data-ttu-id="6b059-177">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="6b059-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="6b059-178">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6b059-178">The default is `false`.</span></span>|  
|<span data-ttu-id="6b059-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="6b059-179">useDefaultWebProxy</span></span>|<span data-ttu-id="6b059-180">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="6b059-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="6b059-181">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="6b059-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="6b059-182">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6b059-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b059-183">子元素</span><span class="sxs-lookup"><span data-stu-id="6b059-183">Child Elements</span></span>  
  
|<span data-ttu-id="6b059-184">項目</span><span class="sxs-lookup"><span data-stu-id="6b059-184">Element</span></span>|<span data-ttu-id="6b059-185">說明</span><span class="sxs-lookup"><span data-stu-id="6b059-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b059-186">\<security></span><span class="sxs-lookup"><span data-stu-id="6b059-186">\<security></span></span>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="6b059-187">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6b059-187">Defines the security settings for the binding.</span></span> <span data-ttu-id="6b059-188">此項目的型別為 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="6b059-188">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="6b059-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b059-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6b059-190">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="6b059-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6b059-191">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="6b059-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="6b059-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6b059-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="6b059-193">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6b059-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b059-194">父項目</span><span class="sxs-lookup"><span data-stu-id="6b059-194">Parent Elements</span></span>  
  
|<span data-ttu-id="6b059-195">項目</span><span class="sxs-lookup"><span data-stu-id="6b059-195">Element</span></span>|<span data-ttu-id="6b059-196">描述</span><span class="sxs-lookup"><span data-stu-id="6b059-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b059-197">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6b059-197">\<bindings></span></span>](bindings.md)|<span data-ttu-id="6b059-198">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="6b059-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b059-199">備註</span><span class="sxs-lookup"><span data-stu-id="6b059-199">Remarks</span></span>  
 <span data-ttu-id="6b059-200">`WSDualHttpBinding` 提供與 `WSHttpBinding` 相同的 Web 服務通訊協定支援，但是要搭配雙工合約使用。</span><span class="sxs-lookup"><span data-stu-id="6b059-200">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="6b059-201">`WSDualHttpBinding` 只支援 SOAP 安全性，而且需要可靠傳訊。</span><span class="sxs-lookup"><span data-stu-id="6b059-201">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="6b059-202">這個繫結要求用戶端擁有針對服務提供回呼端點的公用 URI，</span><span class="sxs-lookup"><span data-stu-id="6b059-202">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="6b059-203">這是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="6b059-203">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="6b059-204">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="6b059-204">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="6b059-205">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="6b059-205">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="6b059-206">這個繫結可透過一個或多個 SOAP 媒介可靠地進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6b059-206">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="6b059-207">根據預設，這個繫結在產生執行階段堆疊時會搭配 WS-ReliableMessaging (可靠性)、WS-Security (訊息安全性和驗證)、HTTP (訊息傳遞) 以及 Text/XML (訊息編碼)。</span><span class="sxs-lookup"><span data-stu-id="6b059-207">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b059-208">範例</span><span class="sxs-lookup"><span data-stu-id="6b059-208">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a><span data-ttu-id="6b059-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b059-209">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="6b059-210">繫結</span><span class="sxs-lookup"><span data-stu-id="6b059-210">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6b059-211">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6b059-211">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6b059-212">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6b059-212">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6b059-213">\<binding></span><span class="sxs-lookup"><span data-stu-id="6b059-213">\<binding></span></span>](../../../misc/binding.md)
