---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50dc2c4c5d4c1517d6ac3409dc4d932f67cbeb8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="f10da-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="f10da-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="f10da-103">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="f10da-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f10da-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="f10da-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f10da-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="f10da-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f10da-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="f10da-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="f10da-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="f10da-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f10da-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f10da-108">\<system.serviceModel></span></span>  
<span data-ttu-id="f10da-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="f10da-109">\<tracking></span></span>  
<span data-ttu-id="f10da-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f10da-110">\<trackingProfile></span></span>  
<span data-ttu-id="f10da-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="f10da-111">\<workflow></span></span>  
<span data-ttu-id="f10da-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="f10da-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="f10da-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="f10da-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f10da-114">語法</span><span class="sxs-lookup"><span data-stu-id="f10da-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f10da-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f10da-115">Attributes and Elements</span></span>  
 <span data-ttu-id="f10da-116">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f10da-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f10da-117">屬性</span><span class="sxs-lookup"><span data-stu-id="f10da-117">Attributes</span></span>  
  
|<span data-ttu-id="f10da-118">屬性</span><span class="sxs-lookup"><span data-stu-id="f10da-118">Attribute</span></span>|<span data-ttu-id="f10da-119">描述</span><span class="sxs-lookup"><span data-stu-id="f10da-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f10da-120">activityName</span><span class="sxs-lookup"><span data-stu-id="f10da-120">activityName</span></span>|<span data-ttu-id="f10da-121">字串，可指定傳用錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="f10da-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="f10da-122">預設為 *，表示會針對所有活動傳回錯誤傳用記錄。</span><span class="sxs-lookup"><span data-stu-id="f10da-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="f10da-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="f10da-123">faultHandlerActivityName</span></span>|<span data-ttu-id="f10da-124">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="f10da-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f10da-125">子元素</span><span class="sxs-lookup"><span data-stu-id="f10da-125">Child Elements</span></span>  
 <span data-ttu-id="f10da-126">無。</span><span class="sxs-lookup"><span data-stu-id="f10da-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f10da-127">父項目</span><span class="sxs-lookup"><span data-stu-id="f10da-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f10da-128">項目</span><span class="sxs-lookup"><span data-stu-id="f10da-128">Element</span></span>|<span data-ttu-id="f10da-129">說明</span><span class="sxs-lookup"><span data-stu-id="f10da-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f10da-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="f10da-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="f10da-131">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="f10da-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f10da-132">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="f10da-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f10da-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f10da-133">See Also</span></span>  
 <span data-ttu-id="f10da-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f10da-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f10da-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f10da-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f10da-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="f10da-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f10da-137">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="f10da-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
