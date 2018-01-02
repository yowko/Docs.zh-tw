---
title: '&lt;oneWay&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1436bc0c1708649378ec6747aed9c23cfc1744dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="a19b8-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="a19b8-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="a19b8-103">針對自訂繫結啟用封包路由和使用單向方法。</span><span class="sxs-lookup"><span data-stu-id="a19b8-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="a19b8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a19b8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a19b8-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a19b8-105">\<bindings></span></span>  
<span data-ttu-id="a19b8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a19b8-106">\<customBinding></span></span>  
<span data-ttu-id="a19b8-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a19b8-107">\<binding></span></span>  
<span data-ttu-id="a19b8-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="a19b8-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a19b8-109">語法</span><span class="sxs-lookup"><span data-stu-id="a19b8-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a19b8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a19b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a19b8-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a19b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a19b8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a19b8-112">Attributes</span></span>  
  
|<span data-ttu-id="a19b8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a19b8-113">Attribute</span></span>|<span data-ttu-id="a19b8-114">描述</span><span class="sxs-lookup"><span data-stu-id="a19b8-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="a19b8-115">布林值，指定是否啟用封包路由。</span><span class="sxs-lookup"><span data-stu-id="a19b8-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="a19b8-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a19b8-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="a19b8-117">整數，指定可接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="a19b8-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a19b8-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a19b8-118">Child Elements</span></span>  
  
|<span data-ttu-id="a19b8-119">項目</span><span class="sxs-lookup"><span data-stu-id="a19b8-119">Element</span></span>|<span data-ttu-id="a19b8-120">描述</span><span class="sxs-lookup"><span data-stu-id="a19b8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a19b8-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="a19b8-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="a19b8-122"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 物件，包含目前通道的通道集區的屬性。</span><span class="sxs-lookup"><span data-stu-id="a19b8-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a19b8-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a19b8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a19b8-124">項目</span><span class="sxs-lookup"><span data-stu-id="a19b8-124">Element</span></span>|<span data-ttu-id="a19b8-125">描述</span><span class="sxs-lookup"><span data-stu-id="a19b8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a19b8-126">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a19b8-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a19b8-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="a19b8-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a19b8-128">備註</span><span class="sxs-lookup"><span data-stu-id="a19b8-128">Remarks</span></span>  
 <span data-ttu-id="a19b8-129">如果要啟用封包路由，便需要這個項目提供的單向轉換層。</span><span class="sxs-lookup"><span data-stu-id="a19b8-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="a19b8-130">使用者可以建立自訂繫結，將這個繫結置於工作階段感知或要求-回覆傳輸層上，讓它啟用路由傳送封包功能。</span><span class="sxs-lookup"><span data-stu-id="a19b8-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="a19b8-131">當您要以較原始的方式來公開單向方法時，也可以使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="a19b8-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="a19b8-132">還有其他轉換可套用至這一層，例如複合雙工和可信賴傳訊。</span><span class="sxs-lookup"><span data-stu-id="a19b8-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19b8-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="a19b8-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a19b8-134">繫結</span><span class="sxs-lookup"><span data-stu-id="a19b8-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a19b8-135">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a19b8-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a19b8-136">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a19b8-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a19b8-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a19b8-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
