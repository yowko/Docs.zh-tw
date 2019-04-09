---
title: <connectionPoolSettings> 的 <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129970"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="d428e-102">\<connectionPoolSettings> of \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="d428e-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="d428e-103">指定 TCP 傳輸的其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="d428e-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="d428e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d428e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d428e-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d428e-105">\<bindings></span></span>  
<span data-ttu-id="d428e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d428e-106">\<customBinding></span></span>  
<span data-ttu-id="d428e-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="d428e-107">\<binding></span></span>  
<span data-ttu-id="d428e-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="d428e-108">\<tcpTransport></span></span>  
<span data-ttu-id="d428e-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="d428e-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d428e-110">語法</span><span class="sxs-lookup"><span data-stu-id="d428e-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d428e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d428e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d428e-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d428e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d428e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d428e-113">Attributes</span></span>  
  
|<span data-ttu-id="d428e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d428e-114">Attribute</span></span>|<span data-ttu-id="d428e-115">描述</span><span class="sxs-lookup"><span data-stu-id="d428e-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="d428e-116">定義用於傳出通道之連線集區名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d428e-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="d428e-117">在資料流處理模式中，不會共用連線，意指會停用連線集區。</span><span class="sxs-lookup"><span data-stu-id="d428e-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="d428e-118">預設為 "default" 字串。</span><span class="sxs-lookup"><span data-stu-id="d428e-118">The default is a "default" string.</span></span> <span data-ttu-id="d428e-119">您可以修改這個值，將特定用戶端的連線隔離在不同群組中。</span><span class="sxs-lookup"><span data-stu-id="d428e-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="d428e-120">正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="d428e-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="d428e-121">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="d428e-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="d428e-122"><xref:System.TimeSpan>，指定作用中連線關閉前的時間。</span><span class="sxs-lookup"><span data-stu-id="d428e-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="d428e-123">預設為 00:05:00。</span><span class="sxs-lookup"><span data-stu-id="d428e-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="d428e-124">連線會在傳回至連線快取時關閉，而不是在傳輸作用期間關閉。</span><span class="sxs-lookup"><span data-stu-id="d428e-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="d428e-125">使用 TCP 傳輸的連線快取建立所需的每個端點，最大快取限制所設定的新連線</span><span class="sxs-lookup"><span data-stu-id="d428e-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by</span></span> `maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="d428e-126">正整數，指定與服務初始化之遠端端點連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="d428e-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="d428e-127">超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="d428e-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="d428e-128">`idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。</span><span class="sxs-lookup"><span data-stu-id="d428e-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="d428e-129">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="d428e-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="d428e-130">這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。</span><span class="sxs-lookup"><span data-stu-id="d428e-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="d428e-131">如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。</span><span class="sxs-lookup"><span data-stu-id="d428e-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="d428e-132">在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="d428e-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d428e-133">子元素</span><span class="sxs-lookup"><span data-stu-id="d428e-133">Child Elements</span></span>  
 <span data-ttu-id="d428e-134">無。</span><span class="sxs-lookup"><span data-stu-id="d428e-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d428e-135">父項目</span><span class="sxs-lookup"><span data-stu-id="d428e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="d428e-136">項目</span><span class="sxs-lookup"><span data-stu-id="d428e-136">Element</span></span>|<span data-ttu-id="d428e-137">描述</span><span class="sxs-lookup"><span data-stu-id="d428e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d428e-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="d428e-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="d428e-139">定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="d428e-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d428e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d428e-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d428e-141">傳輸</span><span class="sxs-lookup"><span data-stu-id="d428e-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="d428e-142">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="d428e-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d428e-143">繫結</span><span class="sxs-lookup"><span data-stu-id="d428e-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d428e-144">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="d428e-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d428e-145">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d428e-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d428e-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d428e-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
