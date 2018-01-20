---
title: '&lt;trackingProfile&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6acc4e5b71d94b712ae27e540df073828285b0aa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="lttrackingprofilegt"></a><span data-ttu-id="e06e5-102">&lt;trackingProfile&gt;</span><span class="sxs-lookup"><span data-stu-id="e06e5-102">&lt;trackingProfile&gt;</span></span>
<span data-ttu-id="e06e5-103">代表組態區段，用於建立工作流程追蹤記錄中追蹤參與者訂閱。</span><span class="sxs-lookup"><span data-stu-id="e06e5-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="e06e5-104">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="e06e5-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e06e5-105">追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。</span><span class="sxs-lookup"><span data-stu-id="e06e5-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="e06e5-106">如需工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e06e5-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e06e5-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e06e5-107">\<system.serviceModel></span></span>  
<span data-ttu-id="e06e5-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e06e5-108">\<tracking></span></span>  
<span data-ttu-id="e06e5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e06e5-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06e5-110">語法</span><span class="sxs-lookup"><span data-stu-id="e06e5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e06e5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e06e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e06e5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e06e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e06e5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e06e5-113">Attributes</span></span>  
  
|<span data-ttu-id="e06e5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e06e5-114">Attribute</span></span>|<span data-ttu-id="e06e5-115">描述</span><span class="sxs-lookup"><span data-stu-id="e06e5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e06e5-116">name</span><span class="sxs-lookup"><span data-stu-id="e06e5-116">name</span></span>|<span data-ttu-id="e06e5-117">指定追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e06e5-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e06e5-118">子元素</span><span class="sxs-lookup"><span data-stu-id="e06e5-118">Child Elements</span></span>  
  
|<span data-ttu-id="e06e5-119">項目</span><span class="sxs-lookup"><span data-stu-id="e06e5-119">Element</span></span>|<span data-ttu-id="e06e5-120">描述</span><span class="sxs-lookup"><span data-stu-id="e06e5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e06e5-121">\<participants></span><span class="sxs-lookup"><span data-stu-id="e06e5-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="e06e5-122">包含所有的查詢所識別的特定工作流程的組態項目**超連結"http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid (VS.100).aspx"ctivityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="e06e5-122">A configuration element that contains all queries for a specific workflow identified by the **a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx"ctivityDefinitionId** property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e06e5-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e06e5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e06e5-124">項目</span><span class="sxs-lookup"><span data-stu-id="e06e5-124">Element</span></span>|<span data-ttu-id="e06e5-125">描述</span><span class="sxs-lookup"><span data-stu-id="e06e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e06e5-126">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e06e5-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="e06e5-127">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="e06e5-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e06e5-128">備註</span><span class="sxs-lookup"><span data-stu-id="e06e5-128">Remarks</span></span>  
 <span data-ttu-id="e06e5-129">追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="e06e5-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e06e5-130">根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="e06e5-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="e06e5-131">反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="e06e5-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="e06e5-132">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="e06e5-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="e06e5-133">有很多種查詢型別訂閱不同類別的超連結"http://msdn.microsoft.com/library/system.activities.tracking.trackingrecord (VS.100).aspx"TrackingRecord 物件。</span><span class="sxs-lookup"><span data-stu-id="e06e5-133">There are a handful of query types that allow you subscribe to different classes of  HYPERLINK "http://msdn.microsoft.com/library/system.activities.tracking.trackingrecord(VS.100).aspx" TrackingRecord objects.</span></span> <span data-ttu-id="e06e5-134">如需查詢的完整清單，請參閱[\<參與者 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="e06e5-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="e06e5-135">下列範例顯示追蹤設定檔中的組態檔，可允許追蹤參與者訂閱`Started`和`Completed`工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="e06e5-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e06e5-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="e06e5-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="e06e5-137">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e06e5-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e06e5-138">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e06e5-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
