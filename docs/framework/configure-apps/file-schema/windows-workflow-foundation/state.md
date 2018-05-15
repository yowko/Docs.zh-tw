---
title: '&lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 327a5e98a9ecf6ba23eaf47c3d6d73bfb7852ee7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltstategt"></a><span data-ttu-id="32c0f-102">&lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="32c0f-102">&lt;state&gt;</span></span>
<span data-ttu-id="32c0f-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="32c0f-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="32c0f-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="32c0f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="32c0f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32c0f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="32c0f-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="32c0f-106">\<tracking></span></span>  
<span data-ttu-id="32c0f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="32c0f-107">\<trackingProfile></span></span>  
<span data-ttu-id="32c0f-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="32c0f-108">\<workflow></span></span>  
<span data-ttu-id="32c0f-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="32c0f-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="32c0f-110">\<w ></span><span class="sxs-lookup"><span data-stu-id="32c0f-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="32c0f-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="32c0f-111">\<states></span></span>  
<span data-ttu-id="32c0f-112">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="32c0f-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c0f-113">語法</span><span class="sxs-lookup"><span data-stu-id="32c0f-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c0f-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32c0f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="32c0f-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="32c0f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c0f-116">屬性</span><span class="sxs-lookup"><span data-stu-id="32c0f-116">Attributes</span></span>  
  
|<span data-ttu-id="32c0f-117">屬性</span><span class="sxs-lookup"><span data-stu-id="32c0f-117">Attribute</span></span>|<span data-ttu-id="32c0f-118">描述</span><span class="sxs-lookup"><span data-stu-id="32c0f-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32c0f-119">name</span><span class="sxs-lookup"><span data-stu-id="32c0f-119">name</span></span>|<span data-ttu-id="32c0f-120">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="32c0f-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32c0f-121">子項目</span><span class="sxs-lookup"><span data-stu-id="32c0f-121">Child Elements</span></span>  
 <span data-ttu-id="32c0f-122">無。</span><span class="sxs-lookup"><span data-stu-id="32c0f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32c0f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="32c0f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="32c0f-124">項目</span><span class="sxs-lookup"><span data-stu-id="32c0f-124">Element</span></span>|<span data-ttu-id="32c0f-125">描述</span><span class="sxs-lookup"><span data-stu-id="32c0f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32c0f-126">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="32c0f-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="32c0f-127">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="32c0f-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32c0f-128">備註</span><span class="sxs-lookup"><span data-stu-id="32c0f-128">Remarks</span></span>  
 <span data-ttu-id="32c0f-129">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="32c0f-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="32c0f-130">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="32c0f-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="32c0f-131">狀態</span><span class="sxs-lookup"><span data-stu-id="32c0f-131">State</span></span>|<span data-ttu-id="32c0f-132">描述</span><span class="sxs-lookup"><span data-stu-id="32c0f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="32c0f-133">已中止</span><span class="sxs-lookup"><span data-stu-id="32c0f-133">Aborted</span></span>|<span data-ttu-id="32c0f-134">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="32c0f-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="32c0f-135">已完成</span><span class="sxs-lookup"><span data-stu-id="32c0f-135">Completed</span></span>|<span data-ttu-id="32c0f-136">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="32c0f-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="32c0f-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="32c0f-137">Deleted</span></span>|<span data-ttu-id="32c0f-138">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="32c0f-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="32c0f-139">閒置</span><span class="sxs-lookup"><span data-stu-id="32c0f-139">Idle</span></span>|<span data-ttu-id="32c0f-140">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="32c0f-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="32c0f-141">已保存</span><span class="sxs-lookup"><span data-stu-id="32c0f-141">Persisted</span></span>|<span data-ttu-id="32c0f-142">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="32c0f-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="32c0f-143">已繼續</span><span class="sxs-lookup"><span data-stu-id="32c0f-143">Resumed</span></span>|<span data-ttu-id="32c0f-144">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="32c0f-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="32c0f-145">已啟動</span><span class="sxs-lookup"><span data-stu-id="32c0f-145">Started</span></span>|<span data-ttu-id="32c0f-146">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="32c0f-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="32c0f-147">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="32c0f-147">UnhandledException</span></span>|<span data-ttu-id="32c0f-148">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="32c0f-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="32c0f-149">Unloaded</span><span class="sxs-lookup"><span data-stu-id="32c0f-149">Unloaded</span></span>|<span data-ttu-id="32c0f-150">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="32c0f-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="32c0f-151">已取消</span><span class="sxs-lookup"><span data-stu-id="32c0f-151">Canceled</span></span>|<span data-ttu-id="32c0f-152">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="32c0f-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="32c0f-153">暫停</span><span class="sxs-lookup"><span data-stu-id="32c0f-153">Suspended</span></span>|<span data-ttu-id="32c0f-154">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="32c0f-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="32c0f-155">已終止</span><span class="sxs-lookup"><span data-stu-id="32c0f-155">Terminated</span></span>|<span data-ttu-id="32c0f-156">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="32c0f-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="32c0f-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="32c0f-157">Unsuspended</span></span>|<span data-ttu-id="32c0f-158">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="32c0f-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="32c0f-159">範例</span><span class="sxs-lookup"><span data-stu-id="32c0f-159">Example</span></span>  
 <span data-ttu-id="32c0f-160">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="32c0f-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32c0f-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32c0f-161">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>      
 [<span data-ttu-id="32c0f-162">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="32c0f-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="32c0f-163">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="32c0f-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
