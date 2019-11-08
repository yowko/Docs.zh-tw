---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736503"
---
# <a name="peertransport"></a><span data-ttu-id="8fb18-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="8fb18-101">\<peerTransport></span></span>
<span data-ttu-id="8fb18-102">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="8fb18-102">Defines a peer transport for a custom binding.</span></span>  
  
<span data-ttu-id="8fb18-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8fb18-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8fb18-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8fb18-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8fb18-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="8fb18-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8fb18-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="8fb18-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="8fb18-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="8fb18-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8fb18-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**</span><span class="sxs-lookup"><span data-stu-id="8fb18-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fb18-109">語法</span><span class="sxs-lookup"><span data-stu-id="8fb18-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fb18-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8fb18-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8fb18-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8fb18-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fb18-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8fb18-112">Attributes</span></span>  
  
|<span data-ttu-id="8fb18-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8fb18-113">Attribute</span></span>|<span data-ttu-id="8fb18-114">描述</span><span class="sxs-lookup"><span data-stu-id="8fb18-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fb18-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="8fb18-115">listenIpAddress</span></span>|<span data-ttu-id="8fb18-116">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="8fb18-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="8fb18-117">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="8fb18-117">The default is `null`.</span></span>|  
|<span data-ttu-id="8fb18-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8fb18-118">maxBufferPoolSize</span></span>|<span data-ttu-id="8fb18-119">正整數，指定緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8fb18-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="8fb18-120">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="8fb18-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="8fb18-121">WCF 有許多組件會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8fb18-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="8fb18-122">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="8fb18-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="8fb18-123">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="8fb18-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="8fb18-124">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="8fb18-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="8fb18-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8fb18-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="8fb18-126">正整數，這個正整數會定義包含標頭之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="8fb18-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="8fb18-127">當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8fb18-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="8fb18-128">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="8fb18-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8fb18-129">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="8fb18-129">The default is 65536.</span></span>|  
|<span data-ttu-id="8fb18-130">連接埠</span><span class="sxs-lookup"><span data-stu-id="8fb18-130">port</span></span>|<span data-ttu-id="8fb18-131">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="8fb18-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="8fb18-132">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="8fb18-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="8fb18-133">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="8fb18-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fb18-134">子項目</span><span class="sxs-lookup"><span data-stu-id="8fb18-134">Child Elements</span></span>  
  
|<span data-ttu-id="8fb18-135">項目</span><span class="sxs-lookup"><span data-stu-id="8fb18-135">Element</span></span>|<span data-ttu-id="8fb18-136">描述</span><span class="sxs-lookup"><span data-stu-id="8fb18-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fb18-137">\<security ></span><span class="sxs-lookup"><span data-stu-id="8fb18-137">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="8fb18-138">定義此傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="8fb18-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="8fb18-139">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="8fb18-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fb18-140">父項目</span><span class="sxs-lookup"><span data-stu-id="8fb18-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8fb18-141">項目</span><span class="sxs-lookup"><span data-stu-id="8fb18-141">Element</span></span>|<span data-ttu-id="8fb18-142">描述</span><span class="sxs-lookup"><span data-stu-id="8fb18-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fb18-143">\<binding ></span><span class="sxs-lookup"><span data-stu-id="8fb18-143">\<binding></span></span>](bindings.md)|<span data-ttu-id="8fb18-144">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="8fb18-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fb18-145">備註</span><span class="sxs-lookup"><span data-stu-id="8fb18-145">Remarks</span></span>  
 <span data-ttu-id="8fb18-146">這個傳輸不可與具有要求/回覆作業的合約一起使用。</span><span class="sxs-lookup"><span data-stu-id="8fb18-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb18-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb18-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8fb18-148">傳輸</span><span class="sxs-lookup"><span data-stu-id="8fb18-148">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="8fb18-149">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="8fb18-149">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="8fb18-150">繫結</span><span class="sxs-lookup"><span data-stu-id="8fb18-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8fb18-151">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="8fb18-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8fb18-152">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="8fb18-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8fb18-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8fb18-153">\<customBinding></span></span>](custombinding.md)
