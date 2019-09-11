---
title: <states>在 WCF 中，<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855035"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="24db0-102">\<\<workflowInstanceQuery WCF 的狀態 > ></span><span class="sxs-lookup"><span data-stu-id="24db0-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="24db0-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="24db0-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="24db0-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="24db0-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24db0-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="24db0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="24db0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="24db0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="24db0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="24db0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="24db0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="24db0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="24db0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="24db0-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<狀態 >**</span><span class="sxs-lookup"><span data-stu-id="24db0-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24db0-114">語法</span><span class="sxs-lookup"><span data-stu-id="24db0-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24db0-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="24db0-115">Attributes and elements</span></span>

<span data-ttu-id="24db0-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="24db0-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24db0-117">屬性</span><span class="sxs-lookup"><span data-stu-id="24db0-117">Attributes</span></span>  

<span data-ttu-id="24db0-118">無。</span><span class="sxs-lookup"><span data-stu-id="24db0-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24db0-119">子元素</span><span class="sxs-lookup"><span data-stu-id="24db0-119">Child elements</span></span>
  
|<span data-ttu-id="24db0-120">項目</span><span class="sxs-lookup"><span data-stu-id="24db0-120">Element</span></span>|<span data-ttu-id="24db0-121">描述</span><span class="sxs-lookup"><span data-stu-id="24db0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24db0-122">\<states></span><span class="sxs-lookup"><span data-stu-id="24db0-122">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="24db0-123">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="24db0-123">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24db0-124">父元素</span><span class="sxs-lookup"><span data-stu-id="24db0-124">Parent elements</span></span>  
  
|<span data-ttu-id="24db0-125">元素</span><span class="sxs-lookup"><span data-stu-id="24db0-125">Element</span></span>|<span data-ttu-id="24db0-126">說明</span><span class="sxs-lookup"><span data-stu-id="24db0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24db0-127">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="24db0-127">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="24db0-128">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="24db0-128">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24db0-129">備註</span><span class="sxs-lookup"><span data-stu-id="24db0-129">Remarks</span></span>

<span data-ttu-id="24db0-130">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="24db0-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="24db0-131">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="24db0-131">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="24db0-132">State</span><span class="sxs-lookup"><span data-stu-id="24db0-132">State</span></span>|<span data-ttu-id="24db0-133">描述</span><span class="sxs-lookup"><span data-stu-id="24db0-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24db0-134">已中止</span><span class="sxs-lookup"><span data-stu-id="24db0-134">Aborted</span></span>|<span data-ttu-id="24db0-135">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="24db0-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="24db0-136">已完成</span><span class="sxs-lookup"><span data-stu-id="24db0-136">Completed</span></span>|<span data-ttu-id="24db0-137">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="24db0-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="24db0-138">Deleted</span><span class="sxs-lookup"><span data-stu-id="24db0-138">Deleted</span></span>|<span data-ttu-id="24db0-139">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="24db0-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="24db0-140">閒置</span><span class="sxs-lookup"><span data-stu-id="24db0-140">Idle</span></span>|<span data-ttu-id="24db0-141">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="24db0-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="24db0-142">已保存</span><span class="sxs-lookup"><span data-stu-id="24db0-142">Persisted</span></span>|<span data-ttu-id="24db0-143">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="24db0-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="24db0-144">已繼續</span><span class="sxs-lookup"><span data-stu-id="24db0-144">Resumed</span></span>|<span data-ttu-id="24db0-145">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="24db0-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="24db0-146">自</span><span class="sxs-lookup"><span data-stu-id="24db0-146">Started</span></span>|<span data-ttu-id="24db0-147">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="24db0-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="24db0-148">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="24db0-148">UnhandledException</span></span>|<span data-ttu-id="24db0-149">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24db0-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="24db0-150">已卸載</span><span class="sxs-lookup"><span data-stu-id="24db0-150">Unloaded</span></span>|<span data-ttu-id="24db0-151">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="24db0-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="24db0-152">已取消</span><span class="sxs-lookup"><span data-stu-id="24db0-152">Canceled</span></span>|<span data-ttu-id="24db0-153">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="24db0-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="24db0-154">擱置</span><span class="sxs-lookup"><span data-stu-id="24db0-154">Suspended</span></span>|<span data-ttu-id="24db0-155">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="24db0-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="24db0-156">已終止</span><span class="sxs-lookup"><span data-stu-id="24db0-156">Terminated</span></span>|<span data-ttu-id="24db0-157">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="24db0-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="24db0-158">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="24db0-158">Unsuspended</span></span>|<span data-ttu-id="24db0-159">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="24db0-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24db0-160">範例</span><span class="sxs-lookup"><span data-stu-id="24db0-160">Example</span></span>

<span data-ttu-id="24db0-161">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="24db0-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="24db0-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24db0-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="24db0-163">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="24db0-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="24db0-164">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="24db0-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
