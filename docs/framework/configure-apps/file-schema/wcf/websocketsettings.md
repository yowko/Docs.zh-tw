---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732563"
---
# <a name="websocketsettings"></a><span data-ttu-id="81723-101">\<W s ></span><span class="sxs-lookup"><span data-stu-id="81723-101">\<webSocketSettings></span></span>
<span data-ttu-id="81723-102">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="81723-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="81723-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81723-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81723-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="81723-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="81723-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="81723-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="81723-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81723-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="81723-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="81723-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="81723-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<w s >**</span><span class="sxs-lookup"><span data-stu-id="81723-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81723-109">語法</span><span class="sxs-lookup"><span data-stu-id="81723-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81723-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81723-110">Attributes and Elements</span></span>  
 <span data-ttu-id="81723-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="81723-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81723-112">屬性</span><span class="sxs-lookup"><span data-stu-id="81723-112">Attributes</span></span>  
  
|<span data-ttu-id="81723-113">屬性</span><span class="sxs-lookup"><span data-stu-id="81723-113">Attribute</span></span>|<span data-ttu-id="81723-114">描述</span><span class="sxs-lookup"><span data-stu-id="81723-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81723-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="81723-115">createNotificationOnConnection</span></span>|<span data-ttu-id="81723-116">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="81723-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="81723-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="81723-117">disablePayloadMasking</span></span>|<span data-ttu-id="81723-118">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="81723-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="81723-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="81723-119">keepAliveInterval</span></span>|<span data-ttu-id="81723-120">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="81723-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="81723-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="81723-121">maxPendingConnections</span></span>|<span data-ttu-id="81723-122">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="81723-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="81723-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="81723-123">receiveBufferSize</span></span>|<span data-ttu-id="81723-124">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="81723-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="81723-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="81723-125">sendBufferSize</span></span>|<span data-ttu-id="81723-126">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="81723-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="81723-127">subProtocol</span><span class="sxs-lookup"><span data-stu-id="81723-127">subProtocol</span></span>|<span data-ttu-id="81723-128">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="81723-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="81723-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="81723-129">transportUsage</span></span>|<span data-ttu-id="81723-130">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="81723-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="81723-131">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="81723-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="81723-132">值</span><span class="sxs-lookup"><span data-stu-id="81723-132">Value</span></span>|<span data-ttu-id="81723-133">描述</span><span class="sxs-lookup"><span data-stu-id="81723-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81723-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="81723-134">WhenDuplex</span></span>|<span data-ttu-id="81723-135">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="81723-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="81723-136">永遠</span><span class="sxs-lookup"><span data-stu-id="81723-136">Always</span></span>|<span data-ttu-id="81723-137">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="81723-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="81723-138">永不</span><span class="sxs-lookup"><span data-stu-id="81723-138">Never</span></span>|<span data-ttu-id="81723-139">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="81723-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81723-140">子項目</span><span class="sxs-lookup"><span data-stu-id="81723-140">Child Elements</span></span>  
 <span data-ttu-id="81723-141">None</span><span class="sxs-lookup"><span data-stu-id="81723-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81723-142">父項目</span><span class="sxs-lookup"><span data-stu-id="81723-142">Parent Elements</span></span>  
  
|<span data-ttu-id="81723-143">項目</span><span class="sxs-lookup"><span data-stu-id="81723-143">Element</span></span>|<span data-ttu-id="81723-144">描述</span><span class="sxs-lookup"><span data-stu-id="81723-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81723-145">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="81723-145">\<netHttpBinding></span></span>|<span data-ttu-id="81723-146">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="81723-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="81723-147">範例</span><span class="sxs-lookup"><span data-stu-id="81723-147">Example</span></span>  
 <span data-ttu-id="81723-148">下列範例示範如何使用 \<W s > 元素。</span><span class="sxs-lookup"><span data-stu-id="81723-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81723-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="81723-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="81723-150">繫結</span><span class="sxs-lookup"><span data-stu-id="81723-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81723-151">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="81723-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81723-152">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="81723-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="81723-153">\<binding ></span><span class="sxs-lookup"><span data-stu-id="81723-153">\<binding></span></span>](bindings.md)
