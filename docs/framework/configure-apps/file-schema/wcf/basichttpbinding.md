---
title: <basicHttpBinding>
description: 定義 WCF 服務可用來設定和公開端點的系結，以與符合 WS-I 基本設定檔1.1 的服務進行通訊。
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 5b2ce1973966468107d7aa4de545a976c67b13ed
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244019"
---
# \<basicHttpBinding>
<span data-ttu-id="1b83a-102">代表繫結，Windows Communication Foundation (WCF) 服務可使用該繫結設定並公開能與 ASMX Web 服務和用戶端，以及其他符合 WS-I Basic Profile 1.1 的服務進行通訊的端點。</span><span class="sxs-lookup"><span data-stu-id="1b83a-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1b83a-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b83a-103">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
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
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b83a-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b83a-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1b83a-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1b83a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b83a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1b83a-106">Attributes</span></span>  
  
|<span data-ttu-id="1b83a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1b83a-107">Attribute</span></span>|<span data-ttu-id="1b83a-108">描述</span><span class="sxs-lookup"><span data-stu-id="1b83a-108">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="1b83a-109">布林值，表示用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。</span><span class="sxs-lookup"><span data-stu-id="1b83a-109">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="1b83a-110">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1b83a-110">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1b83a-111">當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="1b83a-111">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="1b83a-112">如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="1b83a-112">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="1b83a-113">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="1b83a-114">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1b83a-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1b83a-115">如果網際網路資源有本機位址，則此資源為本機資源。</span><span class="sxs-lookup"><span data-stu-id="1b83a-115">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="1b83a-116">本機位址是指位於相同電腦上的本機 LAN 或內部網路，在語法上則是在 Uri 和中缺少句點（.） `http://webserver/` `http://localhost/` 。</span><span class="sxs-lookup"><span data-stu-id="1b83a-116">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="1b83a-117">設定這個屬性可決定以 BasicHttpBinding 設定的端點在存取本機資源時，是否使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-117">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="1b83a-118">如果這個屬性為 `true`，則所有對本機網際網路資源的要求都不會使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-118">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="1b83a-119">當這個屬性設定為 `true` 時，如果想要讓用戶端在與相同電腦上的服務進行交談時通過 Proxy，請使用主機名稱 (而非 localhost)。</span><span class="sxs-lookup"><span data-stu-id="1b83a-119">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="1b83a-120">當這個屬性設定為 `false` 時，則所有的網際網路要求都會通過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-120">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="1b83a-121"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1b83a-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1b83a-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1b83a-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1b83a-123">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="1b83a-124">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="1b83a-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1b83a-125">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="1b83a-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1b83a-126">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="1b83a-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="1b83a-127">整數值，指定配置供從通道接收訊息之訊息緩衝區管理員使用的最大記憶體量。</span><span class="sxs-lookup"><span data-stu-id="1b83a-127">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="1b83a-128">預設值為 524288 (0x80000) 位元組。</span><span class="sxs-lookup"><span data-stu-id="1b83a-128">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="1b83a-129">緩衝區管理員會利用緩衝區集區，將使用緩衝區的成本降至最低。</span><span class="sxs-lookup"><span data-stu-id="1b83a-129">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="1b83a-130">當訊息從通道送出時，服務將需要緩衝區來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1b83a-130">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="1b83a-131">如果緩衝區集區中沒有足夠的記憶體可以處理訊息負載，緩衝區管理員就必須從 CLR 堆積配置額外的記憶體，進而增加記憶體回收負荷。</span><span class="sxs-lookup"><span data-stu-id="1b83a-131">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="1b83a-132">從 CLR 記憶體回收堆積所產生的大量配置表示緩衝區集區太小，而提高這個屬性指定的限制來提供較大的配置，便可改善效能。</span><span class="sxs-lookup"><span data-stu-id="1b83a-132">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="1b83a-133">整數值，指定儲存訊息之緩衝區的大小上限 (以位元組為單位)。在為此繫結設定的端點處理訊息時，可以將訊息儲存在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="1b83a-133">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="1b83a-134">預設值為 65,536 位元組。</span><span class="sxs-lookup"><span data-stu-id="1b83a-134">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="1b83a-135">正整數，定義在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="1b83a-135">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1b83a-136">如果對收件者而言訊息太大，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b83a-136">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="1b83a-137">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="1b83a-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1b83a-138">預設值為 65,536 個位元組。</span><span class="sxs-lookup"><span data-stu-id="1b83a-138">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="1b83a-139">定義用來對 SOAP 訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-139">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="1b83a-140">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="1b83a-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1b83a-141">-Text：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-141">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="1b83a-142">-Mtom：使用訊息傳輸組織機制1.0 （MTOM）編碼器。</span><span class="sxs-lookup"><span data-stu-id="1b83a-142">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="1b83a-143">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="1b83a-143">The default is Text.</span></span> <span data-ttu-id="1b83a-144">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-144">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="1b83a-145">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="1b83a-145">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1b83a-146">這個值在相同類型的系結中應該是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1b83a-146">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="1b83a-147">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="1b83a-147">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1b83a-148">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="1b83a-148">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1b83a-149"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1b83a-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1b83a-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1b83a-151">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1b83a-151">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="1b83a-152">包含 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="1b83a-152">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="1b83a-153">如果 `useSystemWebProxy` 設定為 `true`，則這個設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="1b83a-153">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="1b83a-154">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="1b83a-154">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1b83a-155"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1b83a-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1b83a-156">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1b83a-157">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="1b83a-157">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1b83a-158"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1b83a-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1b83a-159">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1b83a-160">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1b83a-160">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="1b83a-161">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="1b83a-161">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="1b83a-162">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="1b83a-162">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1b83a-163">-BigEndianUnicode： Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="1b83a-163">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="1b83a-164">-Unicode：16位編碼方式。</span><span class="sxs-lookup"><span data-stu-id="1b83a-164">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="1b83a-165">-UTF8：8位編碼</span><span class="sxs-lookup"><span data-stu-id="1b83a-165">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="1b83a-166">預設值為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="1b83a-166">The default is UTF8.</span></span> <span data-ttu-id="1b83a-167">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-167">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="1b83a-168">有效的 <xref:System.ServiceModel.TransferMode> 值，指定進行要求或回應時，訊息是經過緩衝處理或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="1b83a-168">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="1b83a-169">布林值，指定是否應使用系統自動設定的 HTTP Proxy (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="1b83a-169">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="1b83a-170">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="1b83a-170">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b83a-171">子元素</span><span class="sxs-lookup"><span data-stu-id="1b83a-171">Child Elements</span></span>  
  
