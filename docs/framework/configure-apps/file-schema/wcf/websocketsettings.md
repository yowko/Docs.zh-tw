---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: e5f34dca83c8d3d08d27fb72bee5af2a89ac6b9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511910"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="a97c0-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="a97c0-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="a97c0-103">用來指定 Web 通訊端設定的組態元素。</span><span class="sxs-lookup"><span data-stu-id="a97c0-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="a97c0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a97c0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a97c0-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a97c0-105">\<bindings></span></span>  
<span data-ttu-id="a97c0-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a97c0-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a97c0-107">語法</span><span class="sxs-lookup"><span data-stu-id="a97c0-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a97c0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a97c0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a97c0-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a97c0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a97c0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a97c0-110">Attributes</span></span>  
  
|<span data-ttu-id="a97c0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a97c0-111">Attribute</span></span>|<span data-ttu-id="a97c0-112">描述</span><span class="sxs-lookup"><span data-stu-id="a97c0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a97c0-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="a97c0-113">createNotificationOnConnection</span></span>|<span data-ttu-id="a97c0-114">指定是否在連接時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="a97c0-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="a97c0-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="a97c0-115">disablePayloadMasking</span></span>|<span data-ttu-id="a97c0-116">指定是否停用 Web 通訊端遮罩。</span><span class="sxs-lookup"><span data-stu-id="a97c0-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="a97c0-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="a97c0-117">keepAliveInterval</span></span>|<span data-ttu-id="a97c0-118">指定保持運作的間隔。</span><span class="sxs-lookup"><span data-stu-id="a97c0-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="a97c0-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a97c0-119">maxPendingConnections</span></span>|<span data-ttu-id="a97c0-120">指定服務上等待分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="a97c0-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a97c0-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="a97c0-121">receiveBufferSize</span></span>|<span data-ttu-id="a97c0-122">指定接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="a97c0-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="a97c0-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="a97c0-123">sendBufferSize</span></span>|<span data-ttu-id="a97c0-124">指定傳送緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="a97c0-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="a97c0-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="a97c0-125">subProtocol</span></span>|<span data-ttu-id="a97c0-126">指定 Web 通訊端子通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a97c0-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="a97c0-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="a97c0-127">transportUsage</span></span>|<span data-ttu-id="a97c0-128">指定何時要使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="a97c0-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="a97c0-129">transportUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="a97c0-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="a97c0-130">值</span><span class="sxs-lookup"><span data-stu-id="a97c0-130">Value</span></span>|<span data-ttu-id="a97c0-131">描述</span><span class="sxs-lookup"><span data-stu-id="a97c0-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a97c0-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="a97c0-132">WhenDuplex</span></span>|<span data-ttu-id="a97c0-133">當合約為雙工合約時，使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a97c0-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="a97c0-134">永遠</span><span class="sxs-lookup"><span data-stu-id="a97c0-134">Always</span></span>|<span data-ttu-id="a97c0-135">不論合約為何，永遠使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a97c0-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="a97c0-136">永不</span><span class="sxs-lookup"><span data-stu-id="a97c0-136">Never</span></span>|<span data-ttu-id="a97c0-137">永遠不使用 Web 通訊端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a97c0-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a97c0-138">子元素</span><span class="sxs-lookup"><span data-stu-id="a97c0-138">Child Elements</span></span>  
 <span data-ttu-id="a97c0-139">無</span><span class="sxs-lookup"><span data-stu-id="a97c0-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a97c0-140">父項目</span><span class="sxs-lookup"><span data-stu-id="a97c0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a97c0-141">項目</span><span class="sxs-lookup"><span data-stu-id="a97c0-141">Element</span></span>|<span data-ttu-id="a97c0-142">描述</span><span class="sxs-lookup"><span data-stu-id="a97c0-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a97c0-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a97c0-143">\<netHttpBinding></span></span>|<span data-ttu-id="a97c0-144">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a97c0-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a97c0-145">範例</span><span class="sxs-lookup"><span data-stu-id="a97c0-145">Example</span></span>  
 <span data-ttu-id="a97c0-146">下列範例示範如何使用\<webSocketSettings > 項目。</span><span class="sxs-lookup"><span data-stu-id="a97c0-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a97c0-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a97c0-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="a97c0-148">繫結</span><span class="sxs-lookup"><span data-stu-id="a97c0-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a97c0-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a97c0-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a97c0-150">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="a97c0-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a97c0-151">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a97c0-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
