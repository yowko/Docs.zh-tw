---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226868"
---
# <a name="websocketsettings"></a><span data-ttu-id="a8764-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="a8764-101">\<webSocketSettings></span></span>
<span data-ttu-id="a8764-102">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="a8764-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="a8764-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a8764-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8764-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a8764-104">\<bindings></span></span>  
<span data-ttu-id="a8764-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8764-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8764-106">語法</span><span class="sxs-lookup"><span data-stu-id="a8764-106">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8764-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8764-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a8764-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a8764-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8764-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a8764-109">Attributes</span></span>  
  
|<span data-ttu-id="a8764-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a8764-110">Attribute</span></span>|<span data-ttu-id="a8764-111">描述</span><span class="sxs-lookup"><span data-stu-id="a8764-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8764-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="a8764-112">createNotificationOnConnection</span></span>|<span data-ttu-id="a8764-113">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="a8764-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="a8764-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="a8764-114">disablePayloadMasking</span></span>|<span data-ttu-id="a8764-115">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="a8764-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="a8764-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="a8764-116">keepAliveInterval</span></span>|<span data-ttu-id="a8764-117">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="a8764-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="a8764-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a8764-118">maxPendingConnections</span></span>|<span data-ttu-id="a8764-119">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="a8764-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a8764-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="a8764-120">receiveBufferSize</span></span>|<span data-ttu-id="a8764-121">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="a8764-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="a8764-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="a8764-122">sendBufferSize</span></span>|<span data-ttu-id="a8764-123">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="a8764-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="a8764-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="a8764-124">subProtocol</span></span>|<span data-ttu-id="a8764-125">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a8764-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="a8764-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="a8764-126">transportUsage</span></span>|<span data-ttu-id="a8764-127">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="a8764-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="a8764-128">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="a8764-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="a8764-129">值</span><span class="sxs-lookup"><span data-stu-id="a8764-129">Value</span></span>|<span data-ttu-id="a8764-130">描述</span><span class="sxs-lookup"><span data-stu-id="a8764-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8764-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="a8764-131">WhenDuplex</span></span>|<span data-ttu-id="a8764-132">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a8764-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="a8764-133">永遠</span><span class="sxs-lookup"><span data-stu-id="a8764-133">Always</span></span>|<span data-ttu-id="a8764-134">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a8764-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="a8764-135">永不</span><span class="sxs-lookup"><span data-stu-id="a8764-135">Never</span></span>|<span data-ttu-id="a8764-136">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a8764-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8764-137">子元素</span><span class="sxs-lookup"><span data-stu-id="a8764-137">Child Elements</span></span>  
 <span data-ttu-id="a8764-138">None</span><span class="sxs-lookup"><span data-stu-id="a8764-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8764-139">父項目</span><span class="sxs-lookup"><span data-stu-id="a8764-139">Parent Elements</span></span>  
  
|<span data-ttu-id="a8764-140">項目</span><span class="sxs-lookup"><span data-stu-id="a8764-140">Element</span></span>|<span data-ttu-id="a8764-141">描述</span><span class="sxs-lookup"><span data-stu-id="a8764-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8764-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8764-142">\<netHttpBinding></span></span>|<span data-ttu-id="a8764-143">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a8764-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a8764-144">範例</span><span class="sxs-lookup"><span data-stu-id="a8764-144">Example</span></span>  
 <span data-ttu-id="a8764-145">下列範例示範如何使用\<webSocketSettings > 項目。</span><span class="sxs-lookup"><span data-stu-id="a8764-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="a8764-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8764-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="a8764-147">繫結</span><span class="sxs-lookup"><span data-stu-id="a8764-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a8764-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a8764-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a8764-149">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a8764-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a8764-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="a8764-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
