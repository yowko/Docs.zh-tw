---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: 2364eb9d82fd17bd0b80b01070a0f1d789be3d90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556150"
---
# \<netNamedPipeBinding>
<span data-ttu-id="6cfe8-101">為電腦上跨處理序通訊定義安全、可靠且經過最佳化的繫結。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-101">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="6cfe8-102">根據預設，這個繫結會產生一個執行階段通訊堆疊，並且具備 WS-ReliableMessaging (提供可靠性)、傳輸安全性、具名管道 (用於訊息傳遞) 和二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-102">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="6cfe8-103">語法</span><span class="sxs-lookup"><span data-stu-id="6cfe8-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cfe8-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6cfe8-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6cfe8-105">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6cfe8-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cfe8-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6cfe8-106">Attributes</span></span>  
  
|<span data-ttu-id="6cfe8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6cfe8-107">Attribute</span></span>|<span data-ttu-id="6cfe8-108">描述</span><span class="sxs-lookup"><span data-stu-id="6cfe8-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cfe8-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="6cfe8-109">closeTimeout</span></span>|<span data-ttu-id="6cfe8-110"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6cfe8-111">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6cfe8-112">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6cfe8-113">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="6cfe8-113">hostNameComparisonMode</span></span>|<span data-ttu-id="6cfe8-114">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="6cfe8-115">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6cfe8-116">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="6cfe8-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6cfe8-117">maxBufferPoolSize</span></span>|<span data-ttu-id="6cfe8-118">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-118">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="6cfe8-119">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-119">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="6cfe8-120">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-120">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="6cfe8-121">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6cfe8-122">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="6cfe8-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6cfe8-123">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6cfe8-124">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="6cfe8-124">maxBufferSize</span></span>|<span data-ttu-id="6cfe8-125">正整數，指定記憶體中用來儲存訊息的緩衝區大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="6cfe8-126">如果緩衝區已滿，超過的資料會保留在基礎通訊端中，直到緩衝區再度有空間為止。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-126">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="6cfe8-127">這個值不能小於 `maxReceivedMessageSize` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-127">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="6cfe8-128">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-128">The default is 65536.</span></span> <span data-ttu-id="6cfe8-129">如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="6cfe8-130">maxConnections</span><span class="sxs-lookup"><span data-stu-id="6cfe8-130">maxConnections</span></span>|<span data-ttu-id="6cfe8-131">整數，指定服務建立/接受的傳出和傳入連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-131">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="6cfe8-132">傳入和傳出連線是依據此屬性指定的個別限制來計算的。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-132">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="6cfe8-133">超過限制的傳入連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-133">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="6cfe8-134">超過限制的傳出連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-134">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="6cfe8-135">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-135">The default is 10.</span></span>|  
|<span data-ttu-id="6cfe8-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6cfe8-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="6cfe8-137">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6cfe8-138">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="6cfe8-139">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6cfe8-140">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-140">The default is 65536.</span></span>|  
|<span data-ttu-id="6cfe8-141">名稱</span><span class="sxs-lookup"><span data-stu-id="6cfe8-141">name</span></span>|<span data-ttu-id="6cfe8-142">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-142">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6cfe8-143">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-143">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6cfe8-144">從 .NET Framework 4 開始，系結和行為不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-144">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6cfe8-145">如需預設設定和無值系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)[的 WCF 服務設定和簡化的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-145">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="6cfe8-146">openTimeout</span><span class="sxs-lookup"><span data-stu-id="6cfe8-146">openTimeout</span></span>|<span data-ttu-id="6cfe8-147"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6cfe8-148">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6cfe8-149">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-149">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6cfe8-150">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6cfe8-150">receiveTimeout</span></span>|<span data-ttu-id="6cfe8-151"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6cfe8-152">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6cfe8-153">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-153">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="6cfe8-154">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="6cfe8-154">sendTimeout</span></span>|<span data-ttu-id="6cfe8-155"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6cfe8-156">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6cfe8-157">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6cfe8-158">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="6cfe8-158">transactionFlow</span></span>|<span data-ttu-id="6cfe8-159">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="6cfe8-160">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-160">The default is `false`.</span></span>|  
|<span data-ttu-id="6cfe8-161">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="6cfe8-161">transactionProtocol</span></span>|<span data-ttu-id="6cfe8-162">指定要搭配此繫結程序使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="6cfe8-163">有效值為</span><span class="sxs-lookup"><span data-stu-id="6cfe8-163">Valid values are</span></span><br /><br /> <span data-ttu-id="6cfe8-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="6cfe8-164">-   OleTransactions</span></span><br /><span data-ttu-id="6cfe8-165">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="6cfe8-165">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="6cfe8-166">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-166">The default is OleTransactions.</span></span> <span data-ttu-id="6cfe8-167">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="6cfe8-168">transferMode</span><span class="sxs-lookup"><span data-stu-id="6cfe8-168">transferMode</span></span>|<span data-ttu-id="6cfe8-169"><xref:System.ServiceModel.TransferMode> 值，指定訊息要經過緩衝處理或資料流處理，或為要求或回應。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-169">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cfe8-170">子元素</span><span class="sxs-lookup"><span data-stu-id="6cfe8-170">Child Elements</span></span>  
  
|<span data-ttu-id="6cfe8-171">項目</span><span class="sxs-lookup"><span data-stu-id="6cfe8-171">Element</span></span>|<span data-ttu-id="6cfe8-172">描述</span><span class="sxs-lookup"><span data-stu-id="6cfe8-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="6cfe8-173">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="6cfe8-174">此項目的型別為 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-174">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="6cfe8-175">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6cfe8-176">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6cfe8-177">父項目</span><span class="sxs-lookup"><span data-stu-id="6cfe8-177">Parent Elements</span></span>  
  
|<span data-ttu-id="6cfe8-178">項目</span><span class="sxs-lookup"><span data-stu-id="6cfe8-178">Element</span></span>|<span data-ttu-id="6cfe8-179">描述</span><span class="sxs-lookup"><span data-stu-id="6cfe8-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="6cfe8-180">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cfe8-181">備註</span><span class="sxs-lookup"><span data-stu-id="6cfe8-181">Remarks</span></span>  
 <span data-ttu-id="6cfe8-182">根據預設，`NetNamedPipeBinding` 會產生執行階段通訊堆疊，此堆疊使用傳輸安全性、具名管道 (用於訊息傳遞) 和二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-182">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="6cfe8-183">此繫結為適當的 Windows Communication Foundation (WCF) 系統提供的現成選擇，可用於電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-183">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="6cfe8-184">它也支援交易。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-184">It also supports transactions.</span></span>  
  
 <span data-ttu-id="6cfe8-185">`NetNamedPipeBinding` 的預設組態類似於 `NetTcpBinding` 所提供的組態，但較為簡單，因為 WCF 實作只針對電腦應用，所以公開的功能不多。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-185">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="6cfe8-186">最顯著的差異在於，`securityMode` 設定只提供 `None` 和 `Transport` 選項。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-186">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="6cfe8-187">SOAP 安全性支援並非包含的選項。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-187">SOAP security support is not an included option.</span></span> <span data-ttu-id="6cfe8-188">安全性行為可以使用選擇性的 `securityMode` 屬性進行設定。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cfe8-189">範例</span><span class="sxs-lookup"><span data-stu-id="6cfe8-189">Example</span></span>  
 <span data-ttu-id="6cfe8-190">下列範例示範 netNamedPipeBinding 繫結，這會在相同電腦上提供跨處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-190">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="6cfe8-191">具名通道不會跨電腦作業。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-191">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="6cfe8-192">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-192">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="6cfe8-193">繫結型別是在 `binding` 項目的 `<endpoint>` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-193">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="6cfe8-194">如果您要設定 netNamedPipeBinding 繫結，並變更其部分設定，則您必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-194">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="6cfe8-195">端點必須使用 `bindingConfiguration` 屬性，按照名稱參考繫結組態。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-195">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="6cfe8-196">在這個範例中，繫結組態的名稱為 Binding1。</span><span class="sxs-lookup"><span data-stu-id="6cfe8-196">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6cfe8-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cfe8-197">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="6cfe8-198">繫結</span><span class="sxs-lookup"><span data-stu-id="6cfe8-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6cfe8-199">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6cfe8-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6cfe8-200">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="6cfe8-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
