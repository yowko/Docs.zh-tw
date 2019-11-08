---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738784"
---
# <a name="oneway"></a><span data-ttu-id="a1a1a-101">\<單向 ></span><span class="sxs-lookup"><span data-stu-id="a1a1a-101">\<oneWay></span></span>
<span data-ttu-id="a1a1a-102">針對自訂繫結啟用封包路由和使用單向方法。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="a1a1a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a1a1a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a1a1a-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a1a1a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a1a1a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="a1a1a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a1a1a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a1a1a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a1a1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="a1a1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a1a1a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<單向 >**</span><span class="sxs-lookup"><span data-stu-id="a1a1a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a1a-109">語法</span><span class="sxs-lookup"><span data-stu-id="a1a1a-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1a1a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a1a1a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a1a1a-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1a1a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a1a1a-112">Attributes</span></span>  
  
|<span data-ttu-id="a1a1a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a1a1a-113">Attribute</span></span>|<span data-ttu-id="a1a1a-114">描述</span><span class="sxs-lookup"><span data-stu-id="a1a1a-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="a1a1a-115">布林值，指定是否啟用封包路由。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="a1a1a-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="a1a1a-117">整數，指定可接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1a1a-118">子項目</span><span class="sxs-lookup"><span data-stu-id="a1a1a-118">Child Elements</span></span>  
  
|<span data-ttu-id="a1a1a-119">項目</span><span class="sxs-lookup"><span data-stu-id="a1a1a-119">Element</span></span>|<span data-ttu-id="a1a1a-120">描述</span><span class="sxs-lookup"><span data-stu-id="a1a1a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1a1a-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="a1a1a-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="a1a1a-122"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 物件，包含目前通道的通道集區的屬性。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1a1a-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a1a1a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a1a1a-124">項目</span><span class="sxs-lookup"><span data-stu-id="a1a1a-124">Element</span></span>|<span data-ttu-id="a1a1a-125">描述</span><span class="sxs-lookup"><span data-stu-id="a1a1a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1a1a-126">\<binding ></span><span class="sxs-lookup"><span data-stu-id="a1a1a-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="a1a1a-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1a1a-128">備註</span><span class="sxs-lookup"><span data-stu-id="a1a1a-128">Remarks</span></span>  
 <span data-ttu-id="a1a1a-129">如果要啟用封包路由，便需要這個項目提供的單向轉換層。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="a1a1a-130">使用者可以建立自訂繫結，將這個繫結置於工作階段感知或要求-回覆傳輸層上，讓它啟用路由傳送封包功能。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="a1a1a-131">當您要以較原始的方式來公開單向方法時，也可以使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="a1a1a-132">還有其他轉換可套用至這一層，例如複合雙工和可信賴傳訊。</span><span class="sxs-lookup"><span data-stu-id="a1a1a-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a1a-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a1a-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a1a1a-134">繫結</span><span class="sxs-lookup"><span data-stu-id="a1a1a-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a1a1a-135">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a1a1a-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a1a1a-136">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a1a1a-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a1a1a-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a1a1a-137">\<customBinding></span></span>](custombinding.md)
