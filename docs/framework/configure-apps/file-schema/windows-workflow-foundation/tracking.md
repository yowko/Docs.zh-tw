---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151906"
---
# <a name="tracking"></a><span data-ttu-id="72314-101">\<跟蹤></span><span class="sxs-lookup"><span data-stu-id="72314-101">\<tracking></span></span>
<span data-ttu-id="72314-102">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="72314-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="72314-103">有關工作流跟蹤及其配置的詳細資訊，請參閱工作流[的工作流跟蹤和跟蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)和[配置跟蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="72314-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="72314-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="72314-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72314-105">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="72314-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="72314-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<跟蹤>**</span><span class="sxs-lookup"><span data-stu-id="72314-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72314-107">語法</span><span class="sxs-lookup"><span data-stu-id="72314-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72314-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="72314-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72314-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="72314-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72314-110">屬性</span><span class="sxs-lookup"><span data-stu-id="72314-110">Attributes</span></span>  
 <span data-ttu-id="72314-111">無。</span><span class="sxs-lookup"><span data-stu-id="72314-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72314-112">子元素</span><span class="sxs-lookup"><span data-stu-id="72314-112">Child Elements</span></span>  
  
|<span data-ttu-id="72314-113">元素</span><span class="sxs-lookup"><span data-stu-id="72314-113">Element</span></span>|<span data-ttu-id="72314-114">描述</span><span class="sxs-lookup"><span data-stu-id="72314-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72314-115">\<參與者></span><span class="sxs-lookup"><span data-stu-id="72314-115">\<participants></span></span>](participants.md)|<span data-ttu-id="72314-116">組態項目的集合，這些項目會定義訂閱追蹤記錄的參與者。</span><span class="sxs-lookup"><span data-stu-id="72314-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="72314-117">追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 (例如，他們可以選擇寫入檔案)。</span><span class="sxs-lookup"><span data-stu-id="72314-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="72314-118">\<跟蹤設定檔></span><span class="sxs-lookup"><span data-stu-id="72314-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="72314-119">篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="72314-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72314-120">父項目</span><span class="sxs-lookup"><span data-stu-id="72314-120">Parent Elements</span></span>  
  
|<span data-ttu-id="72314-121">元素</span><span class="sxs-lookup"><span data-stu-id="72314-121">Element</span></span>|<span data-ttu-id="72314-122">描述</span><span class="sxs-lookup"><span data-stu-id="72314-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72314-123">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="72314-123">system.ServiceModel</span></span>|<span data-ttu-id="72314-124">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="72314-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72314-125">備註</span><span class="sxs-lookup"><span data-stu-id="72314-125">Remarks</span></span>  
 <span data-ttu-id="72314-126">追蹤可提供您檢查工作流程執行的能力。</span><span class="sxs-lookup"><span data-stu-id="72314-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="72314-127">工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。</span><span class="sxs-lookup"><span data-stu-id="72314-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="72314-128">例如，工作流程執行個體開始或完成時會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="72314-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="72314-129">追蹤也可以擷取與工作流程變數相關聯的商務相關資料。</span><span class="sxs-lookup"><span data-stu-id="72314-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="72314-130">例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。</span><span class="sxs-lookup"><span data-stu-id="72314-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="72314-131">一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。</span><span class="sxs-lookup"><span data-stu-id="72314-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72314-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72314-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="72314-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="72314-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
