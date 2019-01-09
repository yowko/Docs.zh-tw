---
title: WCF 的 &lt;state&gt;、&lt;workflowInstanceQuery&gt;
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 168a6980e955f602ee60bff26461f06cb16c836a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145922"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="e9882-102">WCF 的 &lt;state&gt;、&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e9882-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="e9882-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="e9882-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e9882-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e9882-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e9882-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9882-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e9882-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="e9882-106">\<tracking></span></span>  
<span data-ttu-id="e9882-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="e9882-107">\<profiles></span></span>  
<span data-ttu-id="e9882-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e9882-108">\<trackingProfile></span></span>  
<span data-ttu-id="e9882-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="e9882-109">\<workflow></span></span>  
<span data-ttu-id="e9882-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="e9882-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e9882-111">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e9882-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e9882-112">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="e9882-112">\<states></span></span>  
<span data-ttu-id="e9882-113">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="e9882-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9882-114">語法</span><span class="sxs-lookup"><span data-stu-id="e9882-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9882-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e9882-115">Attributes and elements</span></span>

<span data-ttu-id="e9882-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e9882-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e9882-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e9882-117">Attributes</span></span>

|<span data-ttu-id="e9882-118">屬性</span><span class="sxs-lookup"><span data-stu-id="e9882-118">Attribute</span></span>|<span data-ttu-id="e9882-119">描述</span><span class="sxs-lookup"><span data-stu-id="e9882-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="e9882-120">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="e9882-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9882-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e9882-121">Child elements</span></span>

<span data-ttu-id="e9882-122">無。</span><span class="sxs-lookup"><span data-stu-id="e9882-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e9882-123">父元素</span><span class="sxs-lookup"><span data-stu-id="e9882-123">Parent elements</span></span>

|<span data-ttu-id="e9882-124">元素</span><span class="sxs-lookup"><span data-stu-id="e9882-124">Element</span></span>|<span data-ttu-id="e9882-125">描述</span><span class="sxs-lookup"><span data-stu-id="e9882-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9882-126">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="e9882-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="e9882-127">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="e9882-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9882-128">備註</span><span class="sxs-lookup"><span data-stu-id="e9882-128">Remarks</span></span>  

<span data-ttu-id="e9882-129">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="e9882-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="e9882-130">下表說明可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="e9882-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="e9882-131">狀況</span><span class="sxs-lookup"><span data-stu-id="e9882-131">State</span></span>|<span data-ttu-id="e9882-132">描述</span><span class="sxs-lookup"><span data-stu-id="e9882-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9882-133">已中止</span><span class="sxs-lookup"><span data-stu-id="e9882-133">Aborted</span></span>|<span data-ttu-id="e9882-134">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="e9882-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e9882-135">已完成</span><span class="sxs-lookup"><span data-stu-id="e9882-135">Completed</span></span>|<span data-ttu-id="e9882-136">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="e9882-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e9882-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="e9882-137">Deleted</span></span>|<span data-ttu-id="e9882-138">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="e9882-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e9882-139">閒置</span><span class="sxs-lookup"><span data-stu-id="e9882-139">Idle</span></span>|<span data-ttu-id="e9882-140">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="e9882-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e9882-141">已保存</span><span class="sxs-lookup"><span data-stu-id="e9882-141">Persisted</span></span>|<span data-ttu-id="e9882-142">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="e9882-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e9882-143">已繼續</span><span class="sxs-lookup"><span data-stu-id="e9882-143">Resumed</span></span>|<span data-ttu-id="e9882-144">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="e9882-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e9882-145">已啟動</span><span class="sxs-lookup"><span data-stu-id="e9882-145">Started</span></span>|<span data-ttu-id="e9882-146">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="e9882-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e9882-147">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="e9882-147">UnhandledException</span></span>|<span data-ttu-id="e9882-148">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9882-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e9882-149">Unloaded</span><span class="sxs-lookup"><span data-stu-id="e9882-149">Unloaded</span></span>|<span data-ttu-id="e9882-150">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="e9882-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e9882-151">已取消</span><span class="sxs-lookup"><span data-stu-id="e9882-151">Canceled</span></span>|<span data-ttu-id="e9882-152">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="e9882-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e9882-153">暫停</span><span class="sxs-lookup"><span data-stu-id="e9882-153">Suspended</span></span>|<span data-ttu-id="e9882-154">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="e9882-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e9882-155">已終止</span><span class="sxs-lookup"><span data-stu-id="e9882-155">Terminated</span></span>|<span data-ttu-id="e9882-156">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="e9882-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e9882-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="e9882-157">Unsuspended</span></span>|<span data-ttu-id="e9882-158">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="e9882-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9882-159">範例</span><span class="sxs-lookup"><span data-stu-id="e9882-159">Example</span></span>

<span data-ttu-id="e9882-160">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e9882-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="e9882-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9882-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e9882-162">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e9882-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e9882-163">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e9882-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
