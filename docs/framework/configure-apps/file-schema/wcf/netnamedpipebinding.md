---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: dc1af462222920c7b3c6b66c3822e7b2b326b244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778504"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="87b4d-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="87b4d-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="87b4d-102">為電腦上跨處理序通訊定義安全、可靠且經過最佳化的繫結。</span><span class="sxs-lookup"><span data-stu-id="87b4d-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="87b4d-103">根據預設，這個繫結會產生一個執行階段通訊堆疊，並且具備 WS-ReliableMessaging (提供可靠性)、傳輸安全性、具名管道 (用於訊息傳遞) 和二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="87b4d-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="87b4d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87b4d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87b4d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="87b4d-105">\<bindings></span></span>  
<span data-ttu-id="87b4d-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="87b4d-106">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b4d-107">語法</span><span class="sxs-lookup"><span data-stu-id="87b4d-107">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87b4d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87b4d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87b4d-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="87b4d-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87b4d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="87b4d-110">Attributes</span></span>  
  
|<span data-ttu-id="87b4d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="87b4d-111">Attribute</span></span>|<span data-ttu-id="87b4d-112">描述</span><span class="sxs-lookup"><span data-stu-id="87b4d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87b4d-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="87b4d-113">closeTimeout</span></span>|<span data-ttu-id="87b4d-114"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="87b4d-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="87b4d-115">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87b4d-116">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="87b4d-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="87b4d-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="87b4d-117">hostNameComparisonMode</span></span>|<span data-ttu-id="87b4d-118">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="87b4d-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="87b4d-119">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="87b4d-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="87b4d-120">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="87b4d-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="87b4d-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="87b4d-121">maxBufferPoolSize</span></span>|<span data-ttu-id="87b4d-122">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="87b4d-122">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="87b4d-123">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="87b4d-123">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="87b4d-124">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="87b4d-124">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="87b4d-125">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="87b4d-125">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="87b4d-126">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="87b4d-126">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="87b4d-127">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="87b4d-127">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="87b4d-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="87b4d-128">maxBufferSize</span></span>|<span data-ttu-id="87b4d-129">正整數，指定記憶體中用來儲存訊息的緩衝區大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="87b4d-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="87b4d-130">如果緩衝區已滿，超過的資料會保留在基礎通訊端中，直到緩衝區再度有空間為止。</span><span class="sxs-lookup"><span data-stu-id="87b4d-130">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="87b4d-131">這個值不能小於 `maxReceivedMessageSize` 屬性。</span><span class="sxs-lookup"><span data-stu-id="87b4d-131">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="87b4d-132">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="87b4d-132">The default is 65536.</span></span> <span data-ttu-id="87b4d-133">如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="87b4d-134">maxConnections</span><span class="sxs-lookup"><span data-stu-id="87b4d-134">maxConnections</span></span>|<span data-ttu-id="87b4d-135">整數，指定服務建立/接受的傳出和傳入連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="87b4d-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="87b4d-136">傳入和傳出連線是依據此屬性指定的個別限制來計算的。</span><span class="sxs-lookup"><span data-stu-id="87b4d-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="87b4d-137">超過限制的傳入連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="87b4d-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="87b4d-138">超過限制的傳出連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="87b4d-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="87b4d-139">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="87b4d-139">The default is 10.</span></span>|  
|<span data-ttu-id="87b4d-140">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="87b4d-140">maxReceivedMessageSize</span></span>|<span data-ttu-id="87b4d-141">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="87b4d-141">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="87b4d-142">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="87b4d-142">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="87b4d-143">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="87b4d-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="87b4d-144">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="87b4d-144">The default is 65536.</span></span>|  
|<span data-ttu-id="87b4d-145">名稱</span><span class="sxs-lookup"><span data-stu-id="87b4d-145">name</span></span>|<span data-ttu-id="87b4d-146">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="87b4d-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="87b4d-147">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="87b4d-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="87b4d-148">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="87b4d-148">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="87b4d-149">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="87b4d-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="87b4d-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="87b4d-150">openTimeout</span></span>|<span data-ttu-id="87b4d-151"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="87b4d-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="87b4d-152">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87b4d-153">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="87b4d-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="87b4d-154">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="87b4d-154">receiveTimeout</span></span>|<span data-ttu-id="87b4d-155"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="87b4d-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="87b4d-156">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87b4d-157">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="87b4d-157">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="87b4d-158">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="87b4d-158">sendTimeout</span></span>|<span data-ttu-id="87b4d-159"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="87b4d-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="87b4d-160">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87b4d-161">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="87b4d-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="87b4d-162">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="87b4d-162">transactionFlow</span></span>|<span data-ttu-id="87b4d-163">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="87b4d-163">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="87b4d-164">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="87b4d-164">The default is `false`.</span></span>|  
|<span data-ttu-id="87b4d-165">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="87b4d-165">transactionProtocol</span></span>|<span data-ttu-id="87b4d-166">指定要搭配此繫結程序使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="87b4d-166">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="87b4d-167">有效值為</span><span class="sxs-lookup"><span data-stu-id="87b4d-167">Valid values are</span></span><br /><br /> <span data-ttu-id="87b4d-168">-   OleTransactions</span><span class="sxs-lookup"><span data-stu-id="87b4d-168">-   OleTransactions</span></span><br /><span data-ttu-id="87b4d-169">-   WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="87b4d-169">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="87b4d-170">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="87b4d-170">The default is OleTransactions.</span></span> <span data-ttu-id="87b4d-171">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-171">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="87b4d-172">transferMode</span><span class="sxs-lookup"><span data-stu-id="87b4d-172">transferMode</span></span>|<span data-ttu-id="87b4d-173"><xref:System.ServiceModel.TransferMode> 值，指定訊息要經過緩衝處理或資料流處理，或為要求或回應。</span><span class="sxs-lookup"><span data-stu-id="87b4d-173">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87b4d-174">子元素</span><span class="sxs-lookup"><span data-stu-id="87b4d-174">Child Elements</span></span>  
  
