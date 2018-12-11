---
title: '&lt;Udpannouncementendpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: 50e3b283bb10ba3f34303acbbd76b42d37fa7078
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127793"
---
# <a name="ltudptransportsettingsgt"></a><span data-ttu-id="db8fe-102">&lt;Udpannouncementendpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="db8fe-102">&lt;udpTransportSettings&gt;</span></span>
<span data-ttu-id="db8fe-103">這個組態項目會公開 UDP 傳輸設定[ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="db8fe-103">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span></span>  
  
<span data-ttu-id="db8fe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db8fe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="db8fe-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="db8fe-105">\<standardEndpoints></span></span>  
<span data-ttu-id="db8fe-106">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="db8fe-106">\<udpDiscoveryEndpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db8fe-107">語法</span><span class="sxs-lookup"><span data-stu-id="db8fe-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer" 
                              maxBufferPoolSize="Integer" 
                              maxMulticastRetransmitCount="Integer" 
                              maxPendingMessageCount="Integer" 
                              maxReceivedMessageSize="Integer" 
                              maxUnicastRetransmitCount="Integer" 
                              multicastInterfaceId="String" 
                              socketReceiveBufferSize="Integer" 
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db8fe-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="db8fe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db8fe-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="db8fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db8fe-110">屬性</span><span class="sxs-lookup"><span data-stu-id="db8fe-110">Attributes</span></span>  
  
|<span data-ttu-id="db8fe-111">屬性</span><span class="sxs-lookup"><span data-stu-id="db8fe-111">Attribute</span></span>|<span data-ttu-id="db8fe-112">描述</span><span class="sxs-lookup"><span data-stu-id="db8fe-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db8fe-113">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="db8fe-113">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="db8fe-114">整數，指定傳輸用於識別重複訊息的最大訊息雜湊數目。</span><span class="sxs-lookup"><span data-stu-id="db8fe-114">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="db8fe-115">重複偵測會在 TransportManager 層級完成。</span><span class="sxs-lookup"><span data-stu-id="db8fe-115">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="db8fe-116">將這個屬性設定為 0 會停用重複訊偵測。</span><span class="sxs-lookup"><span data-stu-id="db8fe-116">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="db8fe-117">這個屬性為系統管理員或開發人員提供關閉重複訊息偵測演算法的方式。</span><span class="sxs-lookup"><span data-stu-id="db8fe-117">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="db8fe-118">如果您要實作自己的重複偵測演算法，可以使用此設定。</span><span class="sxs-lookup"><span data-stu-id="db8fe-118">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="db8fe-119">預設值為 4112。</span><span class="sxs-lookup"><span data-stu-id="db8fe-119">The default is 4112.</span></span>|  
|<span data-ttu-id="db8fe-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="db8fe-120">maxBufferPoolSize</span></span>|<span data-ttu-id="db8fe-121">整數，指定傳輸所使用之任何緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="db8fe-121">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="db8fe-122">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="db8fe-122">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="db8fe-123">整數，指定應重新傳送訊息的次數上限 (除了第一次傳送之外)。</span><span class="sxs-lookup"><span data-stu-id="db8fe-123">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="db8fe-124">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="db8fe-124">The default is 2.</span></span>|  
|<span data-ttu-id="db8fe-125">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="db8fe-125">maxPendingMessageCount</span></span>|<span data-ttu-id="db8fe-126">整數，指定已接收但尚未從個別通道執行個體的 InputQueue 移除的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="db8fe-126">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="db8fe-127">如果 InputQueue 已達到其暫止訊息計數的限制，則會捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="db8fe-127">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="db8fe-128">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="db8fe-128">The default is 32.</span></span>|  
|<span data-ttu-id="db8fe-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="db8fe-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="db8fe-130">整數，指定繫結可處理之訊息的大小上限。</span><span class="sxs-lookup"><span data-stu-id="db8fe-130">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="db8fe-131">預設值為 65507。</span><span class="sxs-lookup"><span data-stu-id="db8fe-131">The default value is 65507.</span></span>|  
|<span data-ttu-id="db8fe-132">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="db8fe-132">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="db8fe-133">整數，指定應重新傳送訊息的次數上限 (除了第一次傳送之外)。</span><span class="sxs-lookup"><span data-stu-id="db8fe-133">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="db8fe-134">如果訊息是傳送至單點傳播位址，並且收到含有對應 RelatesTo 標頭的回應訊息，重新傳輸可能會較早終止 (在重新傳輸您設定的次數之前)。</span><span class="sxs-lookup"><span data-stu-id="db8fe-134">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="db8fe-135">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="db8fe-135">The default value is 1.</span></span>|  
|<span data-ttu-id="db8fe-136">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="db8fe-136">multicastInterfaceId</span></span>|<span data-ttu-id="db8fe-137">字串，這個字串可唯一識別在多重主目錄電腦上傳送及接收多點傳送流量時應使用的網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="db8fe-137">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="db8fe-138">在執行階段，傳輸會使用這個屬性值查詢介面索引，接著使用介面索引設定 `IP_MULTICAST_IF` 和 `IPV6_MULTICAST_IF` 通訊端選項。</span><span class="sxs-lookup"><span data-stu-id="db8fe-138">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="db8fe-139">聯結多點傳送群組時會使用相同的介面索引 (如果適用的話)。</span><span class="sxs-lookup"><span data-stu-id="db8fe-139">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="db8fe-140">預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="db8fe-140">The default value is `null`.</span></span>|  
|<span data-ttu-id="db8fe-141">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="db8fe-141">socketReceiveBufferSize</span></span>|<span data-ttu-id="db8fe-142">整數，指定基礎 WinSock 通訊端上接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="db8fe-142">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="db8fe-143">接收通道的使用者可以在繫結上使用此屬性控制系統接收資料時的行為。</span><span class="sxs-lookup"><span data-stu-id="db8fe-143">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="db8fe-144">例如，假設應用程式會於最大臨界值耗用傳入 WCF 訊息，則使用此屬性較高的值可讓訊息在等候應用程式能夠加以處理時，堆疊在 WinSock 緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="db8fe-144">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="db8fe-145">在同樣情況下使用較低的值，會導致訊息遭捨棄。</span><span class="sxs-lookup"><span data-stu-id="db8fe-145">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="db8fe-146">這個屬性會公開基礎 WinSock`SO_RCVBUF`通訊端選項。此屬性值必須是至少大小`maxReceivedMessageSize`。</span><span class="sxs-lookup"><span data-stu-id="db8fe-146">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="db8fe-147">將它設定為值小於`maxReceivedMessageSize`會導致執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db8fe-147">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="db8fe-148">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="db8fe-148">The default value is 65536.</span></span>|  
|<span data-ttu-id="db8fe-149">timeToLive</span><span class="sxs-lookup"><span data-stu-id="db8fe-149">timeToLive</span></span>|<span data-ttu-id="db8fe-150">整數，指定多點傳送封包可以周遊的網路區段躍點數目。</span><span class="sxs-lookup"><span data-stu-id="db8fe-150">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="db8fe-151">這個屬性會公開與 `IP_MULTICAST_TTL` 和 `IP_TTL` 通訊端選項相關聯的功能。</span><span class="sxs-lookup"><span data-stu-id="db8fe-151">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="db8fe-152">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="db8fe-152">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db8fe-153">子元素</span><span class="sxs-lookup"><span data-stu-id="db8fe-153">Child Elements</span></span>  
 <span data-ttu-id="db8fe-154">無。</span><span class="sxs-lookup"><span data-stu-id="db8fe-154">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db8fe-155">父項目</span><span class="sxs-lookup"><span data-stu-id="db8fe-155">Parent Elements</span></span>  
  
|<span data-ttu-id="db8fe-156">項目</span><span class="sxs-lookup"><span data-stu-id="db8fe-156">Element</span></span>|<span data-ttu-id="db8fe-157">描述</span><span class="sxs-lookup"><span data-stu-id="db8fe-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db8fe-158">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="db8fe-158">\<udpDiscoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|<span data-ttu-id="db8fe-159">具有固定探索合約及 UDP 傳輸繫結的標準端點。</span><span class="sxs-lookup"><span data-stu-id="db8fe-159">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db8fe-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db8fe-160">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
