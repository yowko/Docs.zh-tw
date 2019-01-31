---
title: <states> WCF 的 <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: fad6f9c8871f79e4a1e26c893eed86ba168f6d01
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281459"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="97e92-102">\<狀態 > 的 WCF， \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="97e92-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="97e92-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="97e92-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="97e92-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="97e92-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="97e92-105">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="97e92-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="97e92-106">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="97e92-106">\<profiles></span></span>  
<span data-ttu-id="97e92-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="97e92-107">\<trackingProfile></span></span>  
<span data-ttu-id="97e92-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="97e92-108">\<workflow></span></span>  
<span data-ttu-id="97e92-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="97e92-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="97e92-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="97e92-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="97e92-111">\<states></span><span class="sxs-lookup"><span data-stu-id="97e92-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e92-112">語法</span><span class="sxs-lookup"><span data-stu-id="97e92-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97e92-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="97e92-113">Attributes and elements</span></span>

<span data-ttu-id="97e92-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="97e92-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97e92-115">屬性</span><span class="sxs-lookup"><span data-stu-id="97e92-115">Attributes</span></span>  

<span data-ttu-id="97e92-116">無。</span><span class="sxs-lookup"><span data-stu-id="97e92-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97e92-117">子元素</span><span class="sxs-lookup"><span data-stu-id="97e92-117">Child elements</span></span>
  
|<span data-ttu-id="97e92-118">項目</span><span class="sxs-lookup"><span data-stu-id="97e92-118">Element</span></span>|<span data-ttu-id="97e92-119">描述</span><span class="sxs-lookup"><span data-stu-id="97e92-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97e92-120">\<states></span><span class="sxs-lookup"><span data-stu-id="97e92-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="97e92-121">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="97e92-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97e92-122">父元素</span><span class="sxs-lookup"><span data-stu-id="97e92-122">Parent elements</span></span>  
  
|<span data-ttu-id="97e92-123">元素</span><span class="sxs-lookup"><span data-stu-id="97e92-123">Element</span></span>|<span data-ttu-id="97e92-124">描述</span><span class="sxs-lookup"><span data-stu-id="97e92-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97e92-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="97e92-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="97e92-126">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="97e92-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97e92-127">備註</span><span class="sxs-lookup"><span data-stu-id="97e92-127">Remarks</span></span>

<span data-ttu-id="97e92-128">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="97e92-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="97e92-129">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="97e92-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="97e92-130">狀態</span><span class="sxs-lookup"><span data-stu-id="97e92-130">State</span></span>|<span data-ttu-id="97e92-131">描述</span><span class="sxs-lookup"><span data-stu-id="97e92-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97e92-132">已中止</span><span class="sxs-lookup"><span data-stu-id="97e92-132">Aborted</span></span>|<span data-ttu-id="97e92-133">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="97e92-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="97e92-134">已完成</span><span class="sxs-lookup"><span data-stu-id="97e92-134">Completed</span></span>|<span data-ttu-id="97e92-135">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="97e92-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="97e92-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="97e92-136">Deleted</span></span>|<span data-ttu-id="97e92-137">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="97e92-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="97e92-138">閒置</span><span class="sxs-lookup"><span data-stu-id="97e92-138">Idle</span></span>|<span data-ttu-id="97e92-139">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="97e92-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="97e92-140">已保存</span><span class="sxs-lookup"><span data-stu-id="97e92-140">Persisted</span></span>|<span data-ttu-id="97e92-141">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="97e92-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="97e92-142">已繼續</span><span class="sxs-lookup"><span data-stu-id="97e92-142">Resumed</span></span>|<span data-ttu-id="97e92-143">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="97e92-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="97e92-144">已啟動</span><span class="sxs-lookup"><span data-stu-id="97e92-144">Started</span></span>|<span data-ttu-id="97e92-145">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="97e92-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="97e92-146">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="97e92-146">UnhandledException</span></span>|<span data-ttu-id="97e92-147">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="97e92-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="97e92-148">Unloaded</span><span class="sxs-lookup"><span data-stu-id="97e92-148">Unloaded</span></span>|<span data-ttu-id="97e92-149">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="97e92-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="97e92-150">已取消</span><span class="sxs-lookup"><span data-stu-id="97e92-150">Canceled</span></span>|<span data-ttu-id="97e92-151">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="97e92-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="97e92-152">暫停</span><span class="sxs-lookup"><span data-stu-id="97e92-152">Suspended</span></span>|<span data-ttu-id="97e92-153">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="97e92-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="97e92-154">已終止</span><span class="sxs-lookup"><span data-stu-id="97e92-154">Terminated</span></span>|<span data-ttu-id="97e92-155">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="97e92-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="97e92-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="97e92-156">Unsuspended</span></span>|<span data-ttu-id="97e92-157">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="97e92-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97e92-158">範例</span><span class="sxs-lookup"><span data-stu-id="97e92-158">Example</span></span>

<span data-ttu-id="97e92-159">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="97e92-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="97e92-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97e92-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="97e92-161">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="97e92-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="97e92-162">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="97e92-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
