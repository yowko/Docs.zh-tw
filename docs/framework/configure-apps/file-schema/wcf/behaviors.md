---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a87966f643fe46d0ef69f843dc306151ca7c18bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400586"
---
# <a name="behaviors"></a><span data-ttu-id="62242-101">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="62242-101">\<behaviors></span></span>
<span data-ttu-id="62242-102">這個項目會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="62242-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="62242-103">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="62242-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="62242-104">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="62242-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="62242-105">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="62242-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="62242-106">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="62242-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="62242-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62242-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62242-108">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62242-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62242-109">&nbsp;&nbsp;&nbsp;&nbsp; **\<行為 >**</span><span class="sxs-lookup"><span data-stu-id="62242-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62242-110">語法</span><span class="sxs-lookup"><span data-stu-id="62242-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62242-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62242-111">Attributes and Elements</span></span>  
 <span data-ttu-id="62242-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="62242-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62242-113">屬性</span><span class="sxs-lookup"><span data-stu-id="62242-113">Attributes</span></span>  
 <span data-ttu-id="62242-114">None</span><span class="sxs-lookup"><span data-stu-id="62242-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62242-115">子元素</span><span class="sxs-lookup"><span data-stu-id="62242-115">Child Elements</span></span>  
  
|<span data-ttu-id="62242-116">項目</span><span class="sxs-lookup"><span data-stu-id="62242-116">Element</span></span>|<span data-ttu-id="62242-117">描述</span><span class="sxs-lookup"><span data-stu-id="62242-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62242-118">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="62242-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="62242-119">這個組態區段表示為特定端點定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="62242-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="62242-120">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="62242-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="62242-121">這個組態區段表示為特定服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="62242-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62242-122">父項目</span><span class="sxs-lookup"><span data-stu-id="62242-122">Parent Elements</span></span>  
  
|<span data-ttu-id="62242-123">項目</span><span class="sxs-lookup"><span data-stu-id="62242-123">Element</span></span>|<span data-ttu-id="62242-124">描述</span><span class="sxs-lookup"><span data-stu-id="62242-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62242-125">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="62242-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="62242-126">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="62242-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62242-127">備註</span><span class="sxs-lookup"><span data-stu-id="62242-127">Remarks</span></span>  
 <span data-ttu-id="62242-128">您可以使用 `<remove>` 項目移除集合中的特定行為。</span><span class="sxs-lookup"><span data-stu-id="62242-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="62242-129">若要這麼做，只需在 `name` 項目的 `<remove>` 屬性中提供要移除之行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="62242-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="62242-130">您也可以使用 `<clear>` 項目來清除行為集合的所有內容，確保該行為集合在啟始時就是空的。</span><span class="sxs-lookup"><span data-stu-id="62242-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62242-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62242-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="62242-132">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="62242-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="62242-133">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="62242-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="62242-134">指定用端執行階段行為</span><span class="sxs-lookup"><span data-stu-id="62242-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="62242-135">指定服務執行階段行為</span><span class="sxs-lookup"><span data-stu-id="62242-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="62242-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="62242-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
