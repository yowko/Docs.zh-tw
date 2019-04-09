---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 30cb2efa4c00c8b292a8ace6a03306d6ac76a7f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073118"
---
# <a name="states"></a><span data-ttu-id="1e8ec-101">\<states></span><span class="sxs-lookup"><span data-stu-id="1e8ec-101">\<states></span></span>
<span data-ttu-id="1e8ec-102">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="1e8ec-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1e8ec-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1e8ec-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1e8ec-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1e8ec-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="1e8ec-105">\<tracking></span></span>  
<span data-ttu-id="1e8ec-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1e8ec-106">\<trackingProfile></span></span>  
<span data-ttu-id="1e8ec-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="1e8ec-107">\<workflow></span></span>  
<span data-ttu-id="1e8ec-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="1e8ec-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="1e8ec-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="1e8ec-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="1e8ec-110">\<states></span><span class="sxs-lookup"><span data-stu-id="1e8ec-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e8ec-111">語法</span><span class="sxs-lookup"><span data-stu-id="1e8ec-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e8ec-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e8ec-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1e8ec-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e8ec-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1e8ec-114">Attributes</span></span>  
 <span data-ttu-id="1e8ec-115">無。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e8ec-116">子元素</span><span class="sxs-lookup"><span data-stu-id="1e8ec-116">Child Elements</span></span>  
  
|<span data-ttu-id="1e8ec-117">項目</span><span class="sxs-lookup"><span data-stu-id="1e8ec-117">Element</span></span>|<span data-ttu-id="1e8ec-118">描述</span><span class="sxs-lookup"><span data-stu-id="1e8ec-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e8ec-119">\<state></span><span class="sxs-lookup"><span data-stu-id="1e8ec-119">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="1e8ec-120">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e8ec-121">父項目</span><span class="sxs-lookup"><span data-stu-id="1e8ec-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1e8ec-122">項目</span><span class="sxs-lookup"><span data-stu-id="1e8ec-122">Element</span></span>|<span data-ttu-id="1e8ec-123">描述</span><span class="sxs-lookup"><span data-stu-id="1e8ec-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e8ec-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="1e8ec-124">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="1e8ec-125">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e8ec-126">備註</span><span class="sxs-lookup"><span data-stu-id="1e8ec-126">Remarks</span></span>  
 <span data-ttu-id="1e8ec-127">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="1e8ec-128">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="1e8ec-129">狀況</span><span class="sxs-lookup"><span data-stu-id="1e8ec-129">State</span></span>|<span data-ttu-id="1e8ec-130">描述</span><span class="sxs-lookup"><span data-stu-id="1e8ec-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e8ec-131">已中止</span><span class="sxs-lookup"><span data-stu-id="1e8ec-131">Aborted</span></span>|<span data-ttu-id="1e8ec-132">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1e8ec-133">已完成</span><span class="sxs-lookup"><span data-stu-id="1e8ec-133">Completed</span></span>|<span data-ttu-id="1e8ec-134">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1e8ec-135">Deleted</span><span class="sxs-lookup"><span data-stu-id="1e8ec-135">Deleted</span></span>|<span data-ttu-id="1e8ec-136">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1e8ec-137">閒置</span><span class="sxs-lookup"><span data-stu-id="1e8ec-137">Idle</span></span>|<span data-ttu-id="1e8ec-138">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1e8ec-139">已保存</span><span class="sxs-lookup"><span data-stu-id="1e8ec-139">Persisted</span></span>|<span data-ttu-id="1e8ec-140">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1e8ec-141">已繼續</span><span class="sxs-lookup"><span data-stu-id="1e8ec-141">Resumed</span></span>|<span data-ttu-id="1e8ec-142">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1e8ec-143">自</span><span class="sxs-lookup"><span data-stu-id="1e8ec-143">Started</span></span>|<span data-ttu-id="1e8ec-144">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1e8ec-145">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1e8ec-145">UnhandledException</span></span>|<span data-ttu-id="1e8ec-146">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1e8ec-147">已卸載</span><span class="sxs-lookup"><span data-stu-id="1e8ec-147">Unloaded</span></span>|<span data-ttu-id="1e8ec-148">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1e8ec-149">已取消</span><span class="sxs-lookup"><span data-stu-id="1e8ec-149">Canceled</span></span>|<span data-ttu-id="1e8ec-150">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1e8ec-151">擱置</span><span class="sxs-lookup"><span data-stu-id="1e8ec-151">Suspended</span></span>|<span data-ttu-id="1e8ec-152">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1e8ec-153">已終止</span><span class="sxs-lookup"><span data-stu-id="1e8ec-153">Terminated</span></span>|<span data-ttu-id="1e8ec-154">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1e8ec-155">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="1e8ec-155">Unsuspended</span></span>|<span data-ttu-id="1e8ec-156">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e8ec-157">範例</span><span class="sxs-lookup"><span data-stu-id="1e8ec-157">Example</span></span>  
 <span data-ttu-id="1e8ec-158">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="1e8ec-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e8ec-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e8ec-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1e8ec-160">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="1e8ec-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1e8ec-161">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="1e8ec-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
