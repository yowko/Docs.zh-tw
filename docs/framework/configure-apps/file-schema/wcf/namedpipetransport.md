---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933210"
---
# <a name="namedpipetransport"></a><span data-ttu-id="a4fbe-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="a4fbe-101">\<namedPipeTransport></span></span>
<span data-ttu-id="a4fbe-102">定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="a4fbe-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a4fbe-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a4fbe-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a4fbe-104">\<bindings></span></span>  
<span data-ttu-id="a4fbe-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a4fbe-105">\<customBinding></span></span>  
<span data-ttu-id="a4fbe-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="a4fbe-106">\<binding></span></span>  
<span data-ttu-id="a4fbe-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="a4fbe-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4fbe-108">語法</span><span class="sxs-lookup"><span data-stu-id="a4fbe-108">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4fbe-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a4fbe-109">Attributes and Elements</span></span>  
<span data-ttu-id="a4fbe-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4fbe-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a4fbe-111">Attributes</span></span>  
<span data-ttu-id="a4fbe-112">無。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4fbe-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a4fbe-113">Child Elements</span></span>  
  
|<span data-ttu-id="a4fbe-114">項目</span><span class="sxs-lookup"><span data-stu-id="a4fbe-114">Element</span></span>|<span data-ttu-id="a4fbe-115">描述</span><span class="sxs-lookup"><span data-stu-id="a4fbe-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4fbe-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="a4fbe-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="a4fbe-117">取得或設定<xref:System.TimeSpan> , 這個值會決定通道在中斷連接之前, 可以處於初始化狀態的最長時間。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="a4fbe-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="a4fbe-118">ConnectionBufferSize</span></span>|<span data-ttu-id="a4fbe-119">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="a4fbe-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a4fbe-120">hostNameComparisonMode</span></span>|<span data-ttu-id="a4fbe-121">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="a4fbe-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="a4fbe-122">manualAddressing</span></span>|<span data-ttu-id="a4fbe-123">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="a4fbe-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a4fbe-124">maxBufferPoolSize</span></span>|<span data-ttu-id="a4fbe-125">取得或設定傳輸所使用之任何緩衝集區的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="a4fbe-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a4fbe-126">maxBufferSize</span></span>|<span data-ttu-id="a4fbe-127">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="a4fbe-128">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="a4fbe-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="a4fbe-129">maxOutputDelay</span></span>|<span data-ttu-id="a4fbe-130">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="a4fbe-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="a4fbe-131">maxPendingAccepts</span></span>|<span data-ttu-id="a4fbe-132">取得或設定服務可等待接聽程式來處理服務之連入連線的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="a4fbe-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a4fbe-133">maxPendingConnections</span></span>|<span data-ttu-id="a4fbe-134">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a4fbe-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a4fbe-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="a4fbe-136">取得並設定可接收的訊息大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="a4fbe-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="a4fbe-137">transferMode</span></span>|<span data-ttu-id="a4fbe-138">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="a4fbe-139">\<namedPipeTransport > 的\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="a4fbe-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="a4fbe-140">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4fbe-141">父項目</span><span class="sxs-lookup"><span data-stu-id="a4fbe-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a4fbe-142">項目</span><span class="sxs-lookup"><span data-stu-id="a4fbe-142">Element</span></span>|<span data-ttu-id="a4fbe-143">描述</span><span class="sxs-lookup"><span data-stu-id="a4fbe-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4fbe-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="a4fbe-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a4fbe-145">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4fbe-146">備註</span><span class="sxs-lookup"><span data-stu-id="a4fbe-146">Remarks</span></span>  
<span data-ttu-id="a4fbe-147">這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="a4fbe-148">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="a4fbe-149">`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="a4fbe-150">這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。</span><span class="sxs-lookup"><span data-stu-id="a4fbe-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fbe-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4fbe-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a4fbe-152">傳輸</span><span class="sxs-lookup"><span data-stu-id="a4fbe-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a4fbe-153">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="a4fbe-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a4fbe-154">繫結</span><span class="sxs-lookup"><span data-stu-id="a4fbe-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a4fbe-155">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a4fbe-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a4fbe-156">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a4fbe-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a4fbe-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a4fbe-157">\<customBinding></span></span>](custombinding.md)
