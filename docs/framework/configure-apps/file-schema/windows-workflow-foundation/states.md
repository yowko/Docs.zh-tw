---
title: '&lt;狀態&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fe02106d8d7f70cb328214c7e464d80a41b75528
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltstatesgt"></a><span data-ttu-id="04f78-102">&lt;狀態&gt;</span><span class="sxs-lookup"><span data-stu-id="04f78-102">&lt;states&gt;</span></span>
<span data-ttu-id="04f78-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="04f78-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="04f78-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="04f78-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="04f78-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04f78-105">\<system.serviceModel></span></span>  
<span data-ttu-id="04f78-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="04f78-106">\<tracking></span></span>  
<span data-ttu-id="04f78-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="04f78-107">\<trackingProfile></span></span>  
<span data-ttu-id="04f78-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="04f78-108">\<workflow></span></span>  
<span data-ttu-id="04f78-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="04f78-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="04f78-110">\<w ></span><span class="sxs-lookup"><span data-stu-id="04f78-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="04f78-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="04f78-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f78-112">語法</span><span class="sxs-lookup"><span data-stu-id="04f78-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04f78-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04f78-113">Attributes and Elements</span></span>  
 <span data-ttu-id="04f78-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="04f78-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04f78-115">屬性</span><span class="sxs-lookup"><span data-stu-id="04f78-115">Attributes</span></span>  
 <span data-ttu-id="04f78-116">無。</span><span class="sxs-lookup"><span data-stu-id="04f78-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04f78-117">子項目</span><span class="sxs-lookup"><span data-stu-id="04f78-117">Child Elements</span></span>  
  
|<span data-ttu-id="04f78-118">項目</span><span class="sxs-lookup"><span data-stu-id="04f78-118">Element</span></span>|<span data-ttu-id="04f78-119">描述</span><span class="sxs-lookup"><span data-stu-id="04f78-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04f78-120">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="04f78-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="04f78-121">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="04f78-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04f78-122">父項目</span><span class="sxs-lookup"><span data-stu-id="04f78-122">Parent Elements</span></span>  
  
|<span data-ttu-id="04f78-123">項目</span><span class="sxs-lookup"><span data-stu-id="04f78-123">Element</span></span>|<span data-ttu-id="04f78-124">描述</span><span class="sxs-lookup"><span data-stu-id="04f78-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04f78-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="04f78-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="04f78-126">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="04f78-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04f78-127">備註</span><span class="sxs-lookup"><span data-stu-id="04f78-127">Remarks</span></span>  
 <span data-ttu-id="04f78-128">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="04f78-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="04f78-129">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="04f78-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="04f78-130">狀態</span><span class="sxs-lookup"><span data-stu-id="04f78-130">State</span></span>|<span data-ttu-id="04f78-131">描述</span><span class="sxs-lookup"><span data-stu-id="04f78-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04f78-132">已中止</span><span class="sxs-lookup"><span data-stu-id="04f78-132">Aborted</span></span>|<span data-ttu-id="04f78-133">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="04f78-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="04f78-134">已完成</span><span class="sxs-lookup"><span data-stu-id="04f78-134">Completed</span></span>|<span data-ttu-id="04f78-135">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="04f78-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="04f78-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="04f78-136">Deleted</span></span>|<span data-ttu-id="04f78-137">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="04f78-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="04f78-138">閒置</span><span class="sxs-lookup"><span data-stu-id="04f78-138">Idle</span></span>|<span data-ttu-id="04f78-139">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="04f78-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="04f78-140">已保存</span><span class="sxs-lookup"><span data-stu-id="04f78-140">Persisted</span></span>|<span data-ttu-id="04f78-141">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="04f78-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="04f78-142">已繼續</span><span class="sxs-lookup"><span data-stu-id="04f78-142">Resumed</span></span>|<span data-ttu-id="04f78-143">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="04f78-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="04f78-144">已啟動</span><span class="sxs-lookup"><span data-stu-id="04f78-144">Started</span></span>|<span data-ttu-id="04f78-145">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="04f78-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="04f78-146">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="04f78-146">UnhandledException</span></span>|<span data-ttu-id="04f78-147">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04f78-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="04f78-148">Unloaded</span><span class="sxs-lookup"><span data-stu-id="04f78-148">Unloaded</span></span>|<span data-ttu-id="04f78-149">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="04f78-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="04f78-150">已取消</span><span class="sxs-lookup"><span data-stu-id="04f78-150">Canceled</span></span>|<span data-ttu-id="04f78-151">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="04f78-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="04f78-152">暫停</span><span class="sxs-lookup"><span data-stu-id="04f78-152">Suspended</span></span>|<span data-ttu-id="04f78-153">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="04f78-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="04f78-154">已終止</span><span class="sxs-lookup"><span data-stu-id="04f78-154">Terminated</span></span>|<span data-ttu-id="04f78-155">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="04f78-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="04f78-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="04f78-156">Unsuspended</span></span>|<span data-ttu-id="04f78-157">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="04f78-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="04f78-158">範例</span><span class="sxs-lookup"><span data-stu-id="04f78-158">Example</span></span>  
 <span data-ttu-id="04f78-159">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="04f78-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04f78-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04f78-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="04f78-161">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="04f78-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="04f78-162">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="04f78-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
