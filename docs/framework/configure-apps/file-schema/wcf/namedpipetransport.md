---
title: '&lt;namedPipeTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7802bff708cb081aa9f54f76a35ff5842ad60544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="21460-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="21460-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="21460-103">定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="21460-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="21460-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="21460-104">\<system.serviceModel></span></span>  
<span data-ttu-id="21460-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="21460-105">\<bindings></span></span>  
<span data-ttu-id="21460-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="21460-106">\<customBinding></span></span>  
<span data-ttu-id="21460-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="21460-107">\<binding></span></span>  
<span data-ttu-id="21460-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="21460-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21460-109">語法</span><span class="sxs-lookup"><span data-stu-id="21460-109">Syntax</span></span>  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21460-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="21460-110">Attributes and Elements</span></span>  
<span data-ttu-id="21460-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="21460-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21460-112">屬性</span><span class="sxs-lookup"><span data-stu-id="21460-112">Attributes</span></span>  
<span data-ttu-id="21460-113">無。</span><span class="sxs-lookup"><span data-stu-id="21460-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21460-114">子元素</span><span class="sxs-lookup"><span data-stu-id="21460-114">Child Elements</span></span>  
  
|<span data-ttu-id="21460-115">項目</span><span class="sxs-lookup"><span data-stu-id="21460-115">Element</span></span>|<span data-ttu-id="21460-116">描述</span><span class="sxs-lookup"><span data-stu-id="21460-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21460-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="21460-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="21460-118">取得或設定<xref:System.TimeSpan>，決定通道正在中斷連接之前，可以處於初始化狀態中的最大時間。</span><span class="sxs-lookup"><span data-stu-id="21460-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="21460-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="21460-119">ConnectionBufferSize</span></span>|<span data-ttu-id="21460-120">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="21460-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="21460-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="21460-121">hostNameComparisonMode</span></span>|<span data-ttu-id="21460-122">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="21460-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="21460-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="21460-123">manualAddressing</span></span>|<span data-ttu-id="21460-124">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="21460-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="21460-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="21460-125">maxBufferPoolSize</span></span>|<span data-ttu-id="21460-126">取得或設定大小上限，以位元組為單位的傳輸所使用的任何緩衝區集區。</span><span class="sxs-lookup"><span data-stu-id="21460-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="21460-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="21460-127">maxBufferSize</span></span>|<span data-ttu-id="21460-128">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="21460-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="21460-129">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="21460-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="21460-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="21460-130">maxOutputDelay</span></span>|<span data-ttu-id="21460-131">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="21460-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="21460-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="21460-132">maxPendingAccepts</span></span>|<span data-ttu-id="21460-133">取得或設定的服務可以有在接聽程式上等待處理服務傳入連線的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="21460-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="21460-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="21460-134">maxPendingConnections</span></span>|<span data-ttu-id="21460-135">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="21460-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="21460-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="21460-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="21460-137">取得及設定可允許訊息大小上限，以位元組為單位，可接收。</span><span class="sxs-lookup"><span data-stu-id="21460-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="21460-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="21460-138">transferMode</span></span>|<span data-ttu-id="21460-139">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="21460-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="21460-140">\<n > 的\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="21460-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="21460-141">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="21460-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21460-142">父項目</span><span class="sxs-lookup"><span data-stu-id="21460-142">Parent Elements</span></span>  
  
|<span data-ttu-id="21460-143">項目</span><span class="sxs-lookup"><span data-stu-id="21460-143">Element</span></span>|<span data-ttu-id="21460-144">描述</span><span class="sxs-lookup"><span data-stu-id="21460-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21460-145">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="21460-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="21460-146">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="21460-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21460-147">備註</span><span class="sxs-lookup"><span data-stu-id="21460-147">Remarks</span></span>  
<span data-ttu-id="21460-148">這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。</span><span class="sxs-lookup"><span data-stu-id="21460-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="21460-149">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="21460-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="21460-150">`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="21460-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="21460-151">這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。</span><span class="sxs-lookup"><span data-stu-id="21460-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21460-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="21460-152">See Also</span></span>  
<span data-ttu-id="21460-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span><span class="sxs-lookup"><span data-stu-id="21460-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span></span>   
<span data-ttu-id="21460-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="21460-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span></span>   
<span data-ttu-id="21460-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="21460-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span></span>   
<span data-ttu-id="21460-156"><xref:System.ServiceModel.Channels.CustomBinding></span><span class="sxs-lookup"><span data-stu-id="21460-156"><xref:System.ServiceModel.Channels.CustomBinding></span></span>   
<span data-ttu-id="21460-157">[傳輸](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="21460-157">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="21460-158">[選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="21460-158">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="21460-159">[繫結](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="21460-159">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="21460-160">[擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="21460-160">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="21460-161">[自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="21460-161">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="21460-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="21460-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
