---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947399"
---
# <a name="states"></a><span data-ttu-id="8d1c5-101">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="8d1c5-101">\<states></span></span>
<span data-ttu-id="8d1c5-102">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="8d1c5-103">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8d1c5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8d1c5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8d1c5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8d1c5-105">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="8d1c5-105">\<tracking></span></span>  
<span data-ttu-id="8d1c5-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8d1c5-106">\<trackingProfile></span></span>  
<span data-ttu-id="8d1c5-107">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="8d1c5-107">\<workflow></span></span>  
<span data-ttu-id="8d1c5-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="8d1c5-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="8d1c5-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="8d1c5-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="8d1c5-110">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="8d1c5-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1c5-111">語法</span><span class="sxs-lookup"><span data-stu-id="8d1c5-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d1c5-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8d1c5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8d1c5-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d1c5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8d1c5-114">Attributes</span></span>  
 <span data-ttu-id="8d1c5-115">無。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d1c5-116">子元素</span><span class="sxs-lookup"><span data-stu-id="8d1c5-116">Child Elements</span></span>  
  
|<span data-ttu-id="8d1c5-117">項目</span><span class="sxs-lookup"><span data-stu-id="8d1c5-117">Element</span></span>|<span data-ttu-id="8d1c5-118">描述</span><span class="sxs-lookup"><span data-stu-id="8d1c5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d1c5-119">\<state></span><span class="sxs-lookup"><span data-stu-id="8d1c5-119">\<state></span></span>](states.md)|<span data-ttu-id="8d1c5-120">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d1c5-121">父項目</span><span class="sxs-lookup"><span data-stu-id="8d1c5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8d1c5-122">項目</span><span class="sxs-lookup"><span data-stu-id="8d1c5-122">Element</span></span>|<span data-ttu-id="8d1c5-123">說明</span><span class="sxs-lookup"><span data-stu-id="8d1c5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d1c5-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="8d1c5-124">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="8d1c5-125">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d1c5-126">備註</span><span class="sxs-lookup"><span data-stu-id="8d1c5-126">Remarks</span></span>  
 <span data-ttu-id="8d1c5-127">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="8d1c5-128">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="8d1c5-129">State</span><span class="sxs-lookup"><span data-stu-id="8d1c5-129">State</span></span>|<span data-ttu-id="8d1c5-130">描述</span><span class="sxs-lookup"><span data-stu-id="8d1c5-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d1c5-131">已中止</span><span class="sxs-lookup"><span data-stu-id="8d1c5-131">Aborted</span></span>|<span data-ttu-id="8d1c5-132">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="8d1c5-133">已完成</span><span class="sxs-lookup"><span data-stu-id="8d1c5-133">Completed</span></span>|<span data-ttu-id="8d1c5-134">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="8d1c5-135">Deleted</span><span class="sxs-lookup"><span data-stu-id="8d1c5-135">Deleted</span></span>|<span data-ttu-id="8d1c5-136">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="8d1c5-137">閒置</span><span class="sxs-lookup"><span data-stu-id="8d1c5-137">Idle</span></span>|<span data-ttu-id="8d1c5-138">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="8d1c5-139">已保存</span><span class="sxs-lookup"><span data-stu-id="8d1c5-139">Persisted</span></span>|<span data-ttu-id="8d1c5-140">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="8d1c5-141">已繼續</span><span class="sxs-lookup"><span data-stu-id="8d1c5-141">Resumed</span></span>|<span data-ttu-id="8d1c5-142">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="8d1c5-143">自</span><span class="sxs-lookup"><span data-stu-id="8d1c5-143">Started</span></span>|<span data-ttu-id="8d1c5-144">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="8d1c5-145">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="8d1c5-145">UnhandledException</span></span>|<span data-ttu-id="8d1c5-146">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="8d1c5-147">已卸載</span><span class="sxs-lookup"><span data-stu-id="8d1c5-147">Unloaded</span></span>|<span data-ttu-id="8d1c5-148">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="8d1c5-149">已取消</span><span class="sxs-lookup"><span data-stu-id="8d1c5-149">Canceled</span></span>|<span data-ttu-id="8d1c5-150">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="8d1c5-151">擱置</span><span class="sxs-lookup"><span data-stu-id="8d1c5-151">Suspended</span></span>|<span data-ttu-id="8d1c5-152">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="8d1c5-153">已終止</span><span class="sxs-lookup"><span data-stu-id="8d1c5-153">Terminated</span></span>|<span data-ttu-id="8d1c5-154">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="8d1c5-155">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="8d1c5-155">Unsuspended</span></span>|<span data-ttu-id="8d1c5-156">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d1c5-157">範例</span><span class="sxs-lookup"><span data-stu-id="8d1c5-157">Example</span></span>  
 <span data-ttu-id="8d1c5-158">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="8d1c5-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d1c5-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d1c5-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8d1c5-160">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="8d1c5-160">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8d1c5-161">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="8d1c5-161">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
