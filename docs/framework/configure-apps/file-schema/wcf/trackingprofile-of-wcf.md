---
title: <trackingProfile>WCF 的
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854948"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="0d0a7-102">\<trackingProfile>WCF 的</span><span class="sxs-lookup"><span data-stu-id="0d0a7-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="0d0a7-103">代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="0d0a7-104">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="0d0a7-105">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="0d0a7-106">如需工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="0d0a7-107">語法</span><span class="sxs-lookup"><span data-stu-id="0d0a7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d0a7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d0a7-108">Attributes and Elements</span></span>  

<span data-ttu-id="0d0a7-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d0a7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0d0a7-110">Attributes</span></span>  
  
|<span data-ttu-id="0d0a7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0d0a7-111">Attribute</span></span>|<span data-ttu-id="0d0a7-112">描述</span><span class="sxs-lookup"><span data-stu-id="0d0a7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d0a7-113">NAME</span><span class="sxs-lookup"><span data-stu-id="0d0a7-113">name</span></span>|<span data-ttu-id="0d0a7-114">指定追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-114">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d0a7-115">子元素</span><span class="sxs-lookup"><span data-stu-id="0d0a7-115">Child Elements</span></span>  
  
|<span data-ttu-id="0d0a7-116">元素</span><span class="sxs-lookup"><span data-stu-id="0d0a7-116">Element</span></span>|<span data-ttu-id="0d0a7-117">描述</span><span class="sxs-lookup"><span data-stu-id="0d0a7-117">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="0d0a7-118">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d0a7-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0d0a7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0d0a7-120">元素</span><span class="sxs-lookup"><span data-stu-id="0d0a7-120">Element</span></span>|<span data-ttu-id="0d0a7-121">描述</span><span class="sxs-lookup"><span data-stu-id="0d0a7-121">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="0d0a7-122">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d0a7-123">備註</span><span class="sxs-lookup"><span data-stu-id="0d0a7-123">Remarks</span></span>  
 <span data-ttu-id="0d0a7-124">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-124">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="0d0a7-125">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-125">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="0d0a7-126">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-126">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="0d0a7-127">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-127">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="0d0a7-128">有數種查詢類型可讓您訂閱不同的 <xref:System.Activities.Tracking.TrackingRecord> 物件類別。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-128">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="0d0a7-129">如需查詢的完整清單，請參閱 [\<participants>](../windows-workflow-foundation/participants.md) 和[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-129">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="0d0a7-130">下列範例顯示設定檔中的追蹤設定檔，可讓追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="0d0a7-130">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="0d0a7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d0a7-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="0d0a7-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="0d0a7-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0d0a7-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0d0a7-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
