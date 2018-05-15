---
title: '&lt;p&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: df192c6a602aa073f48fab4229b4be3fbeb2349d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="7e9fe-102">&lt;p&gt;</span><span class="sxs-lookup"><span data-stu-id="7e9fe-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="7e9fe-103">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="7e9fe-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7e9fe-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7e9fe-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7e9fe-105">\<bindings></span></span>  
<span data-ttu-id="7e9fe-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7e9fe-106">\<customBinding></span></span>  
<span data-ttu-id="7e9fe-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7e9fe-107">\<binding></span></span>  
<span data-ttu-id="7e9fe-108">\<p ></span><span class="sxs-lookup"><span data-stu-id="7e9fe-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e9fe-109">語法</span><span class="sxs-lookup"><span data-stu-id="7e9fe-109">Syntax</span></span>  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e9fe-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7e9fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7e9fe-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e9fe-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7e9fe-112">Attributes</span></span>  
  
|<span data-ttu-id="7e9fe-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7e9fe-113">Attribute</span></span>|<span data-ttu-id="7e9fe-114">描述</span><span class="sxs-lookup"><span data-stu-id="7e9fe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e9fe-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="7e9fe-115">listenIpAddress</span></span>|<span data-ttu-id="7e9fe-116">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="7e9fe-117">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-117">The default is `null`.</span></span>|  
|<span data-ttu-id="7e9fe-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7e9fe-118">maxBufferPoolSize</span></span>|<span data-ttu-id="7e9fe-119">正整數，指定緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="7e9fe-120">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="7e9fe-121">WCF 有許多組件會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="7e9fe-122">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7e9fe-123">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="7e9fe-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7e9fe-124">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="7e9fe-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7e9fe-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="7e9fe-126">正整數，這個正整數會定義包含標頭之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="7e9fe-127">當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="7e9fe-128">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7e9fe-129">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-129">The default is 65536.</span></span>|  
|<span data-ttu-id="7e9fe-130">連接埠</span><span class="sxs-lookup"><span data-stu-id="7e9fe-130">port</span></span>|<span data-ttu-id="7e9fe-131">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="7e9fe-132">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="7e9fe-133">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e9fe-134">子項目</span><span class="sxs-lookup"><span data-stu-id="7e9fe-134">Child Elements</span></span>  
  
|<span data-ttu-id="7e9fe-135">項目</span><span class="sxs-lookup"><span data-stu-id="7e9fe-135">Element</span></span>|<span data-ttu-id="7e9fe-136">描述</span><span class="sxs-lookup"><span data-stu-id="7e9fe-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e9fe-137">\<security></span><span class="sxs-lookup"><span data-stu-id="7e9fe-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="7e9fe-138">定義此傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="7e9fe-139">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e9fe-140">父項目</span><span class="sxs-lookup"><span data-stu-id="7e9fe-140">Parent Elements</span></span>  
  
|<span data-ttu-id="7e9fe-141">項目</span><span class="sxs-lookup"><span data-stu-id="7e9fe-141">Element</span></span>|<span data-ttu-id="7e9fe-142">描述</span><span class="sxs-lookup"><span data-stu-id="7e9fe-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e9fe-143">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7e9fe-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7e9fe-144">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e9fe-145">備註</span><span class="sxs-lookup"><span data-stu-id="7e9fe-145">Remarks</span></span>  
 <span data-ttu-id="7e9fe-146">這個傳輸不可與具有要求/回覆作業的合約一起使用。</span><span class="sxs-lookup"><span data-stu-id="7e9fe-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e9fe-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e9fe-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7e9fe-148">傳輸</span><span class="sxs-lookup"><span data-stu-id="7e9fe-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="7e9fe-149">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="7e9fe-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="7e9fe-150">繫結</span><span class="sxs-lookup"><span data-stu-id="7e9fe-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7e9fe-151">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="7e9fe-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7e9fe-152">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="7e9fe-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7e9fe-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7e9fe-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