|<span data-ttu-id="1b83a-172">元素</span><span class="sxs-lookup"><span data-stu-id="1b83a-172">Element</span></span>|<span data-ttu-id="1b83a-173">描述</span><span class="sxs-lookup"><span data-stu-id="1b83a-173">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="1b83a-174">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1b83a-174">Defines the security settings for the binding.</span></span> <span data-ttu-id="1b83a-175">此項目的型別為 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-175">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1b83a-176">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="1b83a-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1b83a-177">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="1b83a-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b83a-178">父項目</span><span class="sxs-lookup"><span data-stu-id="1b83a-178">Parent Elements</span></span>  
  
|<span data-ttu-id="1b83a-179">元素</span><span class="sxs-lookup"><span data-stu-id="1b83a-179">Element</span></span>|<span data-ttu-id="1b83a-180">描述</span><span class="sxs-lookup"><span data-stu-id="1b83a-180">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1b83a-181">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="1b83a-181">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b83a-182">備註</span><span class="sxs-lookup"><span data-stu-id="1b83a-182">Remarks</span></span>  
 <span data-ttu-id="1b83a-183">BasicHttpBinding 使用 HTTP 做為傳送 SOAP 1.1 訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="1b83a-183">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="1b83a-184">服務可使用這個繫結公開符合 WS-I BP 1.1 的端點，例如 ASMX 用戶端取用的端點。</span><span class="sxs-lookup"><span data-stu-id="1b83a-184">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="1b83a-185">同樣地，用戶端可使用 BasicHttpBinding 與公開符合 WS-I BP 1.1 之端點的服務通訊，例如 ASMX Web 服務或使用 BasicHttpBinding 設定的服務。</span><span class="sxs-lookup"><span data-stu-id="1b83a-185">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="1b83a-186">安全性預設是關閉的，但是可以將子專案的 mode 屬性設為以外 [\<security>](security-of-basichttpbinding.md) 的值來新增 `None` 。</span><span class="sxs-lookup"><span data-stu-id="1b83a-186">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="1b83a-187">根據預設，它使用「文字」訊息編碼和 UTF-8 文字編碼。</span><span class="sxs-lookup"><span data-stu-id="1b83a-187">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b83a-188">範例</span><span class="sxs-lookup"><span data-stu-id="1b83a-188">Example</span></span>  
 <span data-ttu-id="1b83a-189">下列範例示範 <xref:System.ServiceModel.BasicHttpBinding> 的使用方式，它利用第一代和第二代 Web 服務來提供 HTTP 通訊和最大的互通性。</span><span class="sxs-lookup"><span data-stu-id="1b83a-189">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="1b83a-190">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="1b83a-190">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="1b83a-191">繫結型別是使用 `binding` 項目的 `<endpoint>` 屬性所指定的。</span><span class="sxs-lookup"><span data-stu-id="1b83a-191">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="1b83a-192">如果您要設定基本繫結，並變更其部分設定，則必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="1b83a-192">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="1b83a-193">端點必須使用 `bindingConfiguration` 項目的 `<endpoint>` 屬性來按照名稱參考繫結組態，如下列服務的組態程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1b83a-193">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="1b83a-194">範例</span><span class="sxs-lookup"><span data-stu-id="1b83a-194">Example</span></span>  
 <span data-ttu-id="1b83a-195">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="1b83a-195">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1b83a-196">從端點位址和系結中的名稱移除 bindingConfiguration，即可完成上一個範例中的功能。</span><span class="sxs-lookup"><span data-stu-id="1b83a-196">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="1b83a-197">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="1b83a-197">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b83a-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b83a-198">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="1b83a-199">繫結</span><span class="sxs-lookup"><span data-stu-id="1b83a-199">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1b83a-200">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="1b83a-200">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1b83a-201">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="1b83a-201">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
