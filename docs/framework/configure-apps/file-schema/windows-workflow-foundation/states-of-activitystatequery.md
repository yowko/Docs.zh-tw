---
title: "&lt;activityStateQuery&gt; 的 &lt;states&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26e9901ce8b8c41f2386a8fda696ed03e08154de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltstatesgt-of-ltactivitystatequerygt"></a><span data-ttu-id="b9ce6-102">&lt;activityStateQuery&gt; 的 &lt;states&gt;</span><span class="sxs-lookup"><span data-stu-id="b9ce6-102">&lt;states&gt; of &lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="b9ce6-103">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="b9ce6-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b9ce6-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b9ce6-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-106">\<tracking></span></span>  
<span data-ttu-id="b9ce6-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-107">\<trackingProfile></span></span>  
<span data-ttu-id="b9ce6-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-108">\<workflow></span></span>  
<span data-ttu-id="b9ce6-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-109">\<activityStateQueries></span></span>  
<span data-ttu-id="b9ce6-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-110">\<activityStateQuery></span></span>  
<span data-ttu-id="b9ce6-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ce6-112">語法</span><span class="sxs-lookup"><span data-stu-id="b9ce6-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9ce6-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b9ce6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b9ce6-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9ce6-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b9ce6-115">Attributes</span></span>  
 <span data-ttu-id="b9ce6-116">無。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b9ce6-117">子元素</span><span class="sxs-lookup"><span data-stu-id="b9ce6-117">Child Elements</span></span>  
  
|<span data-ttu-id="b9ce6-118">項目</span><span class="sxs-lookup"><span data-stu-id="b9ce6-118">Element</span></span>|<span data-ttu-id="b9ce6-119">描述</span><span class="sxs-lookup"><span data-stu-id="b9ce6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9ce6-120">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="b9ce6-121">組態項目，其中包含追蹤記錄應發出之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9ce6-122">父項目</span><span class="sxs-lookup"><span data-stu-id="b9ce6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b9ce6-123">項目</span><span class="sxs-lookup"><span data-stu-id="b9ce6-123">Element</span></span>|<span data-ttu-id="b9ce6-124">描述</span><span class="sxs-lookup"><span data-stu-id="b9ce6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9ce6-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="b9ce6-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="b9ce6-126">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b9ce6-127">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9ce6-128">備註</span><span class="sxs-lookup"><span data-stu-id="b9ce6-128">Remarks</span></span>  
 <span data-ttu-id="b9ce6-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b9ce6-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b9ce6-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b9ce6-132">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ce6-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9ce6-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9ce6-133">See Also</span></span>  
 <span data-ttu-id="b9ce6-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b9ce6-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="b9ce6-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b9ce6-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b9ce6-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b9ce6-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b9ce6-137">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b9ce6-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
