---
title: WCF 的 &lt;tracking&gt;
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: f09c8c59bf805ec7a061fba3ebfecd5fb457e402
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttrackinggt-of-wcf"></a><span data-ttu-id="4ca96-102">WCF 的 &lt;tracking&gt;</span><span class="sxs-lookup"><span data-stu-id="4ca96-102">&lt;tracking&gt; of WCF</span></span>
<span data-ttu-id="4ca96-103">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="4ca96-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="4ca96-104">如需工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)和[流程設定追蹤](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="4ca96-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="4ca96-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ca96-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4ca96-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="4ca96-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca96-107">語法</span><span class="sxs-lookup"><span data-stu-id="4ca96-107">Syntax</span></span>  
  
```xml
   <system.serviceModel>  <tracking>       <participants>       <add name="String"            profileName="String"           type="String" />      </participants>     <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ca96-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4ca96-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4ca96-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4ca96-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ca96-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4ca96-110">Attributes</span></span>  
 <span data-ttu-id="4ca96-111">無。</span><span class="sxs-lookup"><span data-stu-id="4ca96-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ca96-112">子項目</span><span class="sxs-lookup"><span data-stu-id="4ca96-112">Child Elements</span></span>  
  
|<span data-ttu-id="4ca96-113">項目</span><span class="sxs-lookup"><span data-stu-id="4ca96-113">Element</span></span>|<span data-ttu-id="4ca96-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ca96-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ca96-115">\<參與者 ></span><span class="sxs-lookup"><span data-stu-id="4ca96-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="4ca96-116">定義參與者的組態項目的集合，這些訂閱追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="4ca96-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="4ca96-117">追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 (例如，他們可以選擇寫入檔案)。</span><span class="sxs-lookup"><span data-stu-id="4ca96-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="4ca96-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4ca96-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="4ca96-119">篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4ca96-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ca96-120">父項目</span><span class="sxs-lookup"><span data-stu-id="4ca96-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4ca96-121">項目</span><span class="sxs-lookup"><span data-stu-id="4ca96-121">Element</span></span>|<span data-ttu-id="4ca96-122">描述</span><span class="sxs-lookup"><span data-stu-id="4ca96-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ca96-123">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4ca96-123">system.ServiceModel</span></span>|<span data-ttu-id="4ca96-124">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="4ca96-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ca96-125">備註</span><span class="sxs-lookup"><span data-stu-id="4ca96-125">Remarks</span></span>  
 <span data-ttu-id="4ca96-126">追蹤可提供您檢查工作流程執行的能力。</span><span class="sxs-lookup"><span data-stu-id="4ca96-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="4ca96-127">工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。</span><span class="sxs-lookup"><span data-stu-id="4ca96-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="4ca96-128">例如，工作流程執行個體開始或完成時會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="4ca96-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="4ca96-129">追蹤也可以擷取與工作流程變數相關聯的商務相關資料。</span><span class="sxs-lookup"><span data-stu-id="4ca96-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="4ca96-130">例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。</span><span class="sxs-lookup"><span data-stu-id="4ca96-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="4ca96-131">一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。</span><span class="sxs-lookup"><span data-stu-id="4ca96-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca96-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ca96-132">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [<span data-ttu-id="4ca96-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="4ca96-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
