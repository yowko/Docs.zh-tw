---
title: '&lt;w&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: eb8b84f70025df3a8a8ac96f61dec6755eb3a364
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="98e1b-102">&lt;w&gt;</span><span class="sxs-lookup"><span data-stu-id="98e1b-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="98e1b-103">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="98e1b-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="98e1b-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="98e1b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="98e1b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="98e1b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="98e1b-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="98e1b-106">\<tracking></span></span>  
<span data-ttu-id="98e1b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="98e1b-107">\<trackingProfile></span></span>  
<span data-ttu-id="98e1b-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="98e1b-108">\<workflow></span></span>  
<span data-ttu-id="98e1b-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="98e1b-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="98e1b-110">\<w ></span><span class="sxs-lookup"><span data-stu-id="98e1b-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e1b-111">語法</span><span class="sxs-lookup"><span data-stu-id="98e1b-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98e1b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="98e1b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="98e1b-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="98e1b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98e1b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="98e1b-114">Attributes</span></span>  
 <span data-ttu-id="98e1b-115">無。</span><span class="sxs-lookup"><span data-stu-id="98e1b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="98e1b-116">子項目</span><span class="sxs-lookup"><span data-stu-id="98e1b-116">Child Elements</span></span>  
  
|<span data-ttu-id="98e1b-117">項目</span><span class="sxs-lookup"><span data-stu-id="98e1b-117">Element</span></span>|<span data-ttu-id="98e1b-118">描述</span><span class="sxs-lookup"><span data-stu-id="98e1b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98e1b-119">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="98e1b-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="98e1b-120">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="98e1b-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98e1b-121">父項目</span><span class="sxs-lookup"><span data-stu-id="98e1b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="98e1b-122">項目</span><span class="sxs-lookup"><span data-stu-id="98e1b-122">Element</span></span>|<span data-ttu-id="98e1b-123">描述</span><span class="sxs-lookup"><span data-stu-id="98e1b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98e1b-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="98e1b-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="98e1b-125">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="98e1b-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98e1b-126">備註</span><span class="sxs-lookup"><span data-stu-id="98e1b-126">Remarks</span></span>  
 <span data-ttu-id="98e1b-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="98e1b-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="98e1b-128">範例</span><span class="sxs-lookup"><span data-stu-id="98e1b-128">Example</span></span>  
 <span data-ttu-id="98e1b-129">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98e1b-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98e1b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98e1b-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="98e1b-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="98e1b-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="98e1b-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="98e1b-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
