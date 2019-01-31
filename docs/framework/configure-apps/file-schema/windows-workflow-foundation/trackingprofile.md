---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: ff5bf2b4140665e7af8f8ec0103c32fe2e8a3142
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267855"
---
# <a name="trackingprofile"></a><span data-ttu-id="d9c8c-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d9c8c-101">\<trackingProfile></span></span>
<span data-ttu-id="d9c8c-102">表示組態區段，用於建立工作流程追蹤記錄中追蹤參與者的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="d9c8c-103">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d9c8c-104">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="d9c8c-105">如需在工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)並[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d9c8c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d9c8c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d9c8c-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d9c8c-107">\<tracking></span></span>  
<span data-ttu-id="d9c8c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d9c8c-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c8c-109">語法</span><span class="sxs-lookup"><span data-stu-id="d9c8c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9c8c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d9c8c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d9c8c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9c8c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d9c8c-112">Attributes</span></span>  
  
|<span data-ttu-id="d9c8c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d9c8c-113">Attribute</span></span>|<span data-ttu-id="d9c8c-114">描述</span><span class="sxs-lookup"><span data-stu-id="d9c8c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9c8c-115">name</span><span class="sxs-lookup"><span data-stu-id="d9c8c-115">name</span></span>|<span data-ttu-id="d9c8c-116">指定追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9c8c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="d9c8c-117">Child Elements</span></span>  
  
|<span data-ttu-id="d9c8c-118">項目</span><span class="sxs-lookup"><span data-stu-id="d9c8c-118">Element</span></span>|<span data-ttu-id="d9c8c-119">描述</span><span class="sxs-lookup"><span data-stu-id="d9c8c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9c8c-120">\<participants></span><span class="sxs-lookup"><span data-stu-id="d9c8c-120">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="d9c8c-121">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9c8c-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d9c8c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d9c8c-123">項目</span><span class="sxs-lookup"><span data-stu-id="d9c8c-123">Element</span></span>|<span data-ttu-id="d9c8c-124">描述</span><span class="sxs-lookup"><span data-stu-id="d9c8c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9c8c-125">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d9c8c-125">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="d9c8c-126">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9c8c-127">備註</span><span class="sxs-lookup"><span data-stu-id="d9c8c-127">Remarks</span></span>  
 <span data-ttu-id="d9c8c-128">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d9c8c-129">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="d9c8c-130">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="d9c8c-131">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="d9c8c-132">有多種查詢型別訂閱不同類別的<xref:System.Activities.Tracking.TrackingRecord>物件。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="d9c8c-133">查詢的完整清單，請參閱 < [\<參與者 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)並[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="d9c8c-133">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="d9c8c-134">下列範例顯示的追蹤設定檔中的組態檔，可允許追蹤參與者訂閱`Started`和`Completed`工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="d9c8c-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9c8c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c8c-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="d9c8c-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d9c8c-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d9c8c-137">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d9c8c-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
