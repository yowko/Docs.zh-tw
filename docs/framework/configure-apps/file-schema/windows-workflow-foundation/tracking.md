---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 0b00780dedc15fe90163145f23c57f62369c401f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198739"
---
# \<tracking>

<span data-ttu-id="6ac79-101">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="6ac79-101">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="6ac79-102">如需工作流程追蹤及其設定的詳細資訊，請參閱工作流程 [追蹤和追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和設定 [工作流程的追蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac79-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="6ac79-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ac79-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ac79-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ac79-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6ac79-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ac79-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ac79-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6ac79-106">Attributes</span></span>  

 <span data-ttu-id="6ac79-107">無。</span><span class="sxs-lookup"><span data-stu-id="6ac79-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ac79-108">子元素</span><span class="sxs-lookup"><span data-stu-id="6ac79-108">Child Elements</span></span>  
  
|<span data-ttu-id="6ac79-109">項目</span><span class="sxs-lookup"><span data-stu-id="6ac79-109">Element</span></span>|<span data-ttu-id="6ac79-110">描述</span><span class="sxs-lookup"><span data-stu-id="6ac79-110">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="6ac79-111">組態項目的集合，這些項目會定義訂閱追蹤記錄的參與者。</span><span class="sxs-lookup"><span data-stu-id="6ac79-111">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="6ac79-112">追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 (例如，他們可以選擇寫入檔案)。</span><span class="sxs-lookup"><span data-stu-id="6ac79-112">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="6ac79-113">篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="6ac79-113">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ac79-114">父項目</span><span class="sxs-lookup"><span data-stu-id="6ac79-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6ac79-115">項目</span><span class="sxs-lookup"><span data-stu-id="6ac79-115">Element</span></span>|<span data-ttu-id="6ac79-116">描述</span><span class="sxs-lookup"><span data-stu-id="6ac79-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ac79-117">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6ac79-117">system.ServiceModel</span></span>|<span data-ttu-id="6ac79-118">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="6ac79-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ac79-119">備註</span><span class="sxs-lookup"><span data-stu-id="6ac79-119">Remarks</span></span>  

 <span data-ttu-id="6ac79-120">追蹤可提供您檢查工作流程執行的能力。</span><span class="sxs-lookup"><span data-stu-id="6ac79-120">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="6ac79-121">工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。</span><span class="sxs-lookup"><span data-stu-id="6ac79-121">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="6ac79-122">例如，工作流程執行個體開始或完成時會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="6ac79-122">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="6ac79-123">追蹤也可以擷取與工作流程變數相關聯的商務相關資料。</span><span class="sxs-lookup"><span data-stu-id="6ac79-123">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="6ac79-124">例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。</span><span class="sxs-lookup"><span data-stu-id="6ac79-124">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="6ac79-125">一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。</span><span class="sxs-lookup"><span data-stu-id="6ac79-125">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac79-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ac79-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="6ac79-127">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="6ac79-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
