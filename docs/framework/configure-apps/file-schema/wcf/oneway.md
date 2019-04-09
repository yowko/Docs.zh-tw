---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: bfda2b9d7b3aa5219a3e4c344347d3b10419a7bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102410"
---
# <a name="oneway"></a><span data-ttu-id="4be79-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="4be79-101">\<oneWay></span></span>
<span data-ttu-id="4be79-102">針對自訂繫結啟用封包路由和使用單向方法。</span><span class="sxs-lookup"><span data-stu-id="4be79-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="4be79-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4be79-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4be79-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4be79-104">\<bindings></span></span>  
<span data-ttu-id="4be79-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4be79-105">\<customBinding></span></span>  
<span data-ttu-id="4be79-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="4be79-106">\<binding></span></span>  
<span data-ttu-id="4be79-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="4be79-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4be79-108">語法</span><span class="sxs-lookup"><span data-stu-id="4be79-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4be79-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4be79-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4be79-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4be79-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4be79-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4be79-111">Attributes</span></span>  
  
|<span data-ttu-id="4be79-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4be79-112">Attribute</span></span>|<span data-ttu-id="4be79-113">描述</span><span class="sxs-lookup"><span data-stu-id="4be79-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="4be79-114">布林值，指定是否啟用封包路由。</span><span class="sxs-lookup"><span data-stu-id="4be79-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="4be79-115">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4be79-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="4be79-116">整數，指定可接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="4be79-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4be79-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4be79-117">Child Elements</span></span>  
  
|<span data-ttu-id="4be79-118">項目</span><span class="sxs-lookup"><span data-stu-id="4be79-118">Element</span></span>|<span data-ttu-id="4be79-119">描述</span><span class="sxs-lookup"><span data-stu-id="4be79-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4be79-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="4be79-120">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="4be79-121"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 物件，包含目前通道的通道集區的屬性。</span><span class="sxs-lookup"><span data-stu-id="4be79-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4be79-122">父項目</span><span class="sxs-lookup"><span data-stu-id="4be79-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4be79-123">項目</span><span class="sxs-lookup"><span data-stu-id="4be79-123">Element</span></span>|<span data-ttu-id="4be79-124">描述</span><span class="sxs-lookup"><span data-stu-id="4be79-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4be79-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="4be79-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4be79-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="4be79-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4be79-127">備註</span><span class="sxs-lookup"><span data-stu-id="4be79-127">Remarks</span></span>  
 <span data-ttu-id="4be79-128">如果要啟用封包路由，便需要這個項目提供的單向轉換層。</span><span class="sxs-lookup"><span data-stu-id="4be79-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="4be79-129">使用者可以建立自訂繫結，將這個繫結置於工作階段感知或要求-回覆傳輸層上，讓它啟用路由傳送封包功能。</span><span class="sxs-lookup"><span data-stu-id="4be79-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="4be79-130">當您要以較原始的方式來公開單向方法時，也可以使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="4be79-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="4be79-131">還有其他轉換可套用至這一層，例如複合雙工和可信賴傳訊。</span><span class="sxs-lookup"><span data-stu-id="4be79-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be79-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4be79-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4be79-133">繫結</span><span class="sxs-lookup"><span data-stu-id="4be79-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4be79-134">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="4be79-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4be79-135">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="4be79-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4be79-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4be79-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
