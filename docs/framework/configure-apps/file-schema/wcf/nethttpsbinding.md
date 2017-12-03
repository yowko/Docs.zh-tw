---
title: '&lt;netHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e339066311adf10791c1b6759cc7be6b419320b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="22f49-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="22f49-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="22f49-103">表示 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務可用於設定和公開能夠透過 HTTPS 通訊之端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="22f49-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="22f49-104">與雙工合約搭配使用時，將會使用 Web 通訊端，否則使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="22f49-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="22f49-105">根項目</span><span class="sxs-lookup"><span data-stu-id="22f49-105">Root Element</span></span>  
<span data-ttu-id="22f49-106">下一個項目</span><span class="sxs-lookup"><span data-stu-id="22f49-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f49-107">語法</span><span class="sxs-lookup"><span data-stu-id="22f49-107">Syntax</span></span>  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan"   
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
           maxBufferPoolSize="Integer"  
           maxBufferSize="Integer"  
           maxReceivedMessageSize="Integer"  
           messageEncoding="Binary/Text/Mtom"  
           name="string"   
           openTimeout="TimeSpan"   
           proxyAddress="URI"  
           receiveTimeout="TimeSpan"  
           sendTimeout="TimeSpan"  
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="22f49-108">類型</span><span class="sxs-lookup"><span data-stu-id="22f49-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22f49-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22f49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="22f49-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="22f49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22f49-111">屬性</span><span class="sxs-lookup"><span data-stu-id="22f49-111">Attributes</span></span>  
  
|<span data-ttu-id="22f49-112">屬性</span><span class="sxs-lookup"><span data-stu-id="22f49-112">Attribute</span></span>|<span data-ttu-id="22f49-113">描述</span><span class="sxs-lookup"><span data-stu-id="22f49-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="22f49-114">布林值，表示用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。</span><span class="sxs-lookup"><span data-stu-id="22f49-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="22f49-115">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="22f49-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="22f49-116">當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="22f49-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="22f49-117">如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="22f49-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="22f49-118">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="22f49-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="22f49-119">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="22f49-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="22f49-120">如果網際網路資源有本機位址，則此資源為本機資源。</span><span class="sxs-lookup"><span data-stu-id="22f49-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="22f49-121">本機位址是指位於相同電腦、區域 LAN 或內部網路上的位址，在語法上沒有句號 (.)，例如，"http://webserver/" 和 "http://localhost/" 這兩個 URI 即是本機位址。</span><span class="sxs-lookup"><span data-stu-id="22f49-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="22f49-122">設定這個屬性可決定以 BasicHttpBinding 設定的端點在存取本機資源時，是否使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="22f49-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="22f49-123">如果這個屬性為 `true`，則所有對本機網際網路資源的要求都不會使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="22f49-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="22f49-124">當這個屬性設定為 `true` 時，如果想要讓用戶端在與相同電腦上的服務進行交談時通過 Proxy，請使用主機名稱 (而非 localhost)。</span><span class="sxs-lookup"><span data-stu-id="22f49-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="22f49-125">當這個屬性設定為 `false` 時，則所有的網際網路要求都會通過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="22f49-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="22f49-126"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="22f49-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="22f49-127">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="22f49-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22f49-128">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="22f49-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="22f49-129">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="22f49-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="22f49-130">這個屬性的型別為 `HostnameComparisonMode`，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="22f49-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="22f49-131">預設值為 `StrongWildcard`，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="22f49-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="22f49-132">整數值，指定配置供從通道接收訊息之訊息緩衝區管理員使用的最大記憶體量。</span><span class="sxs-lookup"><span data-stu-id="22f49-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="22f49-133">預設值為 524288 (0x80000) 位元組。</span><span class="sxs-lookup"><span data-stu-id="22f49-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="22f49-134">緩衝區管理員會利用緩衝區集區，將使用緩衝區的成本降至最低。</span><span class="sxs-lookup"><span data-stu-id="22f49-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="22f49-135">當訊息從通道送出時，服務將需要緩衝區來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="22f49-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="22f49-136">如果緩衝區集區中沒有足夠的記憶體可以處理訊息負載，緩衝區管理員就必須從 CLR 堆積配置額外的記憶體，進而增加記憶體回收負荷。</span><span class="sxs-lookup"><span data-stu-id="22f49-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="22f49-137">從 CLR 記憶體回收堆積所產生的大量配置表示緩衝區集區太小，而提高這個屬性指定的限制來提供較大的配置，便可改善效能。</span><span class="sxs-lookup"><span data-stu-id="22f49-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="22f49-138">整數值，指定儲存訊息之緩衝區的大小上限 (以位元組為單位)。在為此繫結設定的端點處理訊息時，可以將訊息儲存在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="22f49-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="22f49-139">預設值為 65,536 位元組。</span><span class="sxs-lookup"><span data-stu-id="22f49-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="22f49-140">正整數，定義在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="22f49-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="22f49-141">如果對收件者而言訊息太大，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="22f49-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="22f49-142">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="22f49-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="22f49-143">預設為 65,536 個位元組。</span><span class="sxs-lookup"><span data-stu-id="22f49-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="22f49-144">定義用來對 SOAP 訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="22f49-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="22f49-145">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="22f49-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22f49-146">檢索： 使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="22f49-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="22f49-147">Mtom： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="22f49-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="22f49-148">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="22f49-148">The default is Text.</span></span> <span data-ttu-id="22f49-149">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="22f49-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="22f49-150">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="22f49-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="22f49-151">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="22f49-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="22f49-152">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="22f49-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="22f49-153">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="22f49-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="22f49-154">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="22f49-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="22f49-155">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="22f49-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="22f49-156">指定繫結的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="22f49-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="22f49-157">預設值為 "http://tempuri.org/Bindings"。</span><span class="sxs-lookup"><span data-stu-id="22f49-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="22f49-158">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="22f49-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="22f49-159"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="22f49-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="22f49-160">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="22f49-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22f49-161">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="22f49-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="22f49-162">包含 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="22f49-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="22f49-163">如果 `useSystemWebProxy` 設定為 `true`，則這個設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="22f49-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="22f49-164">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="22f49-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="22f49-165"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="22f49-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="22f49-166">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="22f49-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22f49-167">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="22f49-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="22f49-168"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="22f49-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="22f49-169">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="22f49-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22f49-170">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="22f49-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="22f49-171">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="22f49-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="22f49-172">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="22f49-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22f49-173">-BigEndianUnicode: Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="22f49-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="22f49-174">Unicode: 16 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="22f49-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="22f49-175">UTF8: 8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="22f49-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="22f49-176">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="22f49-176">The default is UTF8.</span></span> <span data-ttu-id="22f49-177">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="22f49-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="22f49-178">有效的 <xref:System.ServiceModel.TransferMode> 值，指定進行要求或回應時，訊息是經過緩衝處理或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="22f49-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="22f49-179">布林值，指定是否應使用系統自動設定的 HTTP Proxy (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="22f49-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="22f49-180">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="22f49-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="22f49-181">子元素</span><span class="sxs-lookup"><span data-stu-id="22f49-181">Child Elements</span></span>  
  
