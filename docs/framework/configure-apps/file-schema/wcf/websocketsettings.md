---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 298bf27b171772bb039b11b5e5de70e7d45b061d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258435"
---
# <a name="websocketsettings"></a><span data-ttu-id="e18d5-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="e18d5-101">\<webSocketSettings></span></span>
<span data-ttu-id="e18d5-102">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="e18d5-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="e18d5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e18d5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e18d5-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e18d5-104">\<bindings></span></span>  
<span data-ttu-id="e18d5-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e18d5-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e18d5-106">語法</span><span class="sxs-lookup"><span data-stu-id="e18d5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e18d5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e18d5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e18d5-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e18d5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e18d5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e18d5-109">Attributes</span></span>  
  
|<span data-ttu-id="e18d5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e18d5-110">Attribute</span></span>|<span data-ttu-id="e18d5-111">描述</span><span class="sxs-lookup"><span data-stu-id="e18d5-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e18d5-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="e18d5-112">createNotificationOnConnection</span></span>|<span data-ttu-id="e18d5-113">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="e18d5-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="e18d5-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="e18d5-114">disablePayloadMasking</span></span>|<span data-ttu-id="e18d5-115">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="e18d5-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="e18d5-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="e18d5-116">keepAliveInterval</span></span>|<span data-ttu-id="e18d5-117">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="e18d5-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="e18d5-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e18d5-118">maxPendingConnections</span></span>|<span data-ttu-id="e18d5-119">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="e18d5-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="e18d5-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="e18d5-120">receiveBufferSize</span></span>|<span data-ttu-id="e18d5-121">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e18d5-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="e18d5-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="e18d5-122">sendBufferSize</span></span>|<span data-ttu-id="e18d5-123">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e18d5-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="e18d5-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="e18d5-124">subProtocol</span></span>|<span data-ttu-id="e18d5-125">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e18d5-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="e18d5-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="e18d5-126">transportUsage</span></span>|<span data-ttu-id="e18d5-127">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="e18d5-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="e18d5-128">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="e18d5-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="e18d5-129">值</span><span class="sxs-lookup"><span data-stu-id="e18d5-129">Value</span></span>|<span data-ttu-id="e18d5-130">描述</span><span class="sxs-lookup"><span data-stu-id="e18d5-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e18d5-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="e18d5-131">WhenDuplex</span></span>|<span data-ttu-id="e18d5-132">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e18d5-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="e18d5-133">永遠</span><span class="sxs-lookup"><span data-stu-id="e18d5-133">Always</span></span>|<span data-ttu-id="e18d5-134">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e18d5-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="e18d5-135">永不</span><span class="sxs-lookup"><span data-stu-id="e18d5-135">Never</span></span>|<span data-ttu-id="e18d5-136">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e18d5-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e18d5-137">子元素</span><span class="sxs-lookup"><span data-stu-id="e18d5-137">Child Elements</span></span>  
 <span data-ttu-id="e18d5-138">無</span><span class="sxs-lookup"><span data-stu-id="e18d5-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e18d5-139">父項目</span><span class="sxs-lookup"><span data-stu-id="e18d5-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e18d5-140">項目</span><span class="sxs-lookup"><span data-stu-id="e18d5-140">Element</span></span>|<span data-ttu-id="e18d5-141">描述</span><span class="sxs-lookup"><span data-stu-id="e18d5-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e18d5-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e18d5-142">\<netHttpBinding></span></span>|<span data-ttu-id="e18d5-143">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e18d5-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e18d5-144">範例</span><span class="sxs-lookup"><span data-stu-id="e18d5-144">Example</span></span>  
 <span data-ttu-id="e18d5-145">下列範例示範如何使用\<webSocketSettings > 項目。</span><span class="sxs-lookup"><span data-stu-id="e18d5-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e18d5-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e18d5-146">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="e18d5-147">繫結</span><span class="sxs-lookup"><span data-stu-id="e18d5-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e18d5-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e18d5-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e18d5-149">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="e18d5-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e18d5-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="e18d5-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
