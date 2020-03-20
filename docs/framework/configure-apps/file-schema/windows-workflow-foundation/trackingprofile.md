---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8985da7e1223ac117cf1b68227140634f9c85d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151885"
---
# <a name="trackingprofile"></a><span data-ttu-id="df088-101">\<跟蹤設定檔></span><span class="sxs-lookup"><span data-stu-id="df088-101">\<trackingProfile></span></span>
<span data-ttu-id="df088-102">代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="df088-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="df088-103">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="df088-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="df088-104">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="df088-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="df088-105">有關工作流跟蹤及其配置的詳細資訊，請參閱[工作流跟蹤和跟蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="df088-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="df088-106">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="df088-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="df088-107">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="df088-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="df088-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="df088-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="df088-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<跟蹤設定檔>**</span><span class="sxs-lookup"><span data-stu-id="df088-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df088-110">語法</span><span class="sxs-lookup"><span data-stu-id="df088-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df088-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="df088-111">Attributes and Elements</span></span>  
 <span data-ttu-id="df088-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="df088-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df088-113">屬性</span><span class="sxs-lookup"><span data-stu-id="df088-113">Attributes</span></span>  
  
|<span data-ttu-id="df088-114">屬性</span><span class="sxs-lookup"><span data-stu-id="df088-114">Attribute</span></span>|<span data-ttu-id="df088-115">描述</span><span class="sxs-lookup"><span data-stu-id="df088-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df088-116">NAME</span><span class="sxs-lookup"><span data-stu-id="df088-116">name</span></span>|<span data-ttu-id="df088-117">指定追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="df088-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df088-118">子元素</span><span class="sxs-lookup"><span data-stu-id="df088-118">Child Elements</span></span>  
  
|<span data-ttu-id="df088-119">元素</span><span class="sxs-lookup"><span data-stu-id="df088-119">Element</span></span>|<span data-ttu-id="df088-120">描述</span><span class="sxs-lookup"><span data-stu-id="df088-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df088-121">\<參與者></span><span class="sxs-lookup"><span data-stu-id="df088-121">\<participants></span></span>](participants.md)|<span data-ttu-id="df088-122">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="df088-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df088-123">父項目</span><span class="sxs-lookup"><span data-stu-id="df088-123">Parent Elements</span></span>  
  
|<span data-ttu-id="df088-124">元素</span><span class="sxs-lookup"><span data-stu-id="df088-124">Element</span></span>|<span data-ttu-id="df088-125">描述</span><span class="sxs-lookup"><span data-stu-id="df088-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df088-126">\<跟蹤></span><span class="sxs-lookup"><span data-stu-id="df088-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="df088-127">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="df088-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df088-128">備註</span><span class="sxs-lookup"><span data-stu-id="df088-128">Remarks</span></span>  
 <span data-ttu-id="df088-129">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="df088-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="df088-130">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="df088-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="df088-131">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="df088-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="df088-132">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="df088-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="df088-133">有幾個查詢類型允許您訂閱不同的<xref:System.Activities.Tracking.TrackingRecord>物件類。</span><span class="sxs-lookup"><span data-stu-id="df088-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="df088-134">有關查詢的完整清單，請參閱[\<參與者>](participants.md)和[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="df088-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="df088-135">下面的示例顯示設定檔中的跟蹤設定檔，該設定檔允許追蹤參與者訂閱 和`Started``Completed`工作流事件。</span><span class="sxs-lookup"><span data-stu-id="df088-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df088-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df088-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="df088-137">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="df088-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="df088-138">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="df088-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
