---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: fd7dc38e229b6135f91fc159596ed1669d43701a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228233"
---
# <a name="namedpipetransport"></a><span data-ttu-id="ff71c-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="ff71c-101">\<namedPipeTransport></span></span>
<span data-ttu-id="ff71c-102">定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="ff71c-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="ff71c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ff71c-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ff71c-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ff71c-104">\<bindings></span></span>  
<span data-ttu-id="ff71c-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ff71c-105">\<customBinding></span></span>  
<span data-ttu-id="ff71c-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="ff71c-106">\<binding></span></span>  
<span data-ttu-id="ff71c-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="ff71c-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff71c-108">語法</span><span class="sxs-lookup"><span data-stu-id="ff71c-108">Syntax</span></span>  
  
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
                          maxOutboundConnectionsPerEndpopint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff71c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff71c-109">Attributes and Elements</span></span>  
<span data-ttu-id="ff71c-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ff71c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff71c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ff71c-111">Attributes</span></span>  
<span data-ttu-id="ff71c-112">無。</span><span class="sxs-lookup"><span data-stu-id="ff71c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff71c-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ff71c-113">Child Elements</span></span>  
  
|<span data-ttu-id="ff71c-114">項目</span><span class="sxs-lookup"><span data-stu-id="ff71c-114">Element</span></span>|<span data-ttu-id="ff71c-115">描述</span><span class="sxs-lookup"><span data-stu-id="ff71c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff71c-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="ff71c-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="ff71c-117">取得或設定<xref:System.TimeSpan>，決定通道在中斷連接之前時，可以初始化狀態中的最大時間。</span><span class="sxs-lookup"><span data-stu-id="ff71c-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="ff71c-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="ff71c-118">ConnectionBufferSize</span></span>|<span data-ttu-id="ff71c-119">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="ff71c-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="ff71c-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="ff71c-120">hostNameComparisonMode</span></span>|<span data-ttu-id="ff71c-121">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="ff71c-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="ff71c-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="ff71c-122">manualAddressing</span></span>|<span data-ttu-id="ff71c-123">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="ff71c-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="ff71c-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="ff71c-124">maxBufferPoolSize</span></span>|<span data-ttu-id="ff71c-125">取得或設定最大的大小，以位元組為單位的傳輸所使用的任何緩衝區集區。</span><span class="sxs-lookup"><span data-stu-id="ff71c-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="ff71c-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="ff71c-126">maxBufferSize</span></span>|<span data-ttu-id="ff71c-127">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ff71c-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="ff71c-128">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="ff71c-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="ff71c-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="ff71c-129">maxOutputDelay</span></span>|<span data-ttu-id="ff71c-130">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ff71c-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="ff71c-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="ff71c-131">maxPendingAccepts</span></span>|<span data-ttu-id="ff71c-132">取得或設定的服務可以有在接聽程式上等待處理服務傳入連線的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="ff71c-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="ff71c-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="ff71c-133">maxPendingConnections</span></span>|<span data-ttu-id="ff71c-134">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="ff71c-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="ff71c-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="ff71c-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="ff71c-136">取得及設定可允許訊息大小上限，以位元組為單位，可接收。</span><span class="sxs-lookup"><span data-stu-id="ff71c-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="ff71c-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="ff71c-137">transferMode</span></span>|<span data-ttu-id="ff71c-138">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="ff71c-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="ff71c-139">\<connectionPoolSettings> of \<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="ff71c-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="ff71c-140">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="ff71c-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff71c-141">父項目</span><span class="sxs-lookup"><span data-stu-id="ff71c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ff71c-142">項目</span><span class="sxs-lookup"><span data-stu-id="ff71c-142">Element</span></span>|<span data-ttu-id="ff71c-143">描述</span><span class="sxs-lookup"><span data-stu-id="ff71c-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff71c-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="ff71c-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ff71c-145">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="ff71c-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff71c-146">備註</span><span class="sxs-lookup"><span data-stu-id="ff71c-146">Remarks</span></span>  
<span data-ttu-id="ff71c-147">這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。</span><span class="sxs-lookup"><span data-stu-id="ff71c-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="ff71c-148">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="ff71c-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="ff71c-149">`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ff71c-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="ff71c-150">這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。</span><span class="sxs-lookup"><span data-stu-id="ff71c-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff71c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff71c-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ff71c-152">傳輸</span><span class="sxs-lookup"><span data-stu-id="ff71c-152">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="ff71c-153">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="ff71c-153">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ff71c-154">繫結</span><span class="sxs-lookup"><span data-stu-id="ff71c-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ff71c-155">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="ff71c-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ff71c-156">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="ff71c-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ff71c-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ff71c-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
