---
title: "WCF 的 &lt;states&gt;、&lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb2a277759904a415316e29ba8151f7c1a0f475d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="356ae-102">WCF 的 &lt;states&gt;、&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="356ae-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="356ae-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="356ae-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="356ae-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="356ae-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="356ae-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="356ae-105">\<system.serviceModel></span></span>  
<span data-ttu-id="356ae-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="356ae-106">\<tracking></span></span>  
<span data-ttu-id="356ae-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="356ae-107">\<trackingProfile></span></span>  
<span data-ttu-id="356ae-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="356ae-108">\<workflow></span></span>  
<span data-ttu-id="356ae-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="356ae-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="356ae-110">\<w ></span><span class="sxs-lookup"><span data-stu-id="356ae-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="356ae-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="356ae-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356ae-112">語法</span><span class="sxs-lookup"><span data-stu-id="356ae-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="356ae-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="356ae-113">Attributes and Elements</span></span>  
 <span data-ttu-id="356ae-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="356ae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="356ae-115">屬性</span><span class="sxs-lookup"><span data-stu-id="356ae-115">Attributes</span></span>  
 <span data-ttu-id="356ae-116">無。</span><span class="sxs-lookup"><span data-stu-id="356ae-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="356ae-117">子項目</span><span class="sxs-lookup"><span data-stu-id="356ae-117">Child Elements</span></span>  
  
|<span data-ttu-id="356ae-118">項目</span><span class="sxs-lookup"><span data-stu-id="356ae-118">Element</span></span>|<span data-ttu-id="356ae-119">說明</span><span class="sxs-lookup"><span data-stu-id="356ae-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="356ae-120">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="356ae-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="356ae-121">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="356ae-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="356ae-122">父項目</span><span class="sxs-lookup"><span data-stu-id="356ae-122">Parent Elements</span></span>  
  
|<span data-ttu-id="356ae-123">項目</span><span class="sxs-lookup"><span data-stu-id="356ae-123">Element</span></span>|<span data-ttu-id="356ae-124">說明</span><span class="sxs-lookup"><span data-stu-id="356ae-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="356ae-125">\<w ></span><span class="sxs-lookup"><span data-stu-id="356ae-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="356ae-126">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="356ae-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="356ae-127">備註</span><span class="sxs-lookup"><span data-stu-id="356ae-127">Remarks</span></span>  
 <span data-ttu-id="356ae-128">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="356ae-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="356ae-129">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="356ae-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="356ae-130">狀態</span><span class="sxs-lookup"><span data-stu-id="356ae-130">State</span></span>|<span data-ttu-id="356ae-131">描述</span><span class="sxs-lookup"><span data-stu-id="356ae-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="356ae-132">已中止</span><span class="sxs-lookup"><span data-stu-id="356ae-132">Aborted</span></span>|<span data-ttu-id="356ae-133">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="356ae-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="356ae-134">已完成</span><span class="sxs-lookup"><span data-stu-id="356ae-134">Completed</span></span>|<span data-ttu-id="356ae-135">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="356ae-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="356ae-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="356ae-136">Deleted</span></span>|<span data-ttu-id="356ae-137">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="356ae-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="356ae-138">閒置</span><span class="sxs-lookup"><span data-stu-id="356ae-138">Idle</span></span>|<span data-ttu-id="356ae-139">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="356ae-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="356ae-140">已保存</span><span class="sxs-lookup"><span data-stu-id="356ae-140">Persisted</span></span>|<span data-ttu-id="356ae-141">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="356ae-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="356ae-142">已繼續</span><span class="sxs-lookup"><span data-stu-id="356ae-142">Resumed</span></span>|<span data-ttu-id="356ae-143">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="356ae-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="356ae-144">已啟動</span><span class="sxs-lookup"><span data-stu-id="356ae-144">Started</span></span>|<span data-ttu-id="356ae-145">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="356ae-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="356ae-146">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="356ae-146">UnhandledException</span></span>|<span data-ttu-id="356ae-147">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="356ae-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="356ae-148">Unloaded</span><span class="sxs-lookup"><span data-stu-id="356ae-148">Unloaded</span></span>|<span data-ttu-id="356ae-149">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="356ae-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="356ae-150">已取消</span><span class="sxs-lookup"><span data-stu-id="356ae-150">Canceled</span></span>|<span data-ttu-id="356ae-151">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="356ae-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="356ae-152">暫停</span><span class="sxs-lookup"><span data-stu-id="356ae-152">Suspended</span></span>|<span data-ttu-id="356ae-153">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="356ae-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="356ae-154">已終止</span><span class="sxs-lookup"><span data-stu-id="356ae-154">Terminated</span></span>|<span data-ttu-id="356ae-155">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="356ae-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="356ae-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="356ae-156">Unsuspended</span></span>|<span data-ttu-id="356ae-157">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="356ae-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="356ae-158">範例</span><span class="sxs-lookup"><span data-stu-id="356ae-158">Example</span></span>  
 <span data-ttu-id="356ae-159">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="356ae-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="356ae-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="356ae-160">See Also</span></span>  
 <span data-ttu-id="356ae-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="356ae-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="356ae-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="356ae-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="356ae-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="356ae-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="356ae-164">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="356ae-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="356ae-165">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="356ae-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
