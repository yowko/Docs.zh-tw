---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 6cfddfb9ebfc7c3447af977e14738baabebc8fe9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177845"
---
# \<webSocketSettings>

<span data-ttu-id="97ce3-101">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="97ce3-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="97ce3-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="97ce3-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97ce3-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="97ce3-103">Attributes and Elements</span></span>  

 <span data-ttu-id="97ce3-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="97ce3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97ce3-105">屬性</span><span class="sxs-lookup"><span data-stu-id="97ce3-105">Attributes</span></span>  
  
|<span data-ttu-id="97ce3-106">屬性</span><span class="sxs-lookup"><span data-stu-id="97ce3-106">Attribute</span></span>|<span data-ttu-id="97ce3-107">描述</span><span class="sxs-lookup"><span data-stu-id="97ce3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97ce3-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="97ce3-108">createNotificationOnConnection</span></span>|<span data-ttu-id="97ce3-109">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="97ce3-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="97ce3-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="97ce3-110">disablePayloadMasking</span></span>|<span data-ttu-id="97ce3-111">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="97ce3-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="97ce3-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="97ce3-112">keepAliveInterval</span></span>|<span data-ttu-id="97ce3-113">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="97ce3-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="97ce3-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="97ce3-114">maxPendingConnections</span></span>|<span data-ttu-id="97ce3-115">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="97ce3-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="97ce3-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="97ce3-116">receiveBufferSize</span></span>|<span data-ttu-id="97ce3-117">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="97ce3-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="97ce3-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="97ce3-118">sendBufferSize</span></span>|<span data-ttu-id="97ce3-119">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="97ce3-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="97ce3-120">subProtocol</span><span class="sxs-lookup"><span data-stu-id="97ce3-120">subProtocol</span></span>|<span data-ttu-id="97ce3-121">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97ce3-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="97ce3-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="97ce3-122">transportUsage</span></span>|<span data-ttu-id="97ce3-123">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="97ce3-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="97ce3-124">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="97ce3-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="97ce3-125">值</span><span class="sxs-lookup"><span data-stu-id="97ce3-125">Value</span></span>|<span data-ttu-id="97ce3-126">描述</span><span class="sxs-lookup"><span data-stu-id="97ce3-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97ce3-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="97ce3-127">WhenDuplex</span></span>|<span data-ttu-id="97ce3-128">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97ce3-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="97ce3-129">一律</span><span class="sxs-lookup"><span data-stu-id="97ce3-129">Always</span></span>|<span data-ttu-id="97ce3-130">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97ce3-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="97ce3-131">永不</span><span class="sxs-lookup"><span data-stu-id="97ce3-131">Never</span></span>|<span data-ttu-id="97ce3-132">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97ce3-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97ce3-133">子元素</span><span class="sxs-lookup"><span data-stu-id="97ce3-133">Child Elements</span></span>  

 <span data-ttu-id="97ce3-134">無</span><span class="sxs-lookup"><span data-stu-id="97ce3-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97ce3-135">父項目</span><span class="sxs-lookup"><span data-stu-id="97ce3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="97ce3-136">項目</span><span class="sxs-lookup"><span data-stu-id="97ce3-136">Element</span></span>|<span data-ttu-id="97ce3-137">描述</span><span class="sxs-lookup"><span data-stu-id="97ce3-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="97ce3-138">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="97ce3-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97ce3-139">範例</span><span class="sxs-lookup"><span data-stu-id="97ce3-139">Example</span></span>  

 <span data-ttu-id="97ce3-140">下列範例示範如何使用 \<webSocketSettings> 元素。</span><span class="sxs-lookup"><span data-stu-id="97ce3-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97ce3-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97ce3-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="97ce3-142">繫結</span><span class="sxs-lookup"><span data-stu-id="97ce3-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="97ce3-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="97ce3-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="97ce3-144">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="97ce3-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
