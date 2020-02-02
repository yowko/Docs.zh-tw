---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 7101719f77a03909d9a38dca93100ec90c1add13
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921379"
---
# <a name="tcptransport"></a><span data-ttu-id="93e3b-101">\<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="93e3b-101">\<tcpTransport></span></span>
<span data-ttu-id="93e3b-102">定義 TCP 傳輸，通道可使用此傳輸來傳輸自訂繫結的訊息。</span><span class="sxs-lookup"><span data-stu-id="93e3b-102">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
<span data-ttu-id="93e3b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93e3b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93e3b-104">&nbsp;&nbsp;[ **\<system.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="93e3b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="93e3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="93e3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="93e3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="93e3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="93e3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="93e3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="93e3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tcpTransport >**</span><span class="sxs-lookup"><span data-stu-id="93e3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93e3b-109">語法</span><span class="sxs-lookup"><span data-stu-id="93e3b-109">Syntax</span></span>  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
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
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93e3b-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="93e3b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93e3b-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="93e3b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93e3b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="93e3b-112">Attributes</span></span>  
  
|<span data-ttu-id="93e3b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="93e3b-113">Attribute</span></span>|<span data-ttu-id="93e3b-114">描述</span><span class="sxs-lookup"><span data-stu-id="93e3b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93e3b-115">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="93e3b-115">channelInitializationTimeout</span></span>|<span data-ttu-id="93e3b-116">取得或設定接受通道初始化的時間限制。</span><span class="sxs-lookup"><span data-stu-id="93e3b-116">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="93e3b-117">通道在中斷連接之前，可以處於初始化狀態中的最長時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="93e3b-117">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="93e3b-118">此配額包含 TCP 連線使用 .NET 訊息框架通訊協定來驗證本身時可以採取的時間。</span><span class="sxs-lookup"><span data-stu-id="93e3b-118">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="93e3b-119">用戶端必須先傳送一些初始資料，讓伺服器有足夠的資訊來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="93e3b-119">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="93e3b-120">預設為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="93e3b-120">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="93e3b-121">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="93e3b-121">connectionBufferSize</span></span>|<span data-ttu-id="93e3b-122">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="93e3b-122">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="93e3b-123">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="93e3b-123">hostNameComparisonMode</span></span>|<span data-ttu-id="93e3b-124">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="93e3b-124">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="93e3b-125">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="93e3b-125">listenBacklog</span></span>|<span data-ttu-id="93e3b-126">Web 服務可擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="93e3b-126">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="93e3b-127">`connectionLeaseTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的持續時間。</span><span class="sxs-lookup"><span data-stu-id="93e3b-127">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="93e3b-128">這是通訊端層級屬性，用來控制 Web 服務可擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="93e3b-128">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="93e3b-129">當 ListenBacklog 太低時，WCF 將會停止接受要求，因此會卸載新的連接，直到伺服器認可某些現有的佇列連接為止。</span><span class="sxs-lookup"><span data-stu-id="93e3b-129">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="93e3b-130">預設值為 16 \* 處理器數目。</span><span class="sxs-lookup"><span data-stu-id="93e3b-130">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="93e3b-131">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="93e3b-131">manualAddressing</span></span>|<span data-ttu-id="93e3b-132">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="93e3b-132">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="93e3b-133">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="93e3b-133">maxBufferPoolSize</span></span>|<span data-ttu-id="93e3b-134">取得或設定此傳輸所使用之任何緩衝區集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="93e3b-134">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="93e3b-135">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="93e3b-135">maxBufferSize</span></span>|<span data-ttu-id="93e3b-136">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="93e3b-136">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="93e3b-137">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="93e3b-137">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="93e3b-138">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="93e3b-138">maxOutputDelay</span></span>|<span data-ttu-id="93e3b-139">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="93e3b-139">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="93e3b-140">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="93e3b-140">maxPendingAccepts</span></span>|<span data-ttu-id="93e3b-141">取得或設定可用於處理服務傳入連線的擱置中非同步接受作業的數目上限。</span><span class="sxs-lookup"><span data-stu-id="93e3b-141">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="93e3b-142">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="93e3b-142">maxPendingConnections</span></span>|<span data-ttu-id="93e3b-143">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="93e3b-143">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="93e3b-144">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="93e3b-144">maxReceivedMessageSize</span></span>|<span data-ttu-id="93e3b-145">取得及設定可接收之可允許的訊息大小上限。</span><span class="sxs-lookup"><span data-stu-id="93e3b-145">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="93e3b-146">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="93e3b-146">portSharingEnabled</span></span>|<span data-ttu-id="93e3b-147">布林值，指定是否啟用這個連線的 TCP 連接埠共用功能。</span><span class="sxs-lookup"><span data-stu-id="93e3b-147">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="93e3b-148">如果這是 `false`，則每個繫結將使用它自己的獨佔連接埠。</span><span class="sxs-lookup"><span data-stu-id="93e3b-148">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="93e3b-149">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="93e3b-149">The default is `false`.</span></span><br /><br /> <span data-ttu-id="93e3b-150">這個設定只與服務有關。</span><span class="sxs-lookup"><span data-stu-id="93e3b-150">This setting is relevant only to services.</span></span> <span data-ttu-id="93e3b-151">用戶端不受影響。</span><span class="sxs-lookup"><span data-stu-id="93e3b-151">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="93e3b-152">使用這個設定必須將 [啟動類型] 改為 [手動] 或 [自動]，以啟用 Windows Communication Foundation (WCF) TCP Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="93e3b-152">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="93e3b-153">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="93e3b-153">teredoEnabled</span></span>|<span data-ttu-id="93e3b-154">布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。</span><span class="sxs-lookup"><span data-stu-id="93e3b-154">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="93e3b-155">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="93e3b-155">The default is `false`.</span></span><br /><br /> <span data-ttu-id="93e3b-156">這個屬性會針對基礎 TCP 通訊端啟用 Teredo。</span><span class="sxs-lookup"><span data-stu-id="93e3b-156">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="93e3b-157">如需詳細資訊，請參閱[Teredo 總覽](https://go.microsoft.com/fwlink/?LinkId=95339)。</span><span class="sxs-lookup"><span data-stu-id="93e3b-157">For more information, see [Teredo Overview](https://go.microsoft.com/fwlink/?LinkId=95339).</span></span><br /><br /> <span data-ttu-id="93e3b-158">此屬性僅適用于 Windows XP SP2 和 Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="93e3b-158">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="93e3b-159">Windows Vista 有適用于 Teredo 的全電腦設定選項，因此在執行 Vista 時，會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="93e3b-159">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="93e3b-160">Teredo 需要用戶端和服務電腦都已安裝 Microsoft IPv6 堆疊並正確設定，才能使用 Teredo。</span><span class="sxs-lookup"><span data-stu-id="93e3b-160">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span> <span data-ttu-id="93e3b-161">如需設定 Teredo 的詳細資訊，請參閱[Teredo 總覽](https://go.microsoft.com/fwlink/?LinkId=95339)。</span><span class="sxs-lookup"><span data-stu-id="93e3b-161">For more information about configuring Teredo, see [Teredo Overview](https://go.microsoft.com/fwlink/?LinkId=95339).</span></span> <span data-ttu-id="93e3b-162">如需詳細資訊，請參閱[Windows Server 2003 技術中心](https://go.microsoft.com/fwlink/?LinkId=49888)。</span><span class="sxs-lookup"><span data-stu-id="93e3b-162">For more information, see [Windows Server 2003 Technology Centers](https://go.microsoft.com/fwlink/?LinkId=49888).</span></span>|  
|<span data-ttu-id="93e3b-163">transferMode</span><span class="sxs-lookup"><span data-stu-id="93e3b-163">transferMode</span></span>|<span data-ttu-id="93e3b-164">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="93e3b-164">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="93e3b-165">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="93e3b-165">connectionPoolSettings</span></span>|<span data-ttu-id="93e3b-166">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="93e3b-166">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93e3b-167">子項目</span><span class="sxs-lookup"><span data-stu-id="93e3b-167">Child Elements</span></span>  
 <span data-ttu-id="93e3b-168">None</span><span class="sxs-lookup"><span data-stu-id="93e3b-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93e3b-169">父項目</span><span class="sxs-lookup"><span data-stu-id="93e3b-169">Parent Elements</span></span>  
  
|<span data-ttu-id="93e3b-170">項目</span><span class="sxs-lookup"><span data-stu-id="93e3b-170">Element</span></span>|<span data-ttu-id="93e3b-171">描述</span><span class="sxs-lookup"><span data-stu-id="93e3b-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93e3b-172">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="93e3b-172">\<binding></span></span>](bindings.md)|<span data-ttu-id="93e3b-173">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="93e3b-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93e3b-174">備註</span><span class="sxs-lookup"><span data-stu-id="93e3b-174">Remarks</span></span>  
 <span data-ttu-id="93e3b-175">這個傳輸會使用以下格式的 URI "net.tcp://hostname:port/path"。</span><span class="sxs-lookup"><span data-stu-id="93e3b-175">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="93e3b-176">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="93e3b-176">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="93e3b-177">`tcpTransport` 項目是在建立自訂繫結時的起點，該繫結會實作 TCP 傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="93e3b-177">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="93e3b-178">這個傳輸已針對 WCF 至 WCF 的通訊最佳化。</span><span class="sxs-lookup"><span data-stu-id="93e3b-178">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e3b-179">請參閱</span><span class="sxs-lookup"><span data-stu-id="93e3b-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="93e3b-180">傳輸</span><span class="sxs-lookup"><span data-stu-id="93e3b-180">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="93e3b-181">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="93e3b-181">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="93e3b-182">繫結</span><span class="sxs-lookup"><span data-stu-id="93e3b-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="93e3b-183">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="93e3b-183">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="93e3b-184">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="93e3b-184">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="93e3b-185">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="93e3b-185">\<customBinding></span></span>](custombinding.md)
