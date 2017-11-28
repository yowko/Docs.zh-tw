---
title: '&lt;w&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7ed855dc49c4e6639734dcc6a9bc1db7ae53d01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="18d10-102">&lt;w&gt;</span><span class="sxs-lookup"><span data-stu-id="18d10-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="18d10-103">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="18d10-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="18d10-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="18d10-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="18d10-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="18d10-105">\<system.serviceModel></span></span>  
<span data-ttu-id="18d10-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="18d10-106">\<tracking></span></span>  
<span data-ttu-id="18d10-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="18d10-107">\<trackingProfile></span></span>  
<span data-ttu-id="18d10-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="18d10-108">\<workflow></span></span>  
<span data-ttu-id="18d10-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="18d10-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="18d10-110">\<w ></span><span class="sxs-lookup"><span data-stu-id="18d10-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18d10-111">語法</span><span class="sxs-lookup"><span data-stu-id="18d10-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18d10-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18d10-112">Attributes and Elements</span></span>  
 <span data-ttu-id="18d10-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18d10-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18d10-114">屬性</span><span class="sxs-lookup"><span data-stu-id="18d10-114">Attributes</span></span>  
 <span data-ttu-id="18d10-115">無。</span><span class="sxs-lookup"><span data-stu-id="18d10-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18d10-116">子項目</span><span class="sxs-lookup"><span data-stu-id="18d10-116">Child Elements</span></span>  
  
|<span data-ttu-id="18d10-117">項目</span><span class="sxs-lookup"><span data-stu-id="18d10-117">Element</span></span>|<span data-ttu-id="18d10-118">說明</span><span class="sxs-lookup"><span data-stu-id="18d10-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18d10-119">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="18d10-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="18d10-120">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="18d10-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18d10-121">父項目</span><span class="sxs-lookup"><span data-stu-id="18d10-121">Parent Elements</span></span>  
  
|<span data-ttu-id="18d10-122">項目</span><span class="sxs-lookup"><span data-stu-id="18d10-122">Element</span></span>|<span data-ttu-id="18d10-123">說明</span><span class="sxs-lookup"><span data-stu-id="18d10-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18d10-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="18d10-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="18d10-125">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="18d10-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18d10-126">備註</span><span class="sxs-lookup"><span data-stu-id="18d10-126">Remarks</span></span>  
 <span data-ttu-id="18d10-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="18d10-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="18d10-128">範例</span><span class="sxs-lookup"><span data-stu-id="18d10-128">Example</span></span>  
 <span data-ttu-id="18d10-129">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="18d10-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18d10-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18d10-130">See Also</span></span>  
 <span data-ttu-id="18d10-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="18d10-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="18d10-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="18d10-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="18d10-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="18d10-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="18d10-134">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="18d10-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
