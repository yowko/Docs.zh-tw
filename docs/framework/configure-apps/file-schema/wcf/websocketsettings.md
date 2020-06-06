---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732563"
---
# \<webSocketSettings>
<span data-ttu-id="e0dc7-101">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="e0dc7-102">語法</span><span class="sxs-lookup"><span data-stu-id="e0dc7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0dc7-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e0dc7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e0dc7-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0dc7-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e0dc7-105">Attributes</span></span>  
  
|<span data-ttu-id="e0dc7-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e0dc7-106">Attribute</span></span>|<span data-ttu-id="e0dc7-107">描述</span><span class="sxs-lookup"><span data-stu-id="e0dc7-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0dc7-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="e0dc7-108">createNotificationOnConnection</span></span>|<span data-ttu-id="e0dc7-109">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="e0dc7-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="e0dc7-110">disablePayloadMasking</span></span>|<span data-ttu-id="e0dc7-111">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="e0dc7-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="e0dc7-112">keepAliveInterval</span></span>|<span data-ttu-id="e0dc7-113">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="e0dc7-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e0dc7-114">maxPendingConnections</span></span>|<span data-ttu-id="e0dc7-115">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="e0dc7-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="e0dc7-116">receiveBufferSize</span></span>|<span data-ttu-id="e0dc7-117">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="e0dc7-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="e0dc7-118">sendBufferSize</span></span>|<span data-ttu-id="e0dc7-119">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="e0dc7-120">subProtocol</span><span class="sxs-lookup"><span data-stu-id="e0dc7-120">subProtocol</span></span>|<span data-ttu-id="e0dc7-121">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="e0dc7-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="e0dc7-122">transportUsage</span></span>|<span data-ttu-id="e0dc7-123">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="e0dc7-124">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="e0dc7-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="e0dc7-125">值</span><span class="sxs-lookup"><span data-stu-id="e0dc7-125">Value</span></span>|<span data-ttu-id="e0dc7-126">描述</span><span class="sxs-lookup"><span data-stu-id="e0dc7-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e0dc7-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="e0dc7-127">WhenDuplex</span></span>|<span data-ttu-id="e0dc7-128">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="e0dc7-129">一律</span><span class="sxs-lookup"><span data-stu-id="e0dc7-129">Always</span></span>|<span data-ttu-id="e0dc7-130">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="e0dc7-131">永不</span><span class="sxs-lookup"><span data-stu-id="e0dc7-131">Never</span></span>|<span data-ttu-id="e0dc7-132">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0dc7-133">子元素</span><span class="sxs-lookup"><span data-stu-id="e0dc7-133">Child Elements</span></span>  
 <span data-ttu-id="e0dc7-134">無</span><span class="sxs-lookup"><span data-stu-id="e0dc7-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0dc7-135">父項目</span><span class="sxs-lookup"><span data-stu-id="e0dc7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="e0dc7-136">元素</span><span class="sxs-lookup"><span data-stu-id="e0dc7-136">Element</span></span>|<span data-ttu-id="e0dc7-137">描述</span><span class="sxs-lookup"><span data-stu-id="e0dc7-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="e0dc7-138">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e0dc7-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e0dc7-139">範例</span><span class="sxs-lookup"><span data-stu-id="e0dc7-139">Example</span></span>  
 <span data-ttu-id="e0dc7-140">下列範例示範如何使用 \<webSocketSettings> 元素。</span><span class="sxs-lookup"><span data-stu-id="e0dc7-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0dc7-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0dc7-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="e0dc7-142">繫結</span><span class="sxs-lookup"><span data-stu-id="e0dc7-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e0dc7-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e0dc7-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e0dc7-144">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="e0dc7-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
