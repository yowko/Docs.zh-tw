---
title: '&lt;connectionPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 1e3001f60ae0f18fee88678cae1e9e55d90822c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526755"
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="c376d-102">&lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="c376d-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="c376d-103">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="c376d-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="c376d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c376d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c376d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c376d-105">\<bindings></span></span>  
<span data-ttu-id="c376d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c376d-106">\<customBinding></span></span>  
<span data-ttu-id="c376d-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="c376d-107">\<binding></span></span>  
<span data-ttu-id="c376d-108">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="c376d-108">\<namePipeTransport></span></span>  
<span data-ttu-id="c376d-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="c376d-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c376d-110">語法</span><span class="sxs-lookup"><span data-stu-id="c376d-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c376d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c376d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c376d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c376d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c376d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c376d-113">Attributes</span></span>  
  
|<span data-ttu-id="c376d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c376d-114">Attribute</span></span>|<span data-ttu-id="c376d-115">描述</span><span class="sxs-lookup"><span data-stu-id="c376d-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="c376d-116">定義用於傳出通道之連線集區名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="c376d-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="c376d-117">在資料流處理模式中，不會共用連線，意指會停用連線集區。</span><span class="sxs-lookup"><span data-stu-id="c376d-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="c376d-118">預設為 "default" 字串。</span><span class="sxs-lookup"><span data-stu-id="c376d-118">The default is a "default" string.</span></span> <span data-ttu-id="c376d-119">您可以修改這個值，將特定用戶端的連線隔離在不同群組中。</span><span class="sxs-lookup"><span data-stu-id="c376d-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="c376d-120">正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="c376d-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="c376d-121">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="c376d-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="c376d-122">正整數，指定與服務初始化之遠端端點連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="c376d-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="c376d-123">超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="c376d-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="c376d-124">`idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。</span><span class="sxs-lookup"><span data-stu-id="c376d-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="c376d-125">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="c376d-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="c376d-126">這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。</span><span class="sxs-lookup"><span data-stu-id="c376d-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="c376d-127">如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。</span><span class="sxs-lookup"><span data-stu-id="c376d-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="c376d-128">在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="c376d-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c376d-129">子元素</span><span class="sxs-lookup"><span data-stu-id="c376d-129">Child Elements</span></span>  
 <span data-ttu-id="c376d-130">無。</span><span class="sxs-lookup"><span data-stu-id="c376d-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c376d-131">父項目</span><span class="sxs-lookup"><span data-stu-id="c376d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="c376d-132">項目</span><span class="sxs-lookup"><span data-stu-id="c376d-132">Element</span></span>|<span data-ttu-id="c376d-133">描述</span><span class="sxs-lookup"><span data-stu-id="c376d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c376d-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="c376d-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="c376d-135">定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="c376d-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c376d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c376d-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c376d-137">傳輸</span><span class="sxs-lookup"><span data-stu-id="c376d-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="c376d-138">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="c376d-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c376d-139">繫結</span><span class="sxs-lookup"><span data-stu-id="c376d-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c376d-140">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="c376d-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c376d-141">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="c376d-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c376d-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c376d-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
