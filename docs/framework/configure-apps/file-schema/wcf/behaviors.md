---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701225"
---
# <a name="behaviors"></a><span data-ttu-id="a5fb5-101">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="a5fb5-101">\<behaviors></span></span>
<span data-ttu-id="a5fb5-102">這個項目會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="a5fb5-103">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="a5fb5-104">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="a5fb5-105">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a5fb5-106">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="a5fb5-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a5fb5-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fb5-108">語法</span><span class="sxs-lookup"><span data-stu-id="a5fb5-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5fb5-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a5fb5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a5fb5-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5fb5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a5fb5-111">Attributes</span></span>  
 <span data-ttu-id="a5fb5-112">None</span><span class="sxs-lookup"><span data-stu-id="a5fb5-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5fb5-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a5fb5-113">Child Elements</span></span>  
  
|<span data-ttu-id="a5fb5-114">項目</span><span class="sxs-lookup"><span data-stu-id="a5fb5-114">Element</span></span>|<span data-ttu-id="a5fb5-115">描述</span><span class="sxs-lookup"><span data-stu-id="a5fb5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5fb5-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a5fb5-116">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="a5fb5-117">這個組態區段表示為特定端點定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="a5fb5-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a5fb5-118">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="a5fb5-119">這個組態區段表示為特定服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5fb5-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a5fb5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a5fb5-121">項目</span><span class="sxs-lookup"><span data-stu-id="a5fb5-121">Element</span></span>|<span data-ttu-id="a5fb5-122">描述</span><span class="sxs-lookup"><span data-stu-id="a5fb5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5fb5-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a5fb5-123">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="a5fb5-124">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5fb5-125">備註</span><span class="sxs-lookup"><span data-stu-id="a5fb5-125">Remarks</span></span>  
 <span data-ttu-id="a5fb5-126">您可以使用 `<remove>` 項目移除集合中的特定行為。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="a5fb5-127">若要這麼做，只需在 `name` 項目的 `<remove>` 屬性中提供要移除之行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="a5fb5-128">您也可以使用 `<clear>` 項目來清除行為集合的所有內容，確保該行為集合在啟始時就是空的。</span><span class="sxs-lookup"><span data-stu-id="a5fb5-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fb5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5fb5-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="a5fb5-130">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="a5fb5-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="a5fb5-131">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="a5fb5-131">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="a5fb5-132">指定用端執行階段行為</span><span class="sxs-lookup"><span data-stu-id="a5fb5-132">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="a5fb5-133">指定服務執行階段行為</span><span class="sxs-lookup"><span data-stu-id="a5fb5-133">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="a5fb5-134">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a5fb5-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
