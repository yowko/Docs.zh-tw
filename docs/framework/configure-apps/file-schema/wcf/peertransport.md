---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 68832c3a5bd4cc423642a6272e70cbecab86d6a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181540"
---
# \<peerTransport>

<span data-ttu-id="fe4c2-101">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="fe4c2-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe4c2-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe4c2-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fe4c2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="fe4c2-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe4c2-105">屬性</span><span class="sxs-lookup"><span data-stu-id="fe4c2-105">Attributes</span></span>  
  
|<span data-ttu-id="fe4c2-106">屬性</span><span class="sxs-lookup"><span data-stu-id="fe4c2-106">Attribute</span></span>|<span data-ttu-id="fe4c2-107">描述</span><span class="sxs-lookup"><span data-stu-id="fe4c2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe4c2-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="fe4c2-108">listenIpAddress</span></span>|<span data-ttu-id="fe4c2-109">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="fe4c2-110">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-110">The default is `null`.</span></span>|  
|<span data-ttu-id="fe4c2-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="fe4c2-111">maxBufferPoolSize</span></span>|<span data-ttu-id="fe4c2-112">正整數，指定緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="fe4c2-113">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="fe4c2-114">WCF 有許多組件會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="fe4c2-115">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="fe4c2-116">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="fe4c2-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="fe4c2-117">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="fe4c2-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="fe4c2-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="fe4c2-119">正整數，這個正整數會定義包含標頭之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="fe4c2-120">當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="fe4c2-121">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="fe4c2-122">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-122">The default is 65536.</span></span>|  
|<span data-ttu-id="fe4c2-123">連接埠</span><span class="sxs-lookup"><span data-stu-id="fe4c2-123">port</span></span>|<span data-ttu-id="fe4c2-124">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="fe4c2-125">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="fe4c2-126">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe4c2-127">子元素</span><span class="sxs-lookup"><span data-stu-id="fe4c2-127">Child Elements</span></span>  
  
|<span data-ttu-id="fe4c2-128">項目</span><span class="sxs-lookup"><span data-stu-id="fe4c2-128">Element</span></span>|<span data-ttu-id="fe4c2-129">描述</span><span class="sxs-lookup"><span data-stu-id="fe4c2-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="fe4c2-130">定義此傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="fe4c2-131">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe4c2-132">父項目</span><span class="sxs-lookup"><span data-stu-id="fe4c2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fe4c2-133">項目</span><span class="sxs-lookup"><span data-stu-id="fe4c2-133">Element</span></span>|<span data-ttu-id="fe4c2-134">描述</span><span class="sxs-lookup"><span data-stu-id="fe4c2-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="fe4c2-135">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe4c2-136">備註</span><span class="sxs-lookup"><span data-stu-id="fe4c2-136">Remarks</span></span>  

 <span data-ttu-id="fe4c2-137">這個傳輸不可與具有要求/回覆作業的合約一起使用。</span><span class="sxs-lookup"><span data-stu-id="fe4c2-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4c2-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe4c2-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fe4c2-139">傳輸</span><span class="sxs-lookup"><span data-stu-id="fe4c2-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="fe4c2-140">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="fe4c2-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="fe4c2-141">繫結</span><span class="sxs-lookup"><span data-stu-id="fe4c2-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fe4c2-142">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="fe4c2-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fe4c2-143">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fe4c2-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
