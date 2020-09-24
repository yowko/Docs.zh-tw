---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8bf7798443e2022adef2738aad3e4e1b9846af53
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161993"
---
# \<trackingProfile>

<span data-ttu-id="d826c-101">代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d826c-101">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="d826c-102">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="d826c-102">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d826c-103">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="d826c-103">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="d826c-104">如需工作流程追蹤及其設定的詳細資訊，請參閱[工作流程追蹤和追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="d826c-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="d826c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d826c-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d826c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d826c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d826c-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d826c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d826c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d826c-108">Attributes</span></span>  
  
|<span data-ttu-id="d826c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d826c-109">Attribute</span></span>|<span data-ttu-id="d826c-110">描述</span><span class="sxs-lookup"><span data-stu-id="d826c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d826c-111">NAME</span><span class="sxs-lookup"><span data-stu-id="d826c-111">name</span></span>|<span data-ttu-id="d826c-112">指定追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d826c-112">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d826c-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d826c-113">Child Elements</span></span>  
  
|<span data-ttu-id="d826c-114">項目</span><span class="sxs-lookup"><span data-stu-id="d826c-114">Element</span></span>|<span data-ttu-id="d826c-115">描述</span><span class="sxs-lookup"><span data-stu-id="d826c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="d826c-116">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="d826c-116">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d826c-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d826c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d826c-118">項目</span><span class="sxs-lookup"><span data-stu-id="d826c-118">Element</span></span>|<span data-ttu-id="d826c-119">描述</span><span class="sxs-lookup"><span data-stu-id="d826c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="d826c-120">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="d826c-120">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d826c-121">備註</span><span class="sxs-lookup"><span data-stu-id="d826c-121">Remarks</span></span>  

 <span data-ttu-id="d826c-122">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="d826c-122">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d826c-123">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="d826c-123">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="d826c-124">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="d826c-124">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="d826c-125">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="d826c-125">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="d826c-126">有少數的查詢類型可讓您訂閱不同類別的 <xref:System.Activities.Tracking.TrackingRecord> 物件。</span><span class="sxs-lookup"><span data-stu-id="d826c-126">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="d826c-127">如需查詢的完整清單，請參閱 [\<participants>](participants.md) 和 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="d826c-127">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="d826c-128">下列範例顯示設定檔中的追蹤設定檔，可讓追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="d826c-128">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d826c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d826c-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="d826c-130">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="d826c-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d826c-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d826c-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
