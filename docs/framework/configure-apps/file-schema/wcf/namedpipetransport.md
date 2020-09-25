---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 4582066098feaf50b33b083de56bcb8c3e04df0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204615"
---
# \<namedPipeTransport>

<span data-ttu-id="09234-101">定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="09234-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="09234-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="09234-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09234-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="09234-103">Attributes and Elements</span></span>  

<span data-ttu-id="09234-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="09234-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09234-105">屬性</span><span class="sxs-lookup"><span data-stu-id="09234-105">Attributes</span></span>  

<span data-ttu-id="09234-106">無。</span><span class="sxs-lookup"><span data-stu-id="09234-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="09234-107">子元素</span><span class="sxs-lookup"><span data-stu-id="09234-107">Child Elements</span></span>  
  
|<span data-ttu-id="09234-108">項目</span><span class="sxs-lookup"><span data-stu-id="09234-108">Element</span></span>|<span data-ttu-id="09234-109">描述</span><span class="sxs-lookup"><span data-stu-id="09234-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09234-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="09234-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="09234-111">取得或設定 <xref:System.TimeSpan>，決定通道在中斷連接之前，可以處於初始化狀態中的最長時間。</span><span class="sxs-lookup"><span data-stu-id="09234-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="09234-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="09234-112">ConnectionBufferSize</span></span>|<span data-ttu-id="09234-113">取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="09234-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="09234-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="09234-114">hostNameComparisonMode</span></span>|<span data-ttu-id="09234-115">取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="09234-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="09234-116">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="09234-116">manualAddressing</span></span>|<span data-ttu-id="09234-117">取得或設定值，這個值會指出是否需要訊息的手動定址。</span><span class="sxs-lookup"><span data-stu-id="09234-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="09234-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="09234-118">maxBufferPoolSize</span></span>|<span data-ttu-id="09234-119">取得或設定傳輸所使用之任何緩衝區集區的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="09234-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="09234-120">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="09234-120">maxBufferSize</span></span>|<span data-ttu-id="09234-121">取得或設定要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="09234-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="09234-122">對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。</span><span class="sxs-lookup"><span data-stu-id="09234-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="09234-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="09234-123">maxOutputDelay</span></span>|<span data-ttu-id="09234-124">取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="09234-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="09234-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="09234-125">maxPendingAccepts</span></span>|<span data-ttu-id="09234-126">取得或設定服務可使其等待接聽程式以處理服務之連入連線的通道最大數目。</span><span class="sxs-lookup"><span data-stu-id="09234-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="09234-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="09234-127">maxPendingConnections</span></span>|<span data-ttu-id="09234-128">取得或設定服務上等待分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="09234-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="09234-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="09234-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="09234-130">取得和設定可接收的最大允許訊息大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="09234-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="09234-131">transferMode</span><span class="sxs-lookup"><span data-stu-id="09234-131">transferMode</span></span>|<span data-ttu-id="09234-132">取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="09234-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="09234-133">\<connectionPoolSettings> 次數 \<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="09234-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="09234-134">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="09234-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09234-135">父項目</span><span class="sxs-lookup"><span data-stu-id="09234-135">Parent Elements</span></span>  
  
|<span data-ttu-id="09234-136">項目</span><span class="sxs-lookup"><span data-stu-id="09234-136">Element</span></span>|<span data-ttu-id="09234-137">描述</span><span class="sxs-lookup"><span data-stu-id="09234-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="09234-138">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="09234-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09234-139">備註</span><span class="sxs-lookup"><span data-stu-id="09234-139">Remarks</span></span>  

<span data-ttu-id="09234-140">這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。</span><span class="sxs-lookup"><span data-stu-id="09234-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="09234-141">其他 URI 元件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="09234-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="09234-142">`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="09234-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="09234-143">這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。</span><span class="sxs-lookup"><span data-stu-id="09234-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09234-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09234-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="09234-145">傳輸</span><span class="sxs-lookup"><span data-stu-id="09234-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="09234-146">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="09234-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="09234-147">繫結</span><span class="sxs-lookup"><span data-stu-id="09234-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="09234-148">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="09234-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="09234-149">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="09234-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
