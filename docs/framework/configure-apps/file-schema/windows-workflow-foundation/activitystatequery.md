---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 7b872d933d07af329601063b3d769bc43a22007c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568669"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="73d97-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="73d97-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="73d97-103">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="73d97-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="73d97-104">例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。</span><span class="sxs-lookup"><span data-stu-id="73d97-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="73d97-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="73d97-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="73d97-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="73d97-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="73d97-107">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="73d97-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="73d97-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="73d97-108">\<system.serviceModel></span></span>  
<span data-ttu-id="73d97-109">\<tracking></span><span class="sxs-lookup"><span data-stu-id="73d97-109">\<tracking></span></span>  
<span data-ttu-id="73d97-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="73d97-110">\<trackingProfile></span></span>  
<span data-ttu-id="73d97-111">\<workflow></span><span class="sxs-lookup"><span data-stu-id="73d97-111">\<workflow></span></span>  
<span data-ttu-id="73d97-112">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="73d97-112">\<activityStateQueries></span></span>  
<span data-ttu-id="73d97-113">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="73d97-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d97-114">語法</span><span class="sxs-lookup"><span data-stu-id="73d97-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73d97-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73d97-115">Attributes and Elements</span></span>  
 <span data-ttu-id="73d97-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73d97-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73d97-117">屬性</span><span class="sxs-lookup"><span data-stu-id="73d97-117">Attributes</span></span>  
  
|<span data-ttu-id="73d97-118">屬性</span><span class="sxs-lookup"><span data-stu-id="73d97-118">Attribute</span></span>|<span data-ttu-id="73d97-119">描述</span><span class="sxs-lookup"><span data-stu-id="73d97-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73d97-120">activityName</span><span class="sxs-lookup"><span data-stu-id="73d97-120">activityName</span></span>|<span data-ttu-id="73d97-121">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="73d97-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73d97-122">子元素</span><span class="sxs-lookup"><span data-stu-id="73d97-122">Child Elements</span></span>  
  
|<span data-ttu-id="73d97-123">項目</span><span class="sxs-lookup"><span data-stu-id="73d97-123">Element</span></span>|<span data-ttu-id="73d97-124">描述</span><span class="sxs-lookup"><span data-stu-id="73d97-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73d97-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="73d97-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="73d97-126">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="73d97-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="73d97-127">\<states></span><span class="sxs-lookup"><span data-stu-id="73d97-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="73d97-128">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="73d97-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="73d97-129">\<states></span><span class="sxs-lookup"><span data-stu-id="73d97-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="73d97-130">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="73d97-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73d97-131">父項目</span><span class="sxs-lookup"><span data-stu-id="73d97-131">Parent Elements</span></span>  
  
|<span data-ttu-id="73d97-132">項目</span><span class="sxs-lookup"><span data-stu-id="73d97-132">Element</span></span>|<span data-ttu-id="73d97-133">描述</span><span class="sxs-lookup"><span data-stu-id="73d97-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73d97-134">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="73d97-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="73d97-135">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="73d97-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="73d97-136">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="73d97-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73d97-137">備註</span><span class="sxs-lookup"><span data-stu-id="73d97-137">Remarks</span></span>  
 <span data-ttu-id="73d97-138">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="73d97-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="73d97-139">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="73d97-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="73d97-140">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="73d97-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="73d97-141">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="73d97-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="73d97-142">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="73d97-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73d97-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73d97-143">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="73d97-144">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="73d97-144">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="73d97-145">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="73d97-145">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