|<span data-ttu-id="22f49-182">項目</span><span class="sxs-lookup"><span data-stu-id="22f49-182">Element</span></span>|<span data-ttu-id="22f49-183">說明</span><span class="sxs-lookup"><span data-stu-id="22f49-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f49-184">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="22f49-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="22f49-185">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="22f49-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="22f49-186">此項目的型別為 <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="22f49-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="22f49-187">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="22f49-187">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="22f49-188">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="22f49-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="22f49-189">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="22f49-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22f49-190">父項目</span><span class="sxs-lookup"><span data-stu-id="22f49-190">Parent Elements</span></span>  
  
|<span data-ttu-id="22f49-191">項目</span><span class="sxs-lookup"><span data-stu-id="22f49-191">Element</span></span>|<span data-ttu-id="22f49-192">說明</span><span class="sxs-lookup"><span data-stu-id="22f49-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f49-193">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="22f49-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="22f49-194">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="22f49-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f49-195">備註</span><span class="sxs-lookup"><span data-stu-id="22f49-195">Remarks</span></span>  
 <span data-ttu-id="22f49-196">NetHttpsBinding 使用 HTTPS 做為傳送訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="22f49-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="22f49-197">與雙工合約搭配使用時，將會使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="22f49-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="22f49-198">與要求-回覆合約搭配使用時，NetHttpsBinding 的行為就像具有二進位編碼器的 BasicHttpsBinding。</span><span class="sxs-lookup"><span data-stu-id="22f49-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="22f49-199">安全性已關閉，根據預設，但是可以設定的模式屬性加入[\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)以外的值的子項目`None`。</span><span class="sxs-lookup"><span data-stu-id="22f49-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="22f49-200">根據預設，它使用「文字」訊息編碼和 UTF-8 文字編碼。</span><span class="sxs-lookup"><span data-stu-id="22f49-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f49-201">範例</span><span class="sxs-lookup"><span data-stu-id="22f49-201">Example</span></span>  
 <span data-ttu-id="22f49-202">下列範例示範 <xref:System.ServiceModel.NetHttpBinding> 的使用方式，它利用第一代和第二代 Web 服務來提供 HTTPS 通訊和最大的互通性。</span><span class="sxs-lookup"><span data-stu-id="22f49-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="22f49-203">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="22f49-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="22f49-204">繫結型別是使用 `binding` 項目的 `<endpoint>` 屬性所指定的。</span><span class="sxs-lookup"><span data-stu-id="22f49-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="22f49-205">如果您要設定基本繫結，並變更其部分設定，則必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="22f49-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="22f49-206">端點必須使用 `bindingConfiguration` 項目的 `<endpoint>` 屬性來按照名稱參考繫結組態，如下列服務的組態程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="22f49-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard" 
               receiveTimeout="00:10:00" 
               sendTimeout="00:10:00" 
               openTimeout="00:10:00" 
               closeTimeout="00:10:00" 
               maxReceivedMessageSize="65536" 
               maxBufferSize="65536" 
               maxBufferPoolSize="524288" 
               transferMode="Buffered" 
               messageEncoding="Binary" 
               textEncoding="utf-8" 
               bypassProxyOnLocal="false" 
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="22f49-207">範例</span><span class="sxs-lookup"><span data-stu-id="22f49-207">Example</span></span>  
 <span data-ttu-id="22f49-208">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="22f49-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="22f49-209">前一個範例的功能可以藉由從端點位址移除 bindingConfiguration 以及從繫結移除名稱的方式達成。</span><span class="sxs-lookup"><span data-stu-id="22f49-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="22f49-210">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="22f49-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f49-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22f49-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="22f49-212">繫結</span><span class="sxs-lookup"><span data-stu-id="22f49-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="22f49-213">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="22f49-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="22f49-214">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="22f49-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="22f49-215">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="22f49-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
