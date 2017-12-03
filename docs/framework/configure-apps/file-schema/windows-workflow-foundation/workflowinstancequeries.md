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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fef440aa086253cd4f7df709ee5b5764fe7b2789
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="93999-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="93999-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="93999-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="93999-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="93999-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="93999-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="93999-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="93999-105">\<system.serviceModel></span></span>  
<span data-ttu-id="93999-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="93999-106">\<tracking></span></span>  
<span data-ttu-id="93999-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="93999-107">\<trackingProfile></span></span>  
<span data-ttu-id="93999-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="93999-108">\<workflow></span></span>  
<span data-ttu-id="93999-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="93999-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93999-110">語法</span><span class="sxs-lookup"><span data-stu-id="93999-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93999-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93999-111">Attributes and Elements</span></span>  
 <span data-ttu-id="93999-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="93999-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93999-113">屬性</span><span class="sxs-lookup"><span data-stu-id="93999-113">Attributes</span></span>  
 <span data-ttu-id="93999-114">無。</span><span class="sxs-lookup"><span data-stu-id="93999-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93999-115">子項目</span><span class="sxs-lookup"><span data-stu-id="93999-115">Child Elements</span></span>  
  
|<span data-ttu-id="93999-116">項目</span><span class="sxs-lookup"><span data-stu-id="93999-116">Element</span></span>|<span data-ttu-id="93999-117">說明</span><span class="sxs-lookup"><span data-stu-id="93999-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93999-118">\<w ></span><span class="sxs-lookup"><span data-stu-id="93999-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="93999-119">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="93999-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93999-120">父項目</span><span class="sxs-lookup"><span data-stu-id="93999-120">Parent Elements</span></span>  
  
|<span data-ttu-id="93999-121">項目</span><span class="sxs-lookup"><span data-stu-id="93999-121">Element</span></span>|<span data-ttu-id="93999-122">說明</span><span class="sxs-lookup"><span data-stu-id="93999-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93999-123">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="93999-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="93999-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="93999-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93999-125">備註</span><span class="sxs-lookup"><span data-stu-id="93999-125">Remarks</span></span>  
 <span data-ttu-id="93999-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="93999-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="93999-127">範例</span><span class="sxs-lookup"><span data-stu-id="93999-127">Example</span></span>  
 <span data-ttu-id="93999-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="93999-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93999-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93999-129">See Also</span></span>  
 <span data-ttu-id="93999-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="93999-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="93999-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="93999-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="93999-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="93999-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="93999-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="93999-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
