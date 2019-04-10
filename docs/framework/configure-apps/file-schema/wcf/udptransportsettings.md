---
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: f5be9681dc69fd68dfdfa90f4eb305dc4aa4514b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218494"
---
# <a name="udptransportsettings"></a><span data-ttu-id="8c075-101">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="8c075-101">\<udpTransportSettings></span></span>
<span data-ttu-id="8c075-102">這個組態項目會公開 UDP 傳輸設定[ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="8c075-102">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span></span>  
  
<span data-ttu-id="8c075-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8c075-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c075-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8c075-104">\<standardEndpoints></span></span>  
<span data-ttu-id="8c075-105">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="8c075-105">\<udpDiscoveryEndpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c075-106">語法</span><span class="sxs-lookup"><span data-stu-id="8c075-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c075-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8c075-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8c075-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8c075-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c075-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8c075-109">Attributes</span></span>  
  
|<span data-ttu-id="8c075-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8c075-110">Attribute</span></span>|<span data-ttu-id="8c075-111">描述</span><span class="sxs-lookup"><span data-stu-id="8c075-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c075-112">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="8c075-112">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="8c075-113">整數，指定傳輸用於識別重複訊息的最大訊息雜湊數目。</span><span class="sxs-lookup"><span data-stu-id="8c075-113">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="8c075-114">重複偵測會在 TransportManager 層級完成。</span><span class="sxs-lookup"><span data-stu-id="8c075-114">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="8c075-115">將這個屬性設定為 0 會停用重複訊偵測。</span><span class="sxs-lookup"><span data-stu-id="8c075-115">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="8c075-116">這個屬性為系統管理員或開發人員提供關閉重複訊息偵測演算法的方式。</span><span class="sxs-lookup"><span data-stu-id="8c075-116">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="8c075-117">如果您要實作自己的重複偵測演算法，可以使用此設定。</span><span class="sxs-lookup"><span data-stu-id="8c075-117">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="8c075-118">預設值為 4112。</span><span class="sxs-lookup"><span data-stu-id="8c075-118">The default is 4112.</span></span>|  
|<span data-ttu-id="8c075-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8c075-119">maxBufferPoolSize</span></span>|<span data-ttu-id="8c075-120">整數，指定傳輸所使用之任何緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8c075-120">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="8c075-121">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="8c075-121">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="8c075-122">整數，指定應重新傳送訊息的次數上限 (除了第一次傳送之外)。</span><span class="sxs-lookup"><span data-stu-id="8c075-122">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="8c075-123">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="8c075-123">The default is 2.</span></span>|  
|<span data-ttu-id="8c075-124">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="8c075-124">maxPendingMessageCount</span></span>|<span data-ttu-id="8c075-125">整數，指定已接收但尚未從個別通道執行個體的 InputQueue 移除的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="8c075-125">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="8c075-126">如果 InputQueue 已達到其暫止訊息計數的限制，則會捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="8c075-126">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="8c075-127">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="8c075-127">The default is 32.</span></span>|  
|<span data-ttu-id="8c075-128">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8c075-128">maxReceivedMessageSize</span></span>|<span data-ttu-id="8c075-129">整數，指定繫結可處理之訊息的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8c075-129">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="8c075-130">預設值為 65507。</span><span class="sxs-lookup"><span data-stu-id="8c075-130">The default value is 65507.</span></span>|  
|<span data-ttu-id="8c075-131">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="8c075-131">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="8c075-132">整數，指定應重新傳送訊息的次數上限 (除了第一次傳送之外)。</span><span class="sxs-lookup"><span data-stu-id="8c075-132">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="8c075-133">如果訊息是傳送至單點傳播位址，並且收到含有對應 RelatesTo 標頭的回應訊息，重新傳輸可能會較早終止 (在重新傳輸您設定的次數之前)。</span><span class="sxs-lookup"><span data-stu-id="8c075-133">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="8c075-134">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="8c075-134">The default value is 1.</span></span>|  
|<span data-ttu-id="8c075-135">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="8c075-135">multicastInterfaceId</span></span>|<span data-ttu-id="8c075-136">字串，這個字串可唯一識別在多重主目錄電腦上傳送及接收多點傳送流量時應使用的網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="8c075-136">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="8c075-137">在執行階段，傳輸會使用這個屬性值查詢介面索引，接著使用介面索引設定 `IP_MULTICAST_IF` 和 `IPV6_MULTICAST_IF` 通訊端選項。</span><span class="sxs-lookup"><span data-stu-id="8c075-137">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="8c075-138">聯結多點傳送群組時會使用相同的介面索引 (如果適用的話)。</span><span class="sxs-lookup"><span data-stu-id="8c075-138">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="8c075-139">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="8c075-139">The default value is `null`.</span></span>|  
|<span data-ttu-id="8c075-140">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="8c075-140">socketReceiveBufferSize</span></span>|<span data-ttu-id="8c075-141">整數，指定基礎 WinSock 通訊端上接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="8c075-141">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="8c075-142">接收通道的使用者可以在繫結上使用此屬性控制系統接收資料時的行為。</span><span class="sxs-lookup"><span data-stu-id="8c075-142">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="8c075-143">例如，假設應用程式會於最大臨界值耗用傳入 WCF 訊息，則使用此屬性較高的值可讓訊息在等候應用程式能夠加以處理時，堆疊在 WinSock 緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="8c075-143">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="8c075-144">在同樣情況下使用較低的值，會導致訊息遭捨棄。</span><span class="sxs-lookup"><span data-stu-id="8c075-144">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="8c075-145">這個屬性會公開基礎 WinSock`SO_RCVBUF`通訊端選項。此屬性值必須是至少大小`maxReceivedMessageSize`。</span><span class="sxs-lookup"><span data-stu-id="8c075-145">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="8c075-146">將它設定為值小於`maxReceivedMessageSize`會導致執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8c075-146">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="8c075-147">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="8c075-147">The default value is 65536.</span></span>|  
|<span data-ttu-id="8c075-148">timeToLive</span><span class="sxs-lookup"><span data-stu-id="8c075-148">timeToLive</span></span>|<span data-ttu-id="8c075-149">整數，指定多點傳送封包可以周遊的網路區段躍點數目。</span><span class="sxs-lookup"><span data-stu-id="8c075-149">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="8c075-150">這個屬性會公開與 `IP_MULTICAST_TTL` 和 `IP_TTL` 通訊端選項相關聯的功能。</span><span class="sxs-lookup"><span data-stu-id="8c075-150">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="8c075-151">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="8c075-151">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c075-152">子元素</span><span class="sxs-lookup"><span data-stu-id="8c075-152">Child Elements</span></span>  
 <span data-ttu-id="8c075-153">無。</span><span class="sxs-lookup"><span data-stu-id="8c075-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c075-154">父項目</span><span class="sxs-lookup"><span data-stu-id="8c075-154">Parent Elements</span></span>  
  
|<span data-ttu-id="8c075-155">項目</span><span class="sxs-lookup"><span data-stu-id="8c075-155">Element</span></span>|<span data-ttu-id="8c075-156">描述</span><span class="sxs-lookup"><span data-stu-id="8c075-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c075-157">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="8c075-157">\<udpDiscoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|<span data-ttu-id="8c075-158">具有固定探索合約及 UDP 傳輸繫結的標準端點。</span><span class="sxs-lookup"><span data-stu-id="8c075-158">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c075-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c075-159">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
