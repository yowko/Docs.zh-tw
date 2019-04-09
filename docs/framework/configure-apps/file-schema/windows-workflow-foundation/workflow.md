---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: d6c23bb0b819b5f22367a93db0dec64787449664
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136172"
---
# <a name="workflow"></a><span data-ttu-id="a5bea-101">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a5bea-101">\<workflow></span></span>
<span data-ttu-id="a5bea-102">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="a5bea-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a5bea-103">如需在工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)並[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a5bea-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a5bea-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a5bea-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a5bea-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="a5bea-105">\<tracking></span></span>  
<span data-ttu-id="a5bea-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a5bea-106">\<trackingProfile></span></span>  
<span data-ttu-id="a5bea-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a5bea-107">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5bea-108">語法</span><span class="sxs-lookup"><span data-stu-id="a5bea-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5bea-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a5bea-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a5bea-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a5bea-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5bea-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a5bea-111">Attributes</span></span>  
  
|<span data-ttu-id="a5bea-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a5bea-112">Attribute</span></span>|<span data-ttu-id="a5bea-113">描述</span><span class="sxs-lookup"><span data-stu-id="a5bea-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5bea-114">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="a5bea-114">activityDefinitionId</span></span>|<span data-ttu-id="a5bea-115">指定工作流程之活動定義識別碼的字串，該工作流程正在進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="a5bea-115">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5bea-116">子元素</span><span class="sxs-lookup"><span data-stu-id="a5bea-116">Child Elements</span></span>  
  
|<span data-ttu-id="a5bea-117">項目</span><span class="sxs-lookup"><span data-stu-id="a5bea-117">Element</span></span>|<span data-ttu-id="a5bea-118">描述</span><span class="sxs-lookup"><span data-stu-id="a5bea-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5bea-119">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-119">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="a5bea-120">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a5bea-120">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a5bea-121">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="a5bea-121">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="a5bea-122">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-122">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="a5bea-123">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a5bea-123">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a5bea-124">例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。</span><span class="sxs-lookup"><span data-stu-id="a5bea-124">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a5bea-125">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-125">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a5bea-126">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="a5bea-126">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="a5bea-127">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-127">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="a5bea-128">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="a5bea-128">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a5bea-129">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="a5bea-129">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="a5bea-130">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-130">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="a5bea-131">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="a5bea-131">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a5bea-132">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-132">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="a5bea-133">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-133">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="a5bea-134">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-134">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a5bea-135">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a5bea-135">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="a5bea-136">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-136">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="a5bea-137">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="a5bea-137">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a5bea-138">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-138">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a5bea-139">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a5bea-139">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a5bea-140">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="a5bea-140">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="a5bea-141">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="a5bea-141">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="a5bea-142">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-142">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5bea-143">父項目</span><span class="sxs-lookup"><span data-stu-id="a5bea-143">Parent Elements</span></span>  
  
|<span data-ttu-id="a5bea-144">項目</span><span class="sxs-lookup"><span data-stu-id="a5bea-144">Element</span></span>|<span data-ttu-id="a5bea-145">描述</span><span class="sxs-lookup"><span data-stu-id="a5bea-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5bea-146">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a5bea-146">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="a5bea-147">表示組態區段，用於建立工作流程追蹤記錄中追蹤參與者的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="a5bea-147">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="a5bea-148">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-148">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="a5bea-149">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="a5bea-149">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5bea-150">備註</span><span class="sxs-lookup"><span data-stu-id="a5bea-150">Remarks</span></span>  
 <span data-ttu-id="a5bea-151">追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱特定工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-151">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="a5bea-152">這個設定項目會識別正在追蹤的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a5bea-152">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="a5bea-153">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="a5bea-153">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="a5bea-154">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="a5bea-154">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="a5bea-155">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="a5bea-155">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="a5bea-156">有多種查詢型別訂閱不同類別的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a5bea-156">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="a5bea-157">查詢的完整清單，請參閱本主題的子項目清單和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a5bea-157">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="a5bea-158">下列範例顯示的追蹤設定檔中的組態檔，可允許追蹤參與者訂閱`Started`和`Completed`工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="a5bea-158">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5bea-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5bea-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="a5bea-160">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="a5bea-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5bea-161">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a5bea-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
