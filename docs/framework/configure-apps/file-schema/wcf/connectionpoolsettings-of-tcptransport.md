---
title: '&lt;tcpTransport&gt; 的 &lt;connectionPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 1fbc4e179fa5f59a903dad51728638a1e182b23e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753075"
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="995e4-102">&lt;tcpTransport&gt; 的 &lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="995e4-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="995e4-103">指定 TCP 傳輸的其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="995e4-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="995e4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="995e4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="995e4-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="995e4-105">\<bindings></span></span>  
<span data-ttu-id="995e4-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="995e4-106">\<customBinding></span></span>  
<span data-ttu-id="995e4-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="995e4-107">\<binding></span></span>  
<span data-ttu-id="995e4-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="995e4-108">\<tcpTransport></span></span>  
<span data-ttu-id="995e4-109">\<n ></span><span class="sxs-lookup"><span data-stu-id="995e4-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995e4-110">語法</span><span class="sxs-lookup"><span data-stu-id="995e4-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="995e4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="995e4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="995e4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="995e4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="995e4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="995e4-113">Attributes</span></span>  
  
|<span data-ttu-id="995e4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="995e4-114">Attribute</span></span>|<span data-ttu-id="995e4-115">描述</span><span class="sxs-lookup"><span data-stu-id="995e4-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="995e4-116">定義用於傳出通道之連線集區名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="995e4-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="995e4-117">在資料流處理模式中，不會共用連線，意指會停用連線集區。</span><span class="sxs-lookup"><span data-stu-id="995e4-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="995e4-118">預設為 "default" 字串。</span><span class="sxs-lookup"><span data-stu-id="995e4-118">The default is a "default" string.</span></span> <span data-ttu-id="995e4-119">您可以修改這個值，將特定用戶端的連線隔離在不同群組中。</span><span class="sxs-lookup"><span data-stu-id="995e4-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="995e4-120">正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="995e4-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="995e4-121">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="995e4-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="995e4-122"><xref:System.TimeSpan>，指定作用中連線關閉前的時間。</span><span class="sxs-lookup"><span data-stu-id="995e4-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="995e4-123">預設為 00:05:00。</span><span class="sxs-lookup"><span data-stu-id="995e4-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="995e4-124">連線會在傳回至連線快取時關閉，而不是在傳輸作用期間關閉。</span><span class="sxs-lookup"><span data-stu-id="995e4-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="995e4-125">TCP 傳輸所使用的連線快取會依各端點的需要建立新連線，最高可達 `maxOutboundConnectionsPerEndpoint.` 所設定的快取限制。</span><span class="sxs-lookup"><span data-stu-id="995e4-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="995e4-126">正整數，指定與服務初始化之遠端端點連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="995e4-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="995e4-127">超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="995e4-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="995e4-128">`idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。</span><span class="sxs-lookup"><span data-stu-id="995e4-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="995e4-129">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="995e4-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="995e4-130">這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。</span><span class="sxs-lookup"><span data-stu-id="995e4-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="995e4-131">如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。</span><span class="sxs-lookup"><span data-stu-id="995e4-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="995e4-132">在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="995e4-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="995e4-133">子項目</span><span class="sxs-lookup"><span data-stu-id="995e4-133">Child Elements</span></span>  
 <span data-ttu-id="995e4-134">無。</span><span class="sxs-lookup"><span data-stu-id="995e4-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="995e4-135">父項目</span><span class="sxs-lookup"><span data-stu-id="995e4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="995e4-136">項目</span><span class="sxs-lookup"><span data-stu-id="995e4-136">Element</span></span>|<span data-ttu-id="995e4-137">描述</span><span class="sxs-lookup"><span data-stu-id="995e4-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="995e4-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="995e4-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="995e4-139">定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="995e4-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="995e4-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="995e4-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="995e4-141">傳輸</span><span class="sxs-lookup"><span data-stu-id="995e4-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="995e4-142">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="995e4-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="995e4-143">繫結</span><span class="sxs-lookup"><span data-stu-id="995e4-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="995e4-144">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="995e4-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="995e4-145">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="995e4-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="995e4-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="995e4-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
