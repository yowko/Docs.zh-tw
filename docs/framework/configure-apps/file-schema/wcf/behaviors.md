---
title: "&lt;行為&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f543742ee4d70f64d3bef64be295a7f353c680d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="a7ca7-102">&lt;行為&gt;</span><span class="sxs-lookup"><span data-stu-id="a7ca7-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="a7ca7-103">這個項目會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="a7ca7-104">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="a7ca7-105">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="a7ca7-106">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a7ca7-107">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="a7ca7-108">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a7ca7-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ca7-109">語法</span><span class="sxs-lookup"><span data-stu-id="a7ca7-109">Syntax</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7ca7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7ca7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7ca7-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7ca7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a7ca7-112">Attributes</span></span>  
 <span data-ttu-id="a7ca7-113">無</span><span class="sxs-lookup"><span data-stu-id="a7ca7-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7ca7-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a7ca7-114">Child Elements</span></span>  
  
|<span data-ttu-id="a7ca7-115">項目</span><span class="sxs-lookup"><span data-stu-id="a7ca7-115">Element</span></span>|<span data-ttu-id="a7ca7-116">說明</span><span class="sxs-lookup"><span data-stu-id="a7ca7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7ca7-117">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a7ca7-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="a7ca7-118">這個組態區段表示為特定端點定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="a7ca7-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a7ca7-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="a7ca7-120">這個組態區段表示為特定服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7ca7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a7ca7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a7ca7-122">項目</span><span class="sxs-lookup"><span data-stu-id="a7ca7-122">Element</span></span>|<span data-ttu-id="a7ca7-123">說明</span><span class="sxs-lookup"><span data-stu-id="a7ca7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7ca7-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a7ca7-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="a7ca7-125">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7ca7-126">備註</span><span class="sxs-lookup"><span data-stu-id="a7ca7-126">Remarks</span></span>  
 <span data-ttu-id="a7ca7-127">您可以使用 `<remove>` 項目移除集合中的特定行為。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="a7ca7-128">若要這麼做，只需在 `name` 項目的 `<remove>` 屬性中提供要移除之行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="a7ca7-129">您也可以使用 `<clear>` 項目來清除行為集合的所有內容，確保該行為集合在啟始時就是空的。</span><span class="sxs-lookup"><span data-stu-id="a7ca7-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ca7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7ca7-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="a7ca7-131">設定與擴充執行階段行為</span><span class="sxs-lookup"><span data-stu-id="a7ca7-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [<span data-ttu-id="a7ca7-132">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="a7ca7-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="a7ca7-133">指定用端執行階段行為</span><span class="sxs-lookup"><span data-stu-id="a7ca7-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="a7ca7-134">指定服務執行階段行為</span><span class="sxs-lookup"><span data-stu-id="a7ca7-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [<span data-ttu-id="a7ca7-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a7ca7-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
