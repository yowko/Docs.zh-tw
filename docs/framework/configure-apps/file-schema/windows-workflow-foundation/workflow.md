---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151854"
---
# <a name="workflow"></a><span data-ttu-id="32e2d-101">\<工作流></span><span class="sxs-lookup"><span data-stu-id="32e2d-101">\<workflow></span></span>
<span data-ttu-id="32e2d-102">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="32e2d-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="32e2d-103">有關工作流跟蹤及其配置的詳細資訊，請參閱[工作流跟蹤和跟蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="32e2d-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="32e2d-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="32e2d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="32e2d-105">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="32e2d-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="32e2d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="32e2d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="32e2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="32e2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="32e2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<工作流>**</span><span class="sxs-lookup"><span data-stu-id="32e2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e2d-109">語法</span><span class="sxs-lookup"><span data-stu-id="32e2d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32e2d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32e2d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32e2d-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="32e2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32e2d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="32e2d-112">Attributes</span></span>  
  
|<span data-ttu-id="32e2d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="32e2d-113">Attribute</span></span>|<span data-ttu-id="32e2d-114">描述</span><span class="sxs-lookup"><span data-stu-id="32e2d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32e2d-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="32e2d-115">activityDefinitionId</span></span>|<span data-ttu-id="32e2d-116">指定工作流程之活動定義識別碼的字串，該工作流程正在進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="32e2d-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32e2d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="32e2d-117">Child Elements</span></span>  
  
|<span data-ttu-id="32e2d-118">元素</span><span class="sxs-lookup"><span data-stu-id="32e2d-118">Element</span></span>|<span data-ttu-id="32e2d-119">描述</span><span class="sxs-lookup"><span data-stu-id="32e2d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32e2d-120">\<活動 計畫查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-120">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="32e2d-121">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="32e2d-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="32e2d-122">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="32e2d-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="32e2d-123">\<活動 狀態查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-123">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="32e2d-124">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="32e2d-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="32e2d-125">例如，您可能希望跟蹤工作流實例中每次完成"發送電子郵件"活動的時間。</span><span class="sxs-lookup"><span data-stu-id="32e2d-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="32e2d-126">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="32e2d-127">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="32e2d-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="32e2d-128">\<書簽 恢復查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-128">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="32e2d-129">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="32e2d-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="32e2d-130">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="32e2d-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="32e2d-131">\<取消請求查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-131">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="32e2d-132">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="32e2d-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="32e2d-133">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="32e2d-134">\<自訂跟蹤查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-134">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="32e2d-135">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="32e2d-136">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="32e2d-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="32e2d-137">\<故障傳播查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-137">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="32e2d-138">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="32e2d-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="32e2d-139">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="32e2d-140">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="32e2d-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="32e2d-141">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="32e2d-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="32e2d-142">\<工作流實例查詢></span><span class="sxs-lookup"><span data-stu-id="32e2d-142">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="32e2d-143">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32e2d-144">父項目</span><span class="sxs-lookup"><span data-stu-id="32e2d-144">Parent Elements</span></span>  
  
|<span data-ttu-id="32e2d-145">元素</span><span class="sxs-lookup"><span data-stu-id="32e2d-145">Element</span></span>|<span data-ttu-id="32e2d-146">描述</span><span class="sxs-lookup"><span data-stu-id="32e2d-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32e2d-147">\<跟蹤設定檔></span><span class="sxs-lookup"><span data-stu-id="32e2d-147">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="32e2d-148">代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="32e2d-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="32e2d-149">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="32e2d-150">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="32e2d-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32e2d-151">備註</span><span class="sxs-lookup"><span data-stu-id="32e2d-151">Remarks</span></span>  
 <span data-ttu-id="32e2d-152">追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱特定工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="32e2d-153">這個設定項目會識別正在追蹤的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="32e2d-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="32e2d-154">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="32e2d-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="32e2d-155">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="32e2d-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="32e2d-156">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="32e2d-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="32e2d-157">您可以使用多種查詢型別訂閱不同類別的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="32e2d-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="32e2d-158">有關查詢的完整清單，請參閱本主題的子項目清單和[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="32e2d-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="32e2d-159">下面的示例顯示設定檔中的跟蹤設定檔，該設定檔允許追蹤參與者訂閱 和`Started``Completed`工作流事件。</span><span class="sxs-lookup"><span data-stu-id="32e2d-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32e2d-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32e2d-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="32e2d-161">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="32e2d-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="32e2d-162">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="32e2d-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
