---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 6765259f290047a4199a422b4ad0cced2ffee9ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179825"
---
# <a name="peertransport"></a><span data-ttu-id="6829e-101">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="6829e-101">\<peerTransport></span></span>
<span data-ttu-id="6829e-102">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="6829e-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="6829e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6829e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6829e-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6829e-104">\<bindings></span></span>  
<span data-ttu-id="6829e-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6829e-105">\<customBinding></span></span>  
<span data-ttu-id="6829e-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="6829e-106">\<binding></span></span>  
<span data-ttu-id="6829e-107">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="6829e-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6829e-108">語法</span><span class="sxs-lookup"><span data-stu-id="6829e-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6829e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6829e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6829e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6829e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6829e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6829e-111">Attributes</span></span>  
  
|<span data-ttu-id="6829e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6829e-112">Attribute</span></span>|<span data-ttu-id="6829e-113">描述</span><span class="sxs-lookup"><span data-stu-id="6829e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6829e-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="6829e-114">listenIpAddress</span></span>|<span data-ttu-id="6829e-115">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6829e-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="6829e-116">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="6829e-116">The default is `null`.</span></span>|  
|<span data-ttu-id="6829e-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6829e-117">maxBufferPoolSize</span></span>|<span data-ttu-id="6829e-118">正整數，指定緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="6829e-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="6829e-119">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="6829e-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="6829e-120">WCF 有許多組件會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6829e-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="6829e-121">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="6829e-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6829e-122">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="6829e-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6829e-123">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="6829e-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6829e-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6829e-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="6829e-125">正整數，這個正整數會定義包含標頭之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="6829e-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="6829e-126">當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6829e-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="6829e-127">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="6829e-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6829e-128">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="6829e-128">The default is 65536.</span></span>|  
|<span data-ttu-id="6829e-129">連接埠</span><span class="sxs-lookup"><span data-stu-id="6829e-129">port</span></span>|<span data-ttu-id="6829e-130">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="6829e-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="6829e-131">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="6829e-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="6829e-132">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="6829e-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6829e-133">子元素</span><span class="sxs-lookup"><span data-stu-id="6829e-133">Child Elements</span></span>  
  
|<span data-ttu-id="6829e-134">項目</span><span class="sxs-lookup"><span data-stu-id="6829e-134">Element</span></span>|<span data-ttu-id="6829e-135">描述</span><span class="sxs-lookup"><span data-stu-id="6829e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6829e-136">\<security></span><span class="sxs-lookup"><span data-stu-id="6829e-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="6829e-137">定義此傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6829e-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="6829e-138">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="6829e-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6829e-139">父項目</span><span class="sxs-lookup"><span data-stu-id="6829e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="6829e-140">項目</span><span class="sxs-lookup"><span data-stu-id="6829e-140">Element</span></span>|<span data-ttu-id="6829e-141">描述</span><span class="sxs-lookup"><span data-stu-id="6829e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6829e-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="6829e-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6829e-143">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="6829e-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6829e-144">備註</span><span class="sxs-lookup"><span data-stu-id="6829e-144">Remarks</span></span>  
 <span data-ttu-id="6829e-145">這個傳輸不可與具有要求/回覆作業的合約一起使用。</span><span class="sxs-lookup"><span data-stu-id="6829e-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6829e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6829e-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6829e-147">傳輸</span><span class="sxs-lookup"><span data-stu-id="6829e-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="6829e-148">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="6829e-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="6829e-149">繫結</span><span class="sxs-lookup"><span data-stu-id="6829e-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6829e-150">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="6829e-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6829e-151">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6829e-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6829e-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6829e-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
