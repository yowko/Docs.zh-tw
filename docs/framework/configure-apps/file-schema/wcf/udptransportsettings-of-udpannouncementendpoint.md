---
title: <udpTransportSettings> 的 <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: b67bdf825948dffe18aabe91b0de236eb929bccc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854856"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a><span data-ttu-id="694ce-102">\<udptransportsettings > 的\<udpannouncementendpoint ></span><span class="sxs-lookup"><span data-stu-id="694ce-102">\<udpTransportSettings> of \<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="694ce-103">此 configuration 專案會公開[ \<udptransportsettings >](udpannouncementendpoint.md)的 UDP 傳輸設定。</span><span class="sxs-lookup"><span data-stu-id="694ce-103">This configuration element exposes UDP transport settings for [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md).</span></span>  
  
<span data-ttu-id="694ce-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="694ce-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="694ce-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="694ce-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="694ce-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="694ce-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="694ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Udptransportsettings >** ](udpannouncementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="694ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpAnnouncementEndpoint>**](udpannouncementendpoint.md)</span></span>\
<span data-ttu-id="694ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<updTransportSettings >**</span><span class="sxs-lookup"><span data-stu-id="694ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="694ce-109">語法</span><span class="sxs-lookup"><span data-stu-id="694ce-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
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
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="694ce-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="694ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="694ce-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="694ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="694ce-112">屬性</span><span class="sxs-lookup"><span data-stu-id="694ce-112">Attributes</span></span>  
  
