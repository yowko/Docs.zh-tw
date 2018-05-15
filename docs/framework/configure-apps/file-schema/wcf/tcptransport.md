---
title: '&lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 4141b0f6493c51048ad60accdc1d5ee9bac01231
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttcptransportgt"></a><span data-ttu-id="99ca5-102">&lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="99ca5-102">&lt;tcpTransport&gt;</span></span>
<span data-ttu-id="99ca5-103">定義 TCP 傳輸，通道可使用此傳輸來傳輸自訂繫結的訊息。</span><span class="sxs-lookup"><span data-stu-id="99ca5-103">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
 <span data-ttu-id="99ca5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99ca5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="99ca5-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="99ca5-105">\<bindings></span></span>  
<span data-ttu-id="99ca5-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="99ca5-106">\<customBinding></span></span>  
<span data-ttu-id="99ca5-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="99ca5-107">\<binding></span></span>  
<span data-ttu-id="99ca5-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="99ca5-108">\<tcpTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ca5-109">語法</span><span class="sxs-lookup"><span data-stu-id="99ca5-109">Syntax</span></span>  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99ca5-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99ca5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99ca5-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="99ca5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99ca5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="99ca5-112">Attributes</span></span>  
  
|<span data-ttu-id="99ca5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="99ca5-113">Attribute</span></span>|<span data-ttu-id="99ca5-114">描述</span><span class="sxs-lookup"><span data-stu-id="99ca5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99ca5-115">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="99ca5-115">channelInitializationTimeout</span></span>|<span data-ttu-id="99ca5-116">取得或設定接受通道初始化的時間限制。</span><span class="sxs-lookup"><span data-stu-id="99ca5-116">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="99ca5-117">通道在中斷連接之前，可以處於初始化狀態中的最長時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="99ca5-117">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="99ca5-118">這個配額包含 TCP 連接可以使用 .Net Message Framing 通訊協定自行驗證所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="99ca5-118">This quota includes the time a TCP connection can take to authenticate itself using the .Net Message Framing protocol.</span></span> <span data-ttu-id="99ca5-119">用戶端必須先傳送一些初始資料，讓伺服器有足夠的資訊來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="99ca5-119">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="99ca5-120">預設為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="99ca5-120">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="99ca5-121">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="99ca5-121">connectionBufferSize</span></span>|<span data-ttu-id="99ca5-122">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="99ca5-122">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="99ca5-123">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="99ca5-123">hostNameComparisonMode</span></span>|<span data-ttu-id="99ca5-124">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="99ca5-124">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="99ca5-125">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="99ca5-125">listenBacklog</span></span>|<span data-ttu-id="99ca5-126">Web 服務可擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="99ca5-126">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="99ca5-127">`connectionLeaseTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的持續時間。</span><span class="sxs-lookup"><span data-stu-id="99ca5-127">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="99ca5-128">這是通訊端層級屬性，用來控制 Web 服務可擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="99ca5-128">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="99ca5-129">當 ListenBacklog 太低時，WCF 會停止接受要求，因此將捨棄新的連接直到伺服器認可佇列中部分現有連接為止。預設值為 16 \* 處理器數量。</span><span class="sxs-lookup"><span data-stu-id="99ca5-129">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections .The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="99ca5-130">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="99ca5-130">manualAddressing</span></span>|<span data-ttu-id="99ca5-131">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="99ca5-131">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="99ca5-132">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="99ca5-132">maxBufferPoolSize</span></span>|<span data-ttu-id="99ca5-133">取得或設定此傳輸所使用之任何緩衝區集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="99ca5-133">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="99ca5-134">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="99ca5-134">maxBufferSize</span></span>|<span data-ttu-id="99ca5-135">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="99ca5-135">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="99ca5-136">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="99ca5-136">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="99ca5-137">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="99ca5-137">maxOutputDelay</span></span>|<span data-ttu-id="99ca5-138">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="99ca5-138">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="99ca5-139">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="99ca5-139">maxPendingAccepts</span></span>|<span data-ttu-id="99ca5-140">取得或設定可用於處理服務傳入連線的擱置中非同步接受作業的數目上限。</span><span class="sxs-lookup"><span data-stu-id="99ca5-140">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="99ca5-141">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="99ca5-141">maxPendingConnections</span></span>|<span data-ttu-id="99ca5-142">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="99ca5-142">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="99ca5-143">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="99ca5-143">maxReceivedMessageSize</span></span>|<span data-ttu-id="99ca5-144">取得及設定可接收之可允許的訊息大小上限。</span><span class="sxs-lookup"><span data-stu-id="99ca5-144">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="99ca5-145">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="99ca5-145">portSharingEnabled</span></span>|<span data-ttu-id="99ca5-146">布林值，指定是否啟用這個連線的 TCP 連接埠共用功能。</span><span class="sxs-lookup"><span data-stu-id="99ca5-146">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="99ca5-147">如果這是 `false`，則每個繫結將使用它自己的獨佔連接埠。</span><span class="sxs-lookup"><span data-stu-id="99ca5-147">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="99ca5-148">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="99ca5-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="99ca5-149">這個設定只與服務有關。</span><span class="sxs-lookup"><span data-stu-id="99ca5-149">This setting is relevant only to services.</span></span> <span data-ttu-id="99ca5-150">用戶端不受影響。</span><span class="sxs-lookup"><span data-stu-id="99ca5-150">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="99ca5-151">使用這個設定必須將 [啟動類型] 改為 [手動] 或 [自動]，以啟用 Windows Communication Foundation (WCF) TCP Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="99ca5-151">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="99ca5-152">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="99ca5-152">teredoEnabled</span></span>|<span data-ttu-id="99ca5-153">布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。</span><span class="sxs-lookup"><span data-stu-id="99ca5-153">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="99ca5-154">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="99ca5-154">The default is `false`.</span></span><br /><br /> <span data-ttu-id="99ca5-155">這個屬性會針對基礎 TCP 通訊端啟用 Teredo。</span><span class="sxs-lookup"><span data-stu-id="99ca5-155">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="99ca5-156">如需詳細資訊，請參閱[Teredo 概觀](http://go.microsoft.com/fwlink/?LinkId=95339)。</span><span class="sxs-lookup"><span data-stu-id="99ca5-156">For more information, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span><br /><br /> <span data-ttu-id="99ca5-157">這個屬性只適用於 [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] 和 [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99ca5-157">This property is applicable only on [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] and [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span></span> [!INCLUDE[wv](../../../../../includes/wv-md.md)]<span data-ttu-id="99ca5-158"> 具有整部機器的 Teredo 組態選項，所以在執行 Vista 時，會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="99ca5-158"> has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="99ca5-159">Teredo 需要用戶端和服務電腦都已安裝 Microsoft IPv6 堆疊並正確設定，才能使用 Teredo。</span><span class="sxs-lookup"><span data-stu-id="99ca5-159">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span> <span data-ttu-id="99ca5-160">如需設定 Teredo 的詳細資訊，請參閱[Teredo 概觀](http://go.microsoft.com/fwlink/?LinkId=95339)。</span><span class="sxs-lookup"><span data-stu-id="99ca5-160">For more information about configuring Teredo, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span> <span data-ttu-id="99ca5-161">如需詳細資訊，請參閱[Windows Server 2003 技術中心](http://go.microsoft.com/fwlink/?LinkId=49888)。</span><span class="sxs-lookup"><span data-stu-id="99ca5-161">For more information, see [Windows Server 2003 Technology Centers](http://go.microsoft.com/fwlink/?LinkId=49888).</span></span>|  
|<span data-ttu-id="99ca5-162">transferMode</span><span class="sxs-lookup"><span data-stu-id="99ca5-162">transferMode</span></span>|<span data-ttu-id="99ca5-163">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="99ca5-163">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="99ca5-164">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="99ca5-164">connectionPoolSettings</span></span>|<span data-ttu-id="99ca5-165">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="99ca5-165">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99ca5-166">子項目</span><span class="sxs-lookup"><span data-stu-id="99ca5-166">Child Elements</span></span>  
 <span data-ttu-id="99ca5-167">無</span><span class="sxs-lookup"><span data-stu-id="99ca5-167">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99ca5-168">父項目</span><span class="sxs-lookup"><span data-stu-id="99ca5-168">Parent Elements</span></span>  
  
|<span data-ttu-id="99ca5-169">項目</span><span class="sxs-lookup"><span data-stu-id="99ca5-169">Element</span></span>|<span data-ttu-id="99ca5-170">描述</span><span class="sxs-lookup"><span data-stu-id="99ca5-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99ca5-171">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="99ca5-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="99ca5-172">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="99ca5-172">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ca5-173">備註</span><span class="sxs-lookup"><span data-stu-id="99ca5-173">Remarks</span></span>  
 <span data-ttu-id="99ca5-174">這個傳輸會使用以下格式的 URI "net.tcp://hostname:port/path"。</span><span class="sxs-lookup"><span data-stu-id="99ca5-174">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="99ca5-175">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="99ca5-175">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="99ca5-176">`tcpTransport` 項目是在建立自訂繫結時的起點，該繫結會實作 TCP 傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="99ca5-176">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="99ca5-177">這個傳輸已針對 WCF 至 WCF 的通訊最佳化。</span><span class="sxs-lookup"><span data-stu-id="99ca5-177">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ca5-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99ca5-178">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="99ca5-179">傳輸</span><span class="sxs-lookup"><span data-stu-id="99ca5-179">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="99ca5-180">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="99ca5-180">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="99ca5-181">繫結</span><span class="sxs-lookup"><span data-stu-id="99ca5-181">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="99ca5-182">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="99ca5-182">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="99ca5-183">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="99ca5-183">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="99ca5-184">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="99ca5-184">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
