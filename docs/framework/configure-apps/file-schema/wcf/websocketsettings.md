---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226868"
---
# <a name="websocketsettings"></a><span data-ttu-id="4c1e6-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="4c1e6-101">\<webSocketSettings></span></span>
<span data-ttu-id="4c1e6-102">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="4c1e6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4c1e6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4c1e6-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4c1e6-104">\<bindings></span></span>  
<span data-ttu-id="4c1e6-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4c1e6-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c1e6-106">語法</span><span class="sxs-lookup"><span data-stu-id="4c1e6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c1e6-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4c1e6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4c1e6-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c1e6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4c1e6-109">Attributes</span></span>  
  
|<span data-ttu-id="4c1e6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4c1e6-110">Attribute</span></span>|<span data-ttu-id="4c1e6-111">描述</span><span class="sxs-lookup"><span data-stu-id="4c1e6-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c1e6-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="4c1e6-112">createNotificationOnConnection</span></span>|<span data-ttu-id="4c1e6-113">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="4c1e6-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="4c1e6-114">disablePayloadMasking</span></span>|<span data-ttu-id="4c1e6-115">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="4c1e6-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="4c1e6-116">keepAliveInterval</span></span>|<span data-ttu-id="4c1e6-117">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="4c1e6-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4c1e6-118">maxPendingConnections</span></span>|<span data-ttu-id="4c1e6-119">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="4c1e6-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="4c1e6-120">receiveBufferSize</span></span>|<span data-ttu-id="4c1e6-121">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="4c1e6-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="4c1e6-122">sendBufferSize</span></span>|<span data-ttu-id="4c1e6-123">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="4c1e6-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="4c1e6-124">subProtocol</span></span>|<span data-ttu-id="4c1e6-125">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="4c1e6-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="4c1e6-126">transportUsage</span></span>|<span data-ttu-id="4c1e6-127">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="4c1e6-128">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="4c1e6-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="4c1e6-129">值</span><span class="sxs-lookup"><span data-stu-id="4c1e6-129">Value</span></span>|<span data-ttu-id="4c1e6-130">描述</span><span class="sxs-lookup"><span data-stu-id="4c1e6-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c1e6-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="4c1e6-131">WhenDuplex</span></span>|<span data-ttu-id="4c1e6-132">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="4c1e6-133">永遠</span><span class="sxs-lookup"><span data-stu-id="4c1e6-133">Always</span></span>|<span data-ttu-id="4c1e6-134">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="4c1e6-135">永不</span><span class="sxs-lookup"><span data-stu-id="4c1e6-135">Never</span></span>|<span data-ttu-id="4c1e6-136">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c1e6-137">子元素</span><span class="sxs-lookup"><span data-stu-id="4c1e6-137">Child Elements</span></span>  
 <span data-ttu-id="4c1e6-138">None</span><span class="sxs-lookup"><span data-stu-id="4c1e6-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c1e6-139">父項目</span><span class="sxs-lookup"><span data-stu-id="4c1e6-139">Parent Elements</span></span>  
  
|<span data-ttu-id="4c1e6-140">項目</span><span class="sxs-lookup"><span data-stu-id="4c1e6-140">Element</span></span>|<span data-ttu-id="4c1e6-141">描述</span><span class="sxs-lookup"><span data-stu-id="4c1e6-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c1e6-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4c1e6-142">\<netHttpBinding></span></span>|<span data-ttu-id="4c1e6-143">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4c1e6-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4c1e6-144">範例</span><span class="sxs-lookup"><span data-stu-id="4c1e6-144">Example</span></span>  
 <span data-ttu-id="4c1e6-145">下列範例示範如何使用\<webSocketSettings > 項目。</span><span class="sxs-lookup"><span data-stu-id="4c1e6-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c1e6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c1e6-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="4c1e6-147">繫結</span><span class="sxs-lookup"><span data-stu-id="4c1e6-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4c1e6-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="4c1e6-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4c1e6-149">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="4c1e6-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4c1e6-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="4c1e6-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
