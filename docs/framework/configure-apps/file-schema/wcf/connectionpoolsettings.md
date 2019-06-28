---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 0e56bb5c9e485559d712281a51e79f54c9661b5a
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423130"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="459c9-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="459c9-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="459c9-102">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="459c9-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="459c9-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="459c9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="459c9-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="459c9-104">\<bindings></span></span>  
<span data-ttu-id="459c9-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="459c9-105">\<customBinding></span></span>  
<span data-ttu-id="459c9-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="459c9-106">\<binding></span></span>  
<span data-ttu-id="459c9-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="459c9-107">\<namePipeTransport></span></span>  
<span data-ttu-id="459c9-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="459c9-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="459c9-109">語法</span><span class="sxs-lookup"><span data-stu-id="459c9-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="459c9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="459c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="459c9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="459c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="459c9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="459c9-112">Attributes</span></span>  
  
|<span data-ttu-id="459c9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="459c9-113">Attribute</span></span>|<span data-ttu-id="459c9-114">描述</span><span class="sxs-lookup"><span data-stu-id="459c9-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="459c9-115">定義用於傳出通道之連線集區名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="459c9-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="459c9-116">在資料流處理模式中，不會共用連線，意指會停用連線集區。</span><span class="sxs-lookup"><span data-stu-id="459c9-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="459c9-117">預設為 "default" 字串。</span><span class="sxs-lookup"><span data-stu-id="459c9-117">The default is a "default" string.</span></span> <span data-ttu-id="459c9-118">您可以修改這個值，將特定用戶端的連線隔離在不同群組中。</span><span class="sxs-lookup"><span data-stu-id="459c9-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="459c9-119">正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="459c9-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="459c9-120">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="459c9-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="459c9-121">正整數，指定與服務初始化之遠端端點連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="459c9-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="459c9-122">超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="459c9-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="459c9-123">`idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。</span><span class="sxs-lookup"><span data-stu-id="459c9-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="459c9-124">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="459c9-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="459c9-125">這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。</span><span class="sxs-lookup"><span data-stu-id="459c9-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="459c9-126">如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。</span><span class="sxs-lookup"><span data-stu-id="459c9-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="459c9-127">在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="459c9-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="459c9-128">子元素</span><span class="sxs-lookup"><span data-stu-id="459c9-128">Child Elements</span></span>  
 <span data-ttu-id="459c9-129">無。</span><span class="sxs-lookup"><span data-stu-id="459c9-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="459c9-130">父項目</span><span class="sxs-lookup"><span data-stu-id="459c9-130">Parent Elements</span></span>  
  
|<span data-ttu-id="459c9-131">項目</span><span class="sxs-lookup"><span data-stu-id="459c9-131">Element</span></span>|<span data-ttu-id="459c9-132">描述</span><span class="sxs-lookup"><span data-stu-id="459c9-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="459c9-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="459c9-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="459c9-134">定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="459c9-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="459c9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="459c9-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="459c9-136">傳輸</span><span class="sxs-lookup"><span data-stu-id="459c9-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="459c9-137">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="459c9-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="459c9-138">繫結</span><span class="sxs-lookup"><span data-stu-id="459c9-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="459c9-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="459c9-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="459c9-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="459c9-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="459c9-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="459c9-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