|<span data-ttu-id="694ce-113">屬性</span><span class="sxs-lookup"><span data-stu-id="694ce-113">Attribute</span></span>|<span data-ttu-id="694ce-114">描述</span><span class="sxs-lookup"><span data-stu-id="694ce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="694ce-115">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="694ce-115">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="694ce-116">整數，指定傳輸用於識別重複訊息的最大訊息雜湊數目。</span><span class="sxs-lookup"><span data-stu-id="694ce-116">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="694ce-117">重複偵測會在 TransportManager 層級完成。</span><span class="sxs-lookup"><span data-stu-id="694ce-117">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="694ce-118">將這個屬性設定為 0 會停用重複訊偵測。</span><span class="sxs-lookup"><span data-stu-id="694ce-118">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="694ce-119">這個屬性為系統管理員或開發人員提供關閉重複訊息偵測演算法的方式。</span><span class="sxs-lookup"><span data-stu-id="694ce-119">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="694ce-120">如果您要實作自己的重複偵測演算法，可以使用此設定。</span><span class="sxs-lookup"><span data-stu-id="694ce-120">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="694ce-121">預設值為 4112。</span><span class="sxs-lookup"><span data-stu-id="694ce-121">The default is 4112.</span></span>|  
|<span data-ttu-id="694ce-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="694ce-122">maxBufferPoolSize</span></span>|<span data-ttu-id="694ce-123">整數，指定傳輸所使用之任何緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="694ce-123">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="694ce-124">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="694ce-124">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="694ce-125">整數，指定應重新傳送訊息的次數上限 (除了第一次傳送之外)。</span><span class="sxs-lookup"><span data-stu-id="694ce-125">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="694ce-126">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="694ce-126">The default is 2.</span></span>|  
|<span data-ttu-id="694ce-127">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="694ce-127">maxPendingMessageCount</span></span>|<span data-ttu-id="694ce-128">整數，指定已接收但尚未從個別通道執行個體的 InputQueue 移除的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="694ce-128">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="694ce-129">如果 InputQueue 已達到其暫止訊息計數的限制，則會捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="694ce-129">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="694ce-130">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="694ce-130">The default is 32.</span></span>|  
|<span data-ttu-id="694ce-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="694ce-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="694ce-132">整數，指定繫結可處理之訊息的大小上限。</span><span class="sxs-lookup"><span data-stu-id="694ce-132">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="694ce-133">預設值為 65507。</span><span class="sxs-lookup"><span data-stu-id="694ce-133">The default value is 65507.</span></span>|  
|<span data-ttu-id="694ce-134">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="694ce-134">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="694ce-135">整數，指定應重新傳送訊息的次數上限 (除了第一次傳送之外)。</span><span class="sxs-lookup"><span data-stu-id="694ce-135">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="694ce-136">如果訊息是傳送至單點傳播位址，並且收到含有對應 RelatesTo 標頭的回應訊息，重新傳輸可能會較早終止 (在重新傳輸您設定的次數之前)。</span><span class="sxs-lookup"><span data-stu-id="694ce-136">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="694ce-137">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="694ce-137">The default value is 1.</span></span>|  
|<span data-ttu-id="694ce-138">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="694ce-138">multicastInterfaceId</span></span>|<span data-ttu-id="694ce-139">字串，這個字串可唯一識別在多重主目錄電腦上傳送及接收多點傳送流量時應使用的網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="694ce-139">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="694ce-140">在執行階段，傳輸會使用這個屬性值查詢介面索引，接著使用介面索引設定 `IP_MULTICAST_IF` 和 `IPV6_MULTICAST_IF` 通訊端選項。</span><span class="sxs-lookup"><span data-stu-id="694ce-140">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="694ce-141">聯結多點傳送群組時會使用相同的介面索引 (如果適用的話)。</span><span class="sxs-lookup"><span data-stu-id="694ce-141">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="694ce-142">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="694ce-142">The default value is `null`.</span></span>|  
|<span data-ttu-id="694ce-143">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="694ce-143">socketReceiveBufferSize</span></span>|<span data-ttu-id="694ce-144">整數，指定基礎 WinSock 通訊端上接收緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="694ce-144">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="694ce-145">接收通道的使用者可以在繫結上使用此屬性控制系統接收資料時的行為。</span><span class="sxs-lookup"><span data-stu-id="694ce-145">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="694ce-146">例如，假設應用程式會於最大臨界值耗用傳入 WCF 訊息，則使用此屬性較高的值可讓訊息在等候應用程式能夠加以處理時，堆疊在 WinSock 緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="694ce-146">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="694ce-147">同樣的情況下若使用較小的值，則會導致捨棄訊息。這個屬性會公開基礎 WinSock `SO_RCVBUF` 通訊端選項。此屬性的值至少須等於 `maxReceivedMessageSize` 的大小。</span><span class="sxs-lookup"><span data-stu-id="694ce-147">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="694ce-148">將它設定為小於 `maxReceivedMessageSize` 的值，會導致執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="694ce-148">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="694ce-149">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="694ce-149">The default value is 65536.</span></span>|  
|<span data-ttu-id="694ce-150">timeToLive</span><span class="sxs-lookup"><span data-stu-id="694ce-150">timeToLive</span></span>|<span data-ttu-id="694ce-151">整數，指定多點傳送封包可以周遊的網路區段躍點數目。</span><span class="sxs-lookup"><span data-stu-id="694ce-151">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="694ce-152">這個屬性會公開與 `IP_MULTICAST_TTL` 和 `IP_TTL` 通訊端選項相關聯的功能。</span><span class="sxs-lookup"><span data-stu-id="694ce-152">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="694ce-153">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="694ce-153">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="694ce-154">子元素</span><span class="sxs-lookup"><span data-stu-id="694ce-154">Child Elements</span></span>  
 <span data-ttu-id="694ce-155">無。</span><span class="sxs-lookup"><span data-stu-id="694ce-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="694ce-156">父項目</span><span class="sxs-lookup"><span data-stu-id="694ce-156">Parent Elements</span></span>  
  
|<span data-ttu-id="694ce-157">項目</span><span class="sxs-lookup"><span data-stu-id="694ce-157">Element</span></span>|<span data-ttu-id="694ce-158">說明</span><span class="sxs-lookup"><span data-stu-id="694ce-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="694ce-159">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="694ce-159">\<udpAnnouncementEndpoint></span></span>](udpannouncementendpoint.md)|<span data-ttu-id="694ce-160">具有固定公告合約及 UDP 傳輸繫結的標準端點。</span><span class="sxs-lookup"><span data-stu-id="694ce-160">A standard endpoint that has fixed announcement contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="694ce-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="694ce-161">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
