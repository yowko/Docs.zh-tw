---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151854"
---
# \<workflow>
<span data-ttu-id="0c7c5-101">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-101">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="0c7c5-102">如需工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**  
  
## <a name="syntax"></a><span data-ttu-id="0c7c5-103">語法</span><span class="sxs-lookup"><span data-stu-id="0c7c5-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c7c5-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c7c5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0c7c5-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c7c5-106">屬性</span><span class="sxs-lookup"><span data-stu-id="0c7c5-106">Attributes</span></span>  
  
|<span data-ttu-id="0c7c5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0c7c5-107">Attribute</span></span>|<span data-ttu-id="0c7c5-108">描述</span><span class="sxs-lookup"><span data-stu-id="0c7c5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c7c5-109">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="0c7c5-109">activityDefinitionId</span></span>|<span data-ttu-id="0c7c5-110">指定工作流程之活動定義識別碼的字串，該工作流程正在進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-110">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c7c5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0c7c5-111">Child Elements</span></span>  
  
|<span data-ttu-id="0c7c5-112">元素</span><span class="sxs-lookup"><span data-stu-id="0c7c5-112">Element</span></span>|<span data-ttu-id="0c7c5-113">描述</span><span class="sxs-lookup"><span data-stu-id="0c7c5-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries.md)|<span data-ttu-id="0c7c5-114">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-114">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="0c7c5-115">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-115">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[\<activityStateQueries>](activitystatequeries.md)|<span data-ttu-id="0c7c5-116">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-116">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="0c7c5-117">例如，您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-117">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="0c7c5-118">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-118">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="0c7c5-119">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-119">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="0c7c5-120">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-120">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="0c7c5-121">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|<span data-ttu-id="0c7c5-122">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-122">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0c7c5-123">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-123">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[\<customTrackingQueries>](customtrackingqueries.md)|<span data-ttu-id="0c7c5-124">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-124">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0c7c5-125">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-125">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="0c7c5-126">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-126">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0c7c5-127">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-127">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="0c7c5-128">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-128">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0c7c5-129">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-129">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="0c7c5-130">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-130">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c7c5-131">父項目</span><span class="sxs-lookup"><span data-stu-id="0c7c5-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0c7c5-132">元素</span><span class="sxs-lookup"><span data-stu-id="0c7c5-132">Element</span></span>|<span data-ttu-id="0c7c5-133">描述</span><span class="sxs-lookup"><span data-stu-id="0c7c5-133">Description</span></span>|  
|-------------|-----------------|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="0c7c5-134">代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-134">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="0c7c5-135">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-135">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="0c7c5-136">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-136">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c7c5-137">備註</span><span class="sxs-lookup"><span data-stu-id="0c7c5-137">Remarks</span></span>  
 <span data-ttu-id="0c7c5-138">追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱特定工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-138">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="0c7c5-139">這個設定項目會識別正在追蹤的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-139">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="0c7c5-140">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-140">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="0c7c5-141">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-141">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="0c7c5-142">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-142">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="0c7c5-143">您可以使用多種查詢型別訂閱不同類別的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-143">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="0c7c5-144">如需查詢的完整清單，請參閱本主題的子項目清單和[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-144">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="0c7c5-145">下列範例顯示設定檔中的追蹤設定檔，可讓追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="0c7c5-145">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c7c5-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7c5-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="0c7c5-147">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="0c7c5-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0c7c5-148">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0c7c5-148">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
