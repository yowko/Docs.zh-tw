---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 31490c7425572909cc30fe4237af9309754b68e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768845"
---
# <a name="tracking"></a><span data-ttu-id="3917a-101">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3917a-101">\<tracking></span></span>
<span data-ttu-id="3917a-102">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="3917a-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="3917a-103">如需在工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)並[流程設定追蹤](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="3917a-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="3917a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3917a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3917a-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3917a-105">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3917a-106">語法</span><span class="sxs-lookup"><span data-stu-id="3917a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3917a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3917a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3917a-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3917a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3917a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3917a-109">Attributes</span></span>  
 <span data-ttu-id="3917a-110">無。</span><span class="sxs-lookup"><span data-stu-id="3917a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3917a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3917a-111">Child Elements</span></span>  
  
|<span data-ttu-id="3917a-112">項目</span><span class="sxs-lookup"><span data-stu-id="3917a-112">Element</span></span>|<span data-ttu-id="3917a-113">描述</span><span class="sxs-lookup"><span data-stu-id="3917a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3917a-114">\<participants></span><span class="sxs-lookup"><span data-stu-id="3917a-114">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="3917a-115">訂閱追蹤記錄的組態項目定義的參與者集合。</span><span class="sxs-lookup"><span data-stu-id="3917a-115">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="3917a-116">追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 (例如，他們可以選擇寫入檔案)。</span><span class="sxs-lookup"><span data-stu-id="3917a-116">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="3917a-117">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3917a-117">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="3917a-118">篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="3917a-118">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3917a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3917a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3917a-120">項目</span><span class="sxs-lookup"><span data-stu-id="3917a-120">Element</span></span>|<span data-ttu-id="3917a-121">描述</span><span class="sxs-lookup"><span data-stu-id="3917a-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3917a-122">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3917a-122">system.ServiceModel</span></span>|<span data-ttu-id="3917a-123">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="3917a-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3917a-124">備註</span><span class="sxs-lookup"><span data-stu-id="3917a-124">Remarks</span></span>  
 <span data-ttu-id="3917a-125">追蹤可提供您檢查工作流程執行的能力。</span><span class="sxs-lookup"><span data-stu-id="3917a-125">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="3917a-126">工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。</span><span class="sxs-lookup"><span data-stu-id="3917a-126">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="3917a-127">例如，工作流程執行個體開始或完成時會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="3917a-127">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="3917a-128">追蹤也可以擷取與工作流程變數相關聯的商務相關資料。</span><span class="sxs-lookup"><span data-stu-id="3917a-128">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="3917a-129">例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。</span><span class="sxs-lookup"><span data-stu-id="3917a-129">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="3917a-130">一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。</span><span class="sxs-lookup"><span data-stu-id="3917a-130">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3917a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3917a-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="3917a-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="3917a-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
