---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: f2c1335795ffd3cb395a7006bfaeb3cf7b39636b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448617"
---
# \<tcpTransport>
<span data-ttu-id="c5810-101">定義 TCP 傳輸，通道可使用此傳輸來傳輸自訂繫結的訊息。</span><span class="sxs-lookup"><span data-stu-id="c5810-101">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="c5810-102">語法</span><span class="sxs-lookup"><span data-stu-id="c5810-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5810-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5810-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5810-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c5810-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5810-105">屬性</span><span class="sxs-lookup"><span data-stu-id="c5810-105">Attributes</span></span>  
  
|<span data-ttu-id="c5810-106">屬性</span><span class="sxs-lookup"><span data-stu-id="c5810-106">Attribute</span></span>|<span data-ttu-id="c5810-107">描述</span><span class="sxs-lookup"><span data-stu-id="c5810-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5810-108">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="c5810-108">channelInitializationTimeout</span></span>|<span data-ttu-id="c5810-109">取得或設定接受通道初始化的時間限制。</span><span class="sxs-lookup"><span data-stu-id="c5810-109">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="c5810-110">通道在中斷連接之前，可以處於初始化狀態中的最長時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="c5810-110">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="c5810-111">此配額包含 TCP 連線使用 .NET 訊息框架通訊協定來驗證本身時可以採取的時間。</span><span class="sxs-lookup"><span data-stu-id="c5810-111">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="c5810-112">用戶端必須先傳送一些初始資料，讓伺服器有足夠的資訊來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="c5810-112">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="c5810-113">預設值為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="c5810-113">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="c5810-114">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="c5810-114">connectionBufferSize</span></span>|<span data-ttu-id="c5810-115">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c5810-115">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="c5810-116">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c5810-116">hostNameComparisonMode</span></span>|<span data-ttu-id="c5810-117">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="c5810-117">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="c5810-118">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="c5810-118">listenBacklog</span></span>|<span data-ttu-id="c5810-119">Web 服務可擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="c5810-119">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="c5810-120">`connectionLeaseTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的持續時間。</span><span class="sxs-lookup"><span data-stu-id="c5810-120">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="c5810-121">這是通訊端層級屬性，用來控制 Web 服務可擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="c5810-121">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="c5810-122">當 ListenBacklog 太低時，WCF 將會停止接受要求，因此會卸載新的連接，直到伺服器認可某些現有的佇列連接為止。</span><span class="sxs-lookup"><span data-stu-id="c5810-122">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="c5810-123">預設值為 16 \* 處理器數目。</span><span class="sxs-lookup"><span data-stu-id="c5810-123">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="c5810-124">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="c5810-124">manualAddressing</span></span>|<span data-ttu-id="c5810-125">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="c5810-125">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="c5810-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c5810-126">maxBufferPoolSize</span></span>|<span data-ttu-id="c5810-127">取得或設定此傳輸所使用之任何緩衝區集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="c5810-127">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="c5810-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c5810-128">maxBufferSize</span></span>|<span data-ttu-id="c5810-129">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="c5810-129">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="c5810-130">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="c5810-130">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="c5810-131">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="c5810-131">maxOutputDelay</span></span>|<span data-ttu-id="c5810-132">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c5810-132">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="c5810-133">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="c5810-133">maxPendingAccepts</span></span>|<span data-ttu-id="c5810-134">取得或設定可用於處理服務傳入連線的擱置中非同步接受作業的數目上限。</span><span class="sxs-lookup"><span data-stu-id="c5810-134">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="c5810-135">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c5810-135">maxPendingConnections</span></span>|<span data-ttu-id="c5810-136">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="c5810-136">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c5810-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c5810-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="c5810-138">取得及設定可接收之可允許的訊息大小上限。</span><span class="sxs-lookup"><span data-stu-id="c5810-138">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="c5810-139">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="c5810-139">portSharingEnabled</span></span>|<span data-ttu-id="c5810-140">布林值，指定是否啟用這個連線的 TCP 連接埠共用功能。</span><span class="sxs-lookup"><span data-stu-id="c5810-140">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="c5810-141">如果這是 `false`，則每個繫結將使用它自己的獨佔連接埠。</span><span class="sxs-lookup"><span data-stu-id="c5810-141">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="c5810-142">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c5810-142">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c5810-143">這個設定只與服務有關。</span><span class="sxs-lookup"><span data-stu-id="c5810-143">This setting is relevant only to services.</span></span> <span data-ttu-id="c5810-144">用戶端不受影響。</span><span class="sxs-lookup"><span data-stu-id="c5810-144">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="c5810-145">使用這個設定必須將 [啟動類型] 改為 [手動] 或 [自動]，以啟用 Windows Communication Foundation (WCF) TCP Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="c5810-145">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="c5810-146">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="c5810-146">teredoEnabled</span></span>|<span data-ttu-id="c5810-147">布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。</span><span class="sxs-lookup"><span data-stu-id="c5810-147">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="c5810-148">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c5810-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c5810-149">這個屬性會針對基礎 TCP 通訊端啟用 Teredo。</span><span class="sxs-lookup"><span data-stu-id="c5810-149">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="c5810-150">如需詳細資訊，請參閱[Teredo 總覽](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10))。</span><span class="sxs-lookup"><span data-stu-id="c5810-150">For more information, see [Teredo Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span></span><br /><br /> <span data-ttu-id="c5810-151">此屬性僅適用于 Windows XP SP2 和 Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="c5810-151">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="c5810-152">Windows Vista 有適用于 Teredo 的全電腦設定選項，因此在執行 Vista 時，會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="c5810-152">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="c5810-153">Teredo 需要用戶端和服務電腦都已安裝 Microsoft IPv6 堆疊並正確設定，才能使用 Teredo。</span><span class="sxs-lookup"><span data-stu-id="c5810-153">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span>|  
|<span data-ttu-id="c5810-154">transferMode</span><span class="sxs-lookup"><span data-stu-id="c5810-154">transferMode</span></span>|<span data-ttu-id="c5810-155">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="c5810-155">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="c5810-156">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c5810-156">connectionPoolSettings</span></span>|<span data-ttu-id="c5810-157">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="c5810-157">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5810-158">子元素</span><span class="sxs-lookup"><span data-stu-id="c5810-158">Child Elements</span></span>  
 <span data-ttu-id="c5810-159">無</span><span class="sxs-lookup"><span data-stu-id="c5810-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5810-160">父項目</span><span class="sxs-lookup"><span data-stu-id="c5810-160">Parent Elements</span></span>  
  
|<span data-ttu-id="c5810-161">元素</span><span class="sxs-lookup"><span data-stu-id="c5810-161">Element</span></span>|<span data-ttu-id="c5810-162">描述</span><span class="sxs-lookup"><span data-stu-id="c5810-162">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c5810-163">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="c5810-163">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5810-164">備註</span><span class="sxs-lookup"><span data-stu-id="c5810-164">Remarks</span></span>  
 <span data-ttu-id="c5810-165">這個傳輸會使用以下格式的 URI "net.tcp://hostname:port/path"。</span><span class="sxs-lookup"><span data-stu-id="c5810-165">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="c5810-166">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c5810-166">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="c5810-167">`tcpTransport` 項目是在建立自訂繫結時的起點，該繫結會實作 TCP 傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c5810-167">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="c5810-168">這個傳輸已針對 WCF 至 WCF 的通訊最佳化。</span><span class="sxs-lookup"><span data-stu-id="c5810-168">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5810-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5810-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c5810-170">傳輸</span><span class="sxs-lookup"><span data-stu-id="c5810-170">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="c5810-171">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="c5810-171">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c5810-172">繫結</span><span class="sxs-lookup"><span data-stu-id="c5810-172">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c5810-173">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="c5810-173">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c5810-174">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="c5810-174">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
