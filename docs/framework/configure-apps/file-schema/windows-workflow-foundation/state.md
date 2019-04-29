---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 6f1a9474f3f12005df364a6fb84dc63aa1b68e04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796158"
---
# <a name="state"></a><span data-ttu-id="b659d-101">\<state></span><span class="sxs-lookup"><span data-stu-id="b659d-101">\<state></span></span>
<span data-ttu-id="b659d-102">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="b659d-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="b659d-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b659d-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b659d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b659d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b659d-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b659d-105">\<tracking></span></span>  
<span data-ttu-id="b659d-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b659d-106">\<trackingProfile></span></span>  
<span data-ttu-id="b659d-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b659d-107">\<workflow></span></span>  
<span data-ttu-id="b659d-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="b659d-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="b659d-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="b659d-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="b659d-110">\<states></span><span class="sxs-lookup"><span data-stu-id="b659d-110">\<states></span></span>  
<span data-ttu-id="b659d-111">\<state></span><span class="sxs-lookup"><span data-stu-id="b659d-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b659d-112">語法</span><span class="sxs-lookup"><span data-stu-id="b659d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b659d-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b659d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b659d-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b659d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b659d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b659d-115">Attributes</span></span>  
  
|<span data-ttu-id="b659d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b659d-116">Attribute</span></span>|<span data-ttu-id="b659d-117">描述</span><span class="sxs-lookup"><span data-stu-id="b659d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b659d-118">名稱</span><span class="sxs-lookup"><span data-stu-id="b659d-118">name</span></span>|<span data-ttu-id="b659d-119">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="b659d-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b659d-120">子元素</span><span class="sxs-lookup"><span data-stu-id="b659d-120">Child Elements</span></span>  
 <span data-ttu-id="b659d-121">無。</span><span class="sxs-lookup"><span data-stu-id="b659d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b659d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="b659d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b659d-123">項目</span><span class="sxs-lookup"><span data-stu-id="b659d-123">Element</span></span>|<span data-ttu-id="b659d-124">描述</span><span class="sxs-lookup"><span data-stu-id="b659d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b659d-125">\<states></span><span class="sxs-lookup"><span data-stu-id="b659d-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="b659d-126">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="b659d-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b659d-127">備註</span><span class="sxs-lookup"><span data-stu-id="b659d-127">Remarks</span></span>  
 <span data-ttu-id="b659d-128">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="b659d-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="b659d-129">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="b659d-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="b659d-130">狀況</span><span class="sxs-lookup"><span data-stu-id="b659d-130">State</span></span>|<span data-ttu-id="b659d-131">描述</span><span class="sxs-lookup"><span data-stu-id="b659d-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b659d-132">已中止</span><span class="sxs-lookup"><span data-stu-id="b659d-132">Aborted</span></span>|<span data-ttu-id="b659d-133">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="b659d-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b659d-134">已完成</span><span class="sxs-lookup"><span data-stu-id="b659d-134">Completed</span></span>|<span data-ttu-id="b659d-135">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="b659d-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="b659d-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="b659d-136">Deleted</span></span>|<span data-ttu-id="b659d-137">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="b659d-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="b659d-138">閒置</span><span class="sxs-lookup"><span data-stu-id="b659d-138">Idle</span></span>|<span data-ttu-id="b659d-139">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="b659d-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="b659d-140">已保存</span><span class="sxs-lookup"><span data-stu-id="b659d-140">Persisted</span></span>|<span data-ttu-id="b659d-141">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="b659d-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="b659d-142">已繼續</span><span class="sxs-lookup"><span data-stu-id="b659d-142">Resumed</span></span>|<span data-ttu-id="b659d-143">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="b659d-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="b659d-144">自</span><span class="sxs-lookup"><span data-stu-id="b659d-144">Started</span></span>|<span data-ttu-id="b659d-145">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="b659d-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="b659d-146">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="b659d-146">UnhandledException</span></span>|<span data-ttu-id="b659d-147">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b659d-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="b659d-148">已卸載</span><span class="sxs-lookup"><span data-stu-id="b659d-148">Unloaded</span></span>|<span data-ttu-id="b659d-149">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="b659d-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="b659d-150">已取消</span><span class="sxs-lookup"><span data-stu-id="b659d-150">Canceled</span></span>|<span data-ttu-id="b659d-151">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="b659d-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="b659d-152">擱置</span><span class="sxs-lookup"><span data-stu-id="b659d-152">Suspended</span></span>|<span data-ttu-id="b659d-153">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="b659d-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="b659d-154">已終止</span><span class="sxs-lookup"><span data-stu-id="b659d-154">Terminated</span></span>|<span data-ttu-id="b659d-155">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="b659d-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="b659d-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="b659d-156">Unsuspended</span></span>|<span data-ttu-id="b659d-157">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="b659d-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b659d-158">範例</span><span class="sxs-lookup"><span data-stu-id="b659d-158">Example</span></span>  
 <span data-ttu-id="b659d-159">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b659d-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b659d-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b659d-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b659d-161">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b659d-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b659d-162">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b659d-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
