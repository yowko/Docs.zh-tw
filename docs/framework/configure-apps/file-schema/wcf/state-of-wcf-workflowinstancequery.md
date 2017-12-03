---
title: "WCF 的 &lt;state&gt;、&lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d6edb83370f36b73955ab9d619c8b956f36a007e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="78e95-102">WCF 的 &lt;state&gt;、&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="78e95-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="78e95-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="78e95-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="78e95-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="78e95-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="78e95-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="78e95-105">\<system.serviceModel></span></span>  
<span data-ttu-id="78e95-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="78e95-106">\<tracking></span></span>  
<span data-ttu-id="78e95-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="78e95-107">\<trackingProfile></span></span>  
<span data-ttu-id="78e95-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="78e95-108">\<workflow></span></span>  
<span data-ttu-id="78e95-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="78e95-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="78e95-110">\<w ></span><span class="sxs-lookup"><span data-stu-id="78e95-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="78e95-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="78e95-111">\<states></span></span>  
<span data-ttu-id="78e95-112">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="78e95-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e95-113">語法</span><span class="sxs-lookup"><span data-stu-id="78e95-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78e95-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="78e95-114">Attributes and Elements</span></span>  
 <span data-ttu-id="78e95-115">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="78e95-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78e95-116">屬性</span><span class="sxs-lookup"><span data-stu-id="78e95-116">Attributes</span></span>  
  
|<span data-ttu-id="78e95-117">屬性</span><span class="sxs-lookup"><span data-stu-id="78e95-117">Attribute</span></span>|<span data-ttu-id="78e95-118">描述</span><span class="sxs-lookup"><span data-stu-id="78e95-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78e95-119">name</span><span class="sxs-lookup"><span data-stu-id="78e95-119">name</span></span>|<span data-ttu-id="78e95-120">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="78e95-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78e95-121">子元素</span><span class="sxs-lookup"><span data-stu-id="78e95-121">Child Elements</span></span>  
 <span data-ttu-id="78e95-122">無。</span><span class="sxs-lookup"><span data-stu-id="78e95-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78e95-123">父項目</span><span class="sxs-lookup"><span data-stu-id="78e95-123">Parent Elements</span></span>  
  
|<span data-ttu-id="78e95-124">項目</span><span class="sxs-lookup"><span data-stu-id="78e95-124">Element</span></span>|<span data-ttu-id="78e95-125">說明</span><span class="sxs-lookup"><span data-stu-id="78e95-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78e95-126">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="78e95-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="78e95-127">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="78e95-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e95-128">備註</span><span class="sxs-lookup"><span data-stu-id="78e95-128">Remarks</span></span>  
 <span data-ttu-id="78e95-129">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="78e95-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="78e95-130">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="78e95-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="78e95-131">狀態</span><span class="sxs-lookup"><span data-stu-id="78e95-131">State</span></span>|<span data-ttu-id="78e95-132">描述</span><span class="sxs-lookup"><span data-stu-id="78e95-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78e95-133">已中止</span><span class="sxs-lookup"><span data-stu-id="78e95-133">Aborted</span></span>|<span data-ttu-id="78e95-134">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="78e95-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="78e95-135">已完成</span><span class="sxs-lookup"><span data-stu-id="78e95-135">Completed</span></span>|<span data-ttu-id="78e95-136">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="78e95-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="78e95-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="78e95-137">Deleted</span></span>|<span data-ttu-id="78e95-138">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="78e95-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="78e95-139">閒置</span><span class="sxs-lookup"><span data-stu-id="78e95-139">Idle</span></span>|<span data-ttu-id="78e95-140">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="78e95-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="78e95-141">已保存</span><span class="sxs-lookup"><span data-stu-id="78e95-141">Persisted</span></span>|<span data-ttu-id="78e95-142">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="78e95-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="78e95-143">已繼續</span><span class="sxs-lookup"><span data-stu-id="78e95-143">Resumed</span></span>|<span data-ttu-id="78e95-144">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="78e95-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="78e95-145">已啟動</span><span class="sxs-lookup"><span data-stu-id="78e95-145">Started</span></span>|<span data-ttu-id="78e95-146">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="78e95-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="78e95-147">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="78e95-147">UnhandledException</span></span>|<span data-ttu-id="78e95-148">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="78e95-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="78e95-149">Unloaded</span><span class="sxs-lookup"><span data-stu-id="78e95-149">Unloaded</span></span>|<span data-ttu-id="78e95-150">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="78e95-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="78e95-151">已取消</span><span class="sxs-lookup"><span data-stu-id="78e95-151">Canceled</span></span>|<span data-ttu-id="78e95-152">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="78e95-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="78e95-153">暫停</span><span class="sxs-lookup"><span data-stu-id="78e95-153">Suspended</span></span>|<span data-ttu-id="78e95-154">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="78e95-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="78e95-155">已終止</span><span class="sxs-lookup"><span data-stu-id="78e95-155">Terminated</span></span>|<span data-ttu-id="78e95-156">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="78e95-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="78e95-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="78e95-157">Unsuspended</span></span>|<span data-ttu-id="78e95-158">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="78e95-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="78e95-159">範例</span><span class="sxs-lookup"><span data-stu-id="78e95-159">Example</span></span>  
 <span data-ttu-id="78e95-160">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="78e95-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78e95-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78e95-161">See Also</span></span>  
 <span data-ttu-id="78e95-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78e95-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="78e95-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78e95-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="78e95-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78e95-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="78e95-165">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="78e95-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="78e95-166">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="78e95-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
