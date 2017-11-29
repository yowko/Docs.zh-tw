---
title: "&lt;工作流程&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55347764e9aa685879eb233793490206c68bf570
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowgt"></a><span data-ttu-id="ac51f-102">&lt;工作流程&gt;</span><span class="sxs-lookup"><span data-stu-id="ac51f-102">&lt;workflow&gt;</span></span>
<span data-ttu-id="ac51f-103">包含所有的查詢所識別的特定工作流程的組態項目**超連結"http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid (VS.100).aspx"ctivityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="ac51f-103">A configuration element that contains all queries for a specific workflow identified by the **a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId** property.</span></span>  
  
 <span data-ttu-id="ac51f-104">如需工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ac51f-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ac51f-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ac51f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ac51f-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="ac51f-106">\<tracking></span></span>  
<span data-ttu-id="ac51f-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ac51f-107">\<trackingProfile></span></span>  
<span data-ttu-id="ac51f-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ac51f-108">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac51f-109">語法</span><span class="sxs-lookup"><span data-stu-id="ac51f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac51f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ac51f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ac51f-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ac51f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac51f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ac51f-112">Attributes</span></span>  
  
|<span data-ttu-id="ac51f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ac51f-113">Attribute</span></span>|<span data-ttu-id="ac51f-114">描述</span><span class="sxs-lookup"><span data-stu-id="ac51f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac51f-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="ac51f-115">activityDefinitionId</span></span>|<span data-ttu-id="ac51f-116">指定工作流程之活動定義識別碼的字串，該工作流程正在進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="ac51f-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac51f-117">子元素</span><span class="sxs-lookup"><span data-stu-id="ac51f-117">Child Elements</span></span>  
  
|<span data-ttu-id="ac51f-118">項目</span><span class="sxs-lookup"><span data-stu-id="ac51f-118">Element</span></span>|<span data-ttu-id="ac51f-119">說明</span><span class="sxs-lookup"><span data-stu-id="ac51f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac51f-120">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-120">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="ac51f-121">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="ac51f-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ac51f-122">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="ac51f-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="ac51f-123">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-123">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="ac51f-124">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac51f-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ac51f-125">比方說，您可能想要追蹤的每一次 「 傳送電子郵件 」 活動完成的工作流程執行個體中。</span><span class="sxs-lookup"><span data-stu-id="ac51f-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ac51f-126">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ac51f-127">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="ac51f-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="ac51f-128">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-128">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="ac51f-129">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="ac51f-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ac51f-130">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="ac51f-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="ac51f-131">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-131">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="ac51f-132">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="ac51f-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ac51f-133">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="ac51f-134">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-134">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="ac51f-135">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ac51f-136">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ac51f-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="ac51f-137">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-137">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="ac51f-138">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="ac51f-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ac51f-139">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ac51f-140">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="ac51f-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ac51f-141">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="ac51f-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="ac51f-142">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="ac51f-142">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="ac51f-143">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac51f-144">父項目</span><span class="sxs-lookup"><span data-stu-id="ac51f-144">Parent Elements</span></span>  
  
|<span data-ttu-id="ac51f-145">項目</span><span class="sxs-lookup"><span data-stu-id="ac51f-145">Element</span></span>|<span data-ttu-id="ac51f-146">說明</span><span class="sxs-lookup"><span data-stu-id="ac51f-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac51f-147">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ac51f-147">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="ac51f-148">代表組態區段，用於建立工作流程追蹤記錄中追蹤參與者訂閱。</span><span class="sxs-lookup"><span data-stu-id="ac51f-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="ac51f-149">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="ac51f-150">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="ac51f-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac51f-151">備註</span><span class="sxs-lookup"><span data-stu-id="ac51f-151">Remarks</span></span>  
 <span data-ttu-id="ac51f-152">追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱特定工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="ac51f-153">這個設定項目會識別正在追蹤的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac51f-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="ac51f-154">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="ac51f-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="ac51f-155">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="ac51f-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="ac51f-156">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="ac51f-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="ac51f-157">有多種查詢型別，可讓您訂閱不同類別的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ac51f-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="ac51f-158">如需查詢的完整清單，請參閱本主題的子元素清單和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ac51f-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="ac51f-159">下列範例顯示追蹤設定檔中的組態檔，可允許追蹤參與者訂閱`Started`和`Completed`工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="ac51f-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac51f-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac51f-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="ac51f-161">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ac51f-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ac51f-162">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ac51f-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
