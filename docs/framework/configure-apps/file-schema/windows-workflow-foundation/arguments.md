---
title: "&lt;引數&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b0cb0f132b21a419b0a173df169fbbd65673d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltargumentsgt"></a><span data-ttu-id="ed121-102">&lt;引數&gt;</span><span class="sxs-lookup"><span data-stu-id="ed121-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="ed121-103">表示與某個活動狀態查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="ed121-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="ed121-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ed121-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ed121-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ed121-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ed121-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="ed121-106">\<tracking></span></span>  
<span data-ttu-id="ed121-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ed121-107">\<trackingProfile></span></span>  
<span data-ttu-id="ed121-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ed121-108">\<workflow></span></span>  
<span data-ttu-id="ed121-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ed121-109">\<activityStateQueries></span></span>  
<span data-ttu-id="ed121-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ed121-110">\<activityStateQuery></span></span>  
<span data-ttu-id="ed121-111">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="ed121-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed121-112">語法</span><span class="sxs-lookup"><span data-stu-id="ed121-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed121-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ed121-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ed121-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ed121-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed121-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ed121-115">Attributes</span></span>  
 <span data-ttu-id="ed121-116">無。</span><span class="sxs-lookup"><span data-stu-id="ed121-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ed121-117">子項目</span><span class="sxs-lookup"><span data-stu-id="ed121-117">Child Elements</span></span>  
  
|<span data-ttu-id="ed121-118">項目</span><span class="sxs-lookup"><span data-stu-id="ed121-118">Element</span></span>|<span data-ttu-id="ed121-119">說明</span><span class="sxs-lookup"><span data-stu-id="ed121-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed121-120">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="ed121-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="ed121-121">與活動狀態查詢相關聯的引數。</span><span class="sxs-lookup"><span data-stu-id="ed121-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed121-122">父項目</span><span class="sxs-lookup"><span data-stu-id="ed121-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ed121-123">項目</span><span class="sxs-lookup"><span data-stu-id="ed121-123">Element</span></span>|<span data-ttu-id="ed121-124">說明</span><span class="sxs-lookup"><span data-stu-id="ed121-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed121-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ed121-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="ed121-126">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="ed121-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ed121-127">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="ed121-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed121-128">備註</span><span class="sxs-lookup"><span data-stu-id="ed121-128">Remarks</span></span>  
 <span data-ttu-id="ed121-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="ed121-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ed121-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="ed121-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ed121-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ed121-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ed121-132">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="ed121-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed121-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed121-133">See Also</span></span>  
 <span data-ttu-id="ed121-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ed121-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ed121-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ed121-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ed121-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ed121-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ed121-137">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ed121-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
