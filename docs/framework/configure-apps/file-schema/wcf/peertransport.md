---
title: '&lt;p&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9c01e997e3ba804eae3036e94f2e2e1b951b25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="dd075-102">&lt;p&gt;</span><span class="sxs-lookup"><span data-stu-id="dd075-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="dd075-103">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="dd075-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="dd075-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dd075-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dd075-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd075-105">\<bindings></span></span>  
<span data-ttu-id="dd075-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="dd075-106">\<customBinding></span></span>  
<span data-ttu-id="dd075-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd075-107">\<binding></span></span>  
<span data-ttu-id="dd075-108">\<p ></span><span class="sxs-lookup"><span data-stu-id="dd075-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd075-109">語法</span><span class="sxs-lookup"><span data-stu-id="dd075-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd075-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd075-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd075-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dd075-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd075-112">屬性</span><span class="sxs-lookup"><span data-stu-id="dd075-112">Attributes</span></span>  
  
|<span data-ttu-id="dd075-113">屬性</span><span class="sxs-lookup"><span data-stu-id="dd075-113">Attribute</span></span>|<span data-ttu-id="dd075-114">描述</span><span class="sxs-lookup"><span data-stu-id="dd075-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd075-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="dd075-115">listenIpAddress</span></span>|<span data-ttu-id="dd075-116">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd075-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="dd075-117">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="dd075-117">The default is `null`.</span></span>|  
|<span data-ttu-id="dd075-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="dd075-118">maxBufferPoolSize</span></span>|<span data-ttu-id="dd075-119">正整數，指定緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="dd075-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="dd075-120">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="dd075-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="dd075-121">WCF 有許多組件會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dd075-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="dd075-122">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="dd075-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="dd075-123">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="dd075-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="dd075-124">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="dd075-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="dd075-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="dd075-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="dd075-126">正整數，這個正整數會定義包含標頭之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="dd075-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="dd075-127">當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd075-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="dd075-128">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="dd075-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="dd075-129">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="dd075-129">The default is 65536.</span></span>|  
|<span data-ttu-id="dd075-130">連接埠</span><span class="sxs-lookup"><span data-stu-id="dd075-130">port</span></span>|<span data-ttu-id="dd075-131">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="dd075-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="dd075-132">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="dd075-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="dd075-133">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="dd075-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd075-134">子元素</span><span class="sxs-lookup"><span data-stu-id="dd075-134">Child Elements</span></span>  
  
|<span data-ttu-id="dd075-135">項目</span><span class="sxs-lookup"><span data-stu-id="dd075-135">Element</span></span>|<span data-ttu-id="dd075-136">說明</span><span class="sxs-lookup"><span data-stu-id="dd075-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd075-137">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="dd075-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="dd075-138">定義此傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd075-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="dd075-139">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="dd075-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd075-140">父項目</span><span class="sxs-lookup"><span data-stu-id="dd075-140">Parent Elements</span></span>  
  
|<span data-ttu-id="dd075-141">項目</span><span class="sxs-lookup"><span data-stu-id="dd075-141">Element</span></span>|<span data-ttu-id="dd075-142">說明</span><span class="sxs-lookup"><span data-stu-id="dd075-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd075-143">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd075-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="dd075-144">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="dd075-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd075-145">備註</span><span class="sxs-lookup"><span data-stu-id="dd075-145">Remarks</span></span>  
 <span data-ttu-id="dd075-146">這個傳輸不可與具有要求/回覆作業的合約一起使用。</span><span class="sxs-lookup"><span data-stu-id="dd075-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd075-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd075-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="dd075-148">傳輸</span><span class="sxs-lookup"><span data-stu-id="dd075-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="dd075-149">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="dd075-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="dd075-150">繫結</span><span class="sxs-lookup"><span data-stu-id="dd075-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dd075-151">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="dd075-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="dd075-152">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="dd075-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="dd075-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="dd075-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
