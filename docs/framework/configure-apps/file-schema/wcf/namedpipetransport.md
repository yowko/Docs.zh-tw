---
title: '&lt;Connectionpoolsettings&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: bf9229411143345847247f36de07b5c014d3f259
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149596"
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="a8081-102">&lt;Connectionpoolsettings&gt;</span><span class="sxs-lookup"><span data-stu-id="a8081-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="a8081-103">定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="a8081-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="a8081-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a8081-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a8081-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a8081-105">\<bindings></span></span>  
<span data-ttu-id="a8081-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a8081-106">\<customBinding></span></span>  
<span data-ttu-id="a8081-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a8081-107">\<binding></span></span>  
<span data-ttu-id="a8081-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="a8081-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8081-109">語法</span><span class="sxs-lookup"><span data-stu-id="a8081-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8081-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8081-110">Attributes and Elements</span></span>  
<span data-ttu-id="a8081-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a8081-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8081-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a8081-112">Attributes</span></span>  
<span data-ttu-id="a8081-113">無。</span><span class="sxs-lookup"><span data-stu-id="a8081-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8081-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a8081-114">Child Elements</span></span>  
  
|<span data-ttu-id="a8081-115">項目</span><span class="sxs-lookup"><span data-stu-id="a8081-115">Element</span></span>|<span data-ttu-id="a8081-116">描述</span><span class="sxs-lookup"><span data-stu-id="a8081-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8081-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="a8081-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="a8081-118">取得或設定<xref:System.TimeSpan>，決定通道在中斷連接之前時，可以初始化狀態中的最大時間。</span><span class="sxs-lookup"><span data-stu-id="a8081-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="a8081-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="a8081-119">ConnectionBufferSize</span></span>|<span data-ttu-id="a8081-120">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="a8081-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="a8081-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a8081-121">hostNameComparisonMode</span></span>|<span data-ttu-id="a8081-122">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="a8081-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="a8081-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="a8081-123">manualAddressing</span></span>|<span data-ttu-id="a8081-124">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="a8081-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="a8081-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a8081-125">maxBufferPoolSize</span></span>|<span data-ttu-id="a8081-126">取得或設定最大的大小，以位元組為單位的傳輸所使用的任何緩衝區集區。</span><span class="sxs-lookup"><span data-stu-id="a8081-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="a8081-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a8081-127">maxBufferSize</span></span>|<span data-ttu-id="a8081-128">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="a8081-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="a8081-129">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="a8081-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="a8081-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="a8081-130">maxOutputDelay</span></span>|<span data-ttu-id="a8081-131">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a8081-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="a8081-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="a8081-132">maxPendingAccepts</span></span>|<span data-ttu-id="a8081-133">取得或設定的服務可以有在接聽程式上等待處理服務傳入連線的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="a8081-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="a8081-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a8081-134">maxPendingConnections</span></span>|<span data-ttu-id="a8081-135">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="a8081-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a8081-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a8081-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="a8081-137">取得及設定可允許訊息大小上限，以位元組為單位，可接收。</span><span class="sxs-lookup"><span data-stu-id="a8081-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="a8081-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="a8081-138">transferMode</span></span>|<span data-ttu-id="a8081-139">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="a8081-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="a8081-140">\<n > 的\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="a8081-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="a8081-141">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="a8081-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8081-142">父項目</span><span class="sxs-lookup"><span data-stu-id="a8081-142">Parent Elements</span></span>  
  
|<span data-ttu-id="a8081-143">項目</span><span class="sxs-lookup"><span data-stu-id="a8081-143">Element</span></span>|<span data-ttu-id="a8081-144">描述</span><span class="sxs-lookup"><span data-stu-id="a8081-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8081-145">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a8081-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a8081-146">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="a8081-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8081-147">備註</span><span class="sxs-lookup"><span data-stu-id="a8081-147">Remarks</span></span>  
<span data-ttu-id="a8081-148">這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。</span><span class="sxs-lookup"><span data-stu-id="a8081-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="a8081-149">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a8081-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="a8081-150">`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a8081-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="a8081-151">這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。</span><span class="sxs-lookup"><span data-stu-id="a8081-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8081-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8081-152">See Also</span></span>  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
<span data-ttu-id="a8081-153">[傳輸](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="a8081-153">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="a8081-154">[選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="a8081-154">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="a8081-155">[繫結](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="a8081-155">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="a8081-156">[擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="a8081-156">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="a8081-157">[自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="a8081-157">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="a8081-158">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a8081-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
