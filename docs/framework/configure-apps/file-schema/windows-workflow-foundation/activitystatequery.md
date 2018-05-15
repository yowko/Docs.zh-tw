---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 8f9f30cf16e18eec6f076a41474a1935feeb3460
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="37308-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="37308-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="37308-103">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="37308-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="37308-104">比方說，您可能想要追蹤的每一次 「 傳送電子郵件 」 活動完成的工作流程執行個體中。</span><span class="sxs-lookup"><span data-stu-id="37308-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="37308-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="37308-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="37308-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="37308-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="37308-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="37308-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="37308-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37308-108">\<system.serviceModel></span></span>  
<span data-ttu-id="37308-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="37308-109">\<tracking></span></span>  
<span data-ttu-id="37308-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="37308-110">\<trackingProfile></span></span>  
<span data-ttu-id="37308-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="37308-111">\<workflow></span></span>  
<span data-ttu-id="37308-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="37308-112">\<activityStateQueries></span></span>  
<span data-ttu-id="37308-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="37308-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37308-114">語法</span><span class="sxs-lookup"><span data-stu-id="37308-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37308-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="37308-115">Attributes and Elements</span></span>  
 <span data-ttu-id="37308-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="37308-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37308-117">屬性</span><span class="sxs-lookup"><span data-stu-id="37308-117">Attributes</span></span>  
  
|<span data-ttu-id="37308-118">屬性</span><span class="sxs-lookup"><span data-stu-id="37308-118">Attribute</span></span>|<span data-ttu-id="37308-119">描述</span><span class="sxs-lookup"><span data-stu-id="37308-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37308-120">activityName</span><span class="sxs-lookup"><span data-stu-id="37308-120">activityName</span></span>|<span data-ttu-id="37308-121">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="37308-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37308-122">子項目</span><span class="sxs-lookup"><span data-stu-id="37308-122">Child Elements</span></span>  
  
|<span data-ttu-id="37308-123">項目</span><span class="sxs-lookup"><span data-stu-id="37308-123">Element</span></span>|<span data-ttu-id="37308-124">描述</span><span class="sxs-lookup"><span data-stu-id="37308-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37308-125">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="37308-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="37308-126">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="37308-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="37308-127">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="37308-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="37308-128">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="37308-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="37308-129">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="37308-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="37308-130">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="37308-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37308-131">父項目</span><span class="sxs-lookup"><span data-stu-id="37308-131">Parent Elements</span></span>  
  
|<span data-ttu-id="37308-132">項目</span><span class="sxs-lookup"><span data-stu-id="37308-132">Element</span></span>|<span data-ttu-id="37308-133">描述</span><span class="sxs-lookup"><span data-stu-id="37308-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37308-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="37308-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="37308-135">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="37308-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="37308-136">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="37308-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37308-137">備註</span><span class="sxs-lookup"><span data-stu-id="37308-137">Remarks</span></span>  
 <span data-ttu-id="37308-138">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="37308-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="37308-139">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="37308-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="37308-140">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="37308-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="37308-141">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="37308-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37308-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37308-142">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="37308-143">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="37308-143">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="37308-144">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="37308-144">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