|<span data-ttu-id="87b4d-175">項目</span><span class="sxs-lookup"><span data-stu-id="87b4d-175">Element</span></span>|<span data-ttu-id="87b4d-176">描述</span><span class="sxs-lookup"><span data-stu-id="87b4d-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87b4d-177">\<security></span><span class="sxs-lookup"><span data-stu-id="87b4d-177">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="87b4d-178">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="87b4d-178">Defines the security settings for the binding.</span></span> <span data-ttu-id="87b4d-179">此項目的型別為 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-179">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="87b4d-180">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87b4d-180">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="87b4d-181">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="87b4d-181">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="87b4d-182">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="87b4d-182">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87b4d-183">父項目</span><span class="sxs-lookup"><span data-stu-id="87b4d-183">Parent Elements</span></span>  
  
|<span data-ttu-id="87b4d-184">項目</span><span class="sxs-lookup"><span data-stu-id="87b4d-184">Element</span></span>|<span data-ttu-id="87b4d-185">描述</span><span class="sxs-lookup"><span data-stu-id="87b4d-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87b4d-186">\<bindings></span><span class="sxs-lookup"><span data-stu-id="87b4d-186">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="87b4d-187">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="87b4d-187">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87b4d-188">備註</span><span class="sxs-lookup"><span data-stu-id="87b4d-188">Remarks</span></span>  
 <span data-ttu-id="87b4d-189">根據預設，`NetNamedPipeBinding` 會產生執行階段通訊堆疊，此堆疊使用傳輸安全性、具名管道 (用於訊息傳遞) 和二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="87b4d-189">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="87b4d-190">此繫結為適當的 Windows Communication Foundation (WCF) 系統提供的現成選擇，可用於電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="87b4d-190">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="87b4d-191">它也支援交易。</span><span class="sxs-lookup"><span data-stu-id="87b4d-191">It also supports transactions.</span></span>  
  
 <span data-ttu-id="87b4d-192">`NetNamedPipeBinding` 的預設組態類似於 `NetTcpBinding` 所提供的組態，但較為簡單，因為 WCF 實作只針對電腦應用，所以公開的功能不多。</span><span class="sxs-lookup"><span data-stu-id="87b4d-192">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="87b4d-193">最顯著的差異在於，`securityMode` 設定只提供 `None` 和 `Transport` 選項。</span><span class="sxs-lookup"><span data-stu-id="87b4d-193">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="87b4d-194">SOAP 安全性支援並非包含的選項。</span><span class="sxs-lookup"><span data-stu-id="87b4d-194">SOAP security support is not an included option.</span></span> <span data-ttu-id="87b4d-195">安全性行為可以使用選擇性的 `securityMode` 屬性進行設定。</span><span class="sxs-lookup"><span data-stu-id="87b4d-195">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87b4d-196">範例</span><span class="sxs-lookup"><span data-stu-id="87b4d-196">Example</span></span>  
 <span data-ttu-id="87b4d-197">下列範例示範 netNamedPipeBinding 繫結，這會在相同電腦上提供跨處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="87b4d-197">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="87b4d-198">具名通道不會跨電腦作業。</span><span class="sxs-lookup"><span data-stu-id="87b4d-198">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="87b4d-199">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="87b4d-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="87b4d-200">繫結型別是在 `binding` 項目的 `<endpoint>` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="87b4d-200">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="87b4d-201">如果您要設定 netNamedPipeBinding 繫結，並變更其部分設定，則您必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="87b4d-201">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="87b4d-202">端點必須使用 `bindingConfiguration` 屬性，按照名稱參考繫結組態。</span><span class="sxs-lookup"><span data-stu-id="87b4d-202">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="87b4d-203">在這個範例中，繫結組態的名稱為 Binding1。</span><span class="sxs-lookup"><span data-stu-id="87b4d-203">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="87b4d-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87b4d-204">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="87b4d-205">\<binding></span><span class="sxs-lookup"><span data-stu-id="87b4d-205">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="87b4d-206">繫結</span><span class="sxs-lookup"><span data-stu-id="87b4d-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="87b4d-207">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="87b4d-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="87b4d-208">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="87b4d-208">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
