---
title: WCF 的 &lt;workflowInstanceQueries&gt;
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: dfa75a7e4729244ba5887e6666c0fdfe840e9faf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425845"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="9d5e5-102">WCF 的 &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="9d5e5-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="9d5e5-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="9d5e5-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="9d5e5-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9d5e5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="9d5e5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9d5e5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9d5e5-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="9d5e5-106">\<tracking></span></span>  
<span data-ttu-id="9d5e5-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9d5e5-107">\<trackingProfile></span></span>  
<span data-ttu-id="9d5e5-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="9d5e5-108">\<workflow></span></span>  
<span data-ttu-id="9d5e5-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="9d5e5-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5e5-110">語法</span><span class="sxs-lookup"><span data-stu-id="9d5e5-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d5e5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9d5e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9d5e5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9d5e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d5e5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9d5e5-113">Attributes</span></span>  
 <span data-ttu-id="9d5e5-114">無。</span><span class="sxs-lookup"><span data-stu-id="9d5e5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d5e5-115">子元素</span><span class="sxs-lookup"><span data-stu-id="9d5e5-115">Child Elements</span></span>  
  
|<span data-ttu-id="9d5e5-116">項目</span><span class="sxs-lookup"><span data-stu-id="9d5e5-116">Element</span></span>|<span data-ttu-id="9d5e5-117">描述</span><span class="sxs-lookup"><span data-stu-id="9d5e5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d5e5-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="9d5e5-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="9d5e5-119">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="9d5e5-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d5e5-120">父項目</span><span class="sxs-lookup"><span data-stu-id="9d5e5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9d5e5-121">項目</span><span class="sxs-lookup"><span data-stu-id="9d5e5-121">Element</span></span>|<span data-ttu-id="9d5e5-122">描述</span><span class="sxs-lookup"><span data-stu-id="9d5e5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d5e5-123">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="9d5e5-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9d5e5-124">包含所有的查詢所識別的特定工作流程的組態項目[activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx)屬性。</span><span class="sxs-lookup"><span data-stu-id="9d5e5-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d5e5-125">備註</span><span class="sxs-lookup"><span data-stu-id="9d5e5-125">Remarks</span></span>  
 <span data-ttu-id="9d5e5-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="9d5e5-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9d5e5-127">範例</span><span class="sxs-lookup"><span data-stu-id="9d5e5-127">Example</span></span>  
 <span data-ttu-id="9d5e5-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="9d5e5-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d5e5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d5e5-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="9d5e5-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9d5e5-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9d5e5-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9d5e5-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
