---
title: <tracking>WCF 的
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399424"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="a0789-102">\<追蹤 WCF ></span><span class="sxs-lookup"><span data-stu-id="a0789-102">\<tracking> of WCF</span></span>
<span data-ttu-id="a0789-103">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="a0789-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="a0789-104">如需工作流程追蹤及其設定的詳細資訊，請參閱工作流程[追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)追蹤和設定[工作流程的追蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="a0789-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="a0789-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0789-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a0789-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a0789-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a0789-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<追蹤 >**</span><span class="sxs-lookup"><span data-stu-id="a0789-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0789-108">語法</span><span class="sxs-lookup"><span data-stu-id="a0789-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
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
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0789-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a0789-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a0789-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a0789-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0789-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a0789-111">Attributes</span></span>  
 <span data-ttu-id="a0789-112">無。</span><span class="sxs-lookup"><span data-stu-id="a0789-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0789-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a0789-113">Child Elements</span></span>  
  
|<span data-ttu-id="a0789-114">項目</span><span class="sxs-lookup"><span data-stu-id="a0789-114">Element</span></span>|<span data-ttu-id="a0789-115">描述</span><span class="sxs-lookup"><span data-stu-id="a0789-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0789-116">\<participants></span><span class="sxs-lookup"><span data-stu-id="a0789-116">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="a0789-117">定義訂閱追蹤記錄之參與者的 configuration 專案集合。</span><span class="sxs-lookup"><span data-stu-id="a0789-117">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="a0789-118">追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 (例如，他們可以選擇寫入檔案)。</span><span class="sxs-lookup"><span data-stu-id="a0789-118">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="a0789-119">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a0789-119">\<trackingProfile></span></span>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="a0789-120">篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="a0789-120">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0789-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a0789-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a0789-122">項目</span><span class="sxs-lookup"><span data-stu-id="a0789-122">Element</span></span>|<span data-ttu-id="a0789-123">說明</span><span class="sxs-lookup"><span data-stu-id="a0789-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0789-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a0789-124">system.ServiceModel</span></span>|<span data-ttu-id="a0789-125">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="a0789-125">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0789-126">備註</span><span class="sxs-lookup"><span data-stu-id="a0789-126">Remarks</span></span>  
 <span data-ttu-id="a0789-127">追蹤可提供您檢查工作流程執行的能力。</span><span class="sxs-lookup"><span data-stu-id="a0789-127">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="a0789-128">工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。</span><span class="sxs-lookup"><span data-stu-id="a0789-128">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="a0789-129">例如，工作流程執行個體開始或完成時會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a0789-129">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="a0789-130">追蹤也可以擷取與工作流程變數相關聯的商務相關資料。</span><span class="sxs-lookup"><span data-stu-id="a0789-130">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="a0789-131">例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。</span><span class="sxs-lookup"><span data-stu-id="a0789-131">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="a0789-132">一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。</span><span class="sxs-lookup"><span data-stu-id="a0789-132">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0789-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0789-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="a0789-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a0789-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
