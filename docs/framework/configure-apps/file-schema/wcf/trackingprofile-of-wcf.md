---
title: <trackingProfile>WCF 的
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854948"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="de4ae-102">\<WCF 的 trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="de4ae-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="de4ae-103">表示在追蹤參與者中建立工作流程追蹤記錄之訂閱的設定區段。</span><span class="sxs-lookup"><span data-stu-id="de4ae-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="de4ae-104">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="de4ae-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="de4ae-105">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="de4ae-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="de4ae-106">如需工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="de4ae-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="de4ae-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="de4ae-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de4ae-108">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="de4ae-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="de4ae-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="de4ae-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="de4ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="de4ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="de4ae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="de4ae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4ae-112">語法</span><span class="sxs-lookup"><span data-stu-id="de4ae-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de4ae-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="de4ae-113">Attributes and Elements</span></span>  

<span data-ttu-id="de4ae-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="de4ae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de4ae-115">屬性</span><span class="sxs-lookup"><span data-stu-id="de4ae-115">Attributes</span></span>  
  
|<span data-ttu-id="de4ae-116">屬性</span><span class="sxs-lookup"><span data-stu-id="de4ae-116">Attribute</span></span>|<span data-ttu-id="de4ae-117">描述</span><span class="sxs-lookup"><span data-stu-id="de4ae-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de4ae-118">NAME</span><span class="sxs-lookup"><span data-stu-id="de4ae-118">name</span></span>|<span data-ttu-id="de4ae-119">指定追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="de4ae-119">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de4ae-120">子元素</span><span class="sxs-lookup"><span data-stu-id="de4ae-120">Child Elements</span></span>  
  
|<span data-ttu-id="de4ae-121">項目</span><span class="sxs-lookup"><span data-stu-id="de4ae-121">Element</span></span>|<span data-ttu-id="de4ae-122">描述</span><span class="sxs-lookup"><span data-stu-id="de4ae-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de4ae-123">\<participants></span><span class="sxs-lookup"><span data-stu-id="de4ae-123">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="de4ae-124">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="de4ae-124">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de4ae-125">父項目</span><span class="sxs-lookup"><span data-stu-id="de4ae-125">Parent Elements</span></span>  
  
|<span data-ttu-id="de4ae-126">項目</span><span class="sxs-lookup"><span data-stu-id="de4ae-126">Element</span></span>|<span data-ttu-id="de4ae-127">描述</span><span class="sxs-lookup"><span data-stu-id="de4ae-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de4ae-128">\<tracking></span><span class="sxs-lookup"><span data-stu-id="de4ae-128">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="de4ae-129">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="de4ae-129">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de4ae-130">備註</span><span class="sxs-lookup"><span data-stu-id="de4ae-130">Remarks</span></span>  
 <span data-ttu-id="de4ae-131">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="de4ae-131">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="de4ae-132">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="de4ae-132">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="de4ae-133">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="de4ae-133">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="de4ae-134">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="de4ae-134">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="de4ae-135">有數種查詢類型可讓您訂閱不同的<xref:System.Activities.Tracking.TrackingRecord>物件類別。</span><span class="sxs-lookup"><span data-stu-id="de4ae-135">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="de4ae-136">如需查詢的完整清單，請參閱[ \<參與者 >](../windows-workflow-foundation/participants.md)和[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="de4ae-136">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="de4ae-137">下列範例顯示設定檔中的追蹤設定檔，可讓追蹤參與者訂閱`Started`和`Completed`工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="de4ae-137">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de4ae-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de4ae-138">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="de4ae-139">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="de4ae-139">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de4ae-140">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="de4ae-140">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
