---
title: '&lt;workflowInstanceQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 182a4082de6f1c67b7a0bc26662e2491623b2bba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="f3b14-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="f3b14-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="f3b14-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="f3b14-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="f3b14-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f3b14-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f3b14-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f3b14-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f3b14-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="f3b14-106">\<tracking></span></span>  
<span data-ttu-id="f3b14-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f3b14-107">\<trackingProfile></span></span>  
<span data-ttu-id="f3b14-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="f3b14-108">\<workflow></span></span>  
<span data-ttu-id="f3b14-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f3b14-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b14-110">語法</span><span class="sxs-lookup"><span data-stu-id="f3b14-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3b14-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f3b14-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f3b14-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f3b14-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3b14-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f3b14-113">Attributes</span></span>  
 <span data-ttu-id="f3b14-114">無。</span><span class="sxs-lookup"><span data-stu-id="f3b14-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3b14-115">子項目</span><span class="sxs-lookup"><span data-stu-id="f3b14-115">Child Elements</span></span>  
  
|<span data-ttu-id="f3b14-116">項目</span><span class="sxs-lookup"><span data-stu-id="f3b14-116">Element</span></span>|<span data-ttu-id="f3b14-117">說明</span><span class="sxs-lookup"><span data-stu-id="f3b14-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3b14-118">\<w ></span><span class="sxs-lookup"><span data-stu-id="f3b14-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="f3b14-119">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="f3b14-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3b14-120">父項目</span><span class="sxs-lookup"><span data-stu-id="f3b14-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f3b14-121">項目</span><span class="sxs-lookup"><span data-stu-id="f3b14-121">Element</span></span>|<span data-ttu-id="f3b14-122">說明</span><span class="sxs-lookup"><span data-stu-id="f3b14-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3b14-123">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="f3b14-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f3b14-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="f3b14-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3b14-125">備註</span><span class="sxs-lookup"><span data-stu-id="f3b14-125">Remarks</span></span>  
 <span data-ttu-id="f3b14-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="f3b14-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f3b14-127">範例</span><span class="sxs-lookup"><span data-stu-id="f3b14-127">Example</span></span>  
 <span data-ttu-id="f3b14-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="f3b14-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3b14-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b14-129">See Also</span></span>  
 <span data-ttu-id="f3b14-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f3b14-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f3b14-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f3b14-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f3b14-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="f3b14-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f3b14-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="f3b14-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
