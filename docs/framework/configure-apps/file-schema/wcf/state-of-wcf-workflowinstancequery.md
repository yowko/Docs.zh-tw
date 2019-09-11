---
title: <state>在 WCF 中，<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854959"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="f94ce-102">\<WCF、 \<workflowInstanceQuery > 的狀態 ></span><span class="sxs-lookup"><span data-stu-id="f94ce-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="f94ce-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="f94ce-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="f94ce-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f94ce-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f94ce-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f94ce-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="f94ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="f94ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="f94ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="f94ce-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="f94ce-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="f94ce-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="f94ce-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<狀態 >** ](states-of-wcf-workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="f94ce-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)</span></span>\
<span data-ttu-id="f94ce-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<狀態 >**</span><span class="sxs-lookup"><span data-stu-id="f94ce-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f94ce-115">語法</span><span class="sxs-lookup"><span data-stu-id="f94ce-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f94ce-116">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f94ce-116">Attributes and elements</span></span>

<span data-ttu-id="f94ce-117">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f94ce-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="f94ce-118">屬性</span><span class="sxs-lookup"><span data-stu-id="f94ce-118">Attributes</span></span>

|<span data-ttu-id="f94ce-119">屬性</span><span class="sxs-lookup"><span data-stu-id="f94ce-119">Attribute</span></span>|<span data-ttu-id="f94ce-120">說明</span><span class="sxs-lookup"><span data-stu-id="f94ce-120">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f94ce-121">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="f94ce-121">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f94ce-122">子元素</span><span class="sxs-lookup"><span data-stu-id="f94ce-122">Child elements</span></span>

<span data-ttu-id="f94ce-123">無。</span><span class="sxs-lookup"><span data-stu-id="f94ce-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f94ce-124">父元素</span><span class="sxs-lookup"><span data-stu-id="f94ce-124">Parent elements</span></span>

|<span data-ttu-id="f94ce-125">元素</span><span class="sxs-lookup"><span data-stu-id="f94ce-125">Element</span></span>|<span data-ttu-id="f94ce-126">說明</span><span class="sxs-lookup"><span data-stu-id="f94ce-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f94ce-127">\<states></span><span class="sxs-lookup"><span data-stu-id="f94ce-127">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="f94ce-128">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="f94ce-128">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f94ce-129">備註</span><span class="sxs-lookup"><span data-stu-id="f94ce-129">Remarks</span></span>  

<span data-ttu-id="f94ce-130">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="f94ce-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="f94ce-131">下表說明可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="f94ce-131">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="f94ce-132">State</span><span class="sxs-lookup"><span data-stu-id="f94ce-132">State</span></span>|<span data-ttu-id="f94ce-133">描述</span><span class="sxs-lookup"><span data-stu-id="f94ce-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f94ce-134">已中止</span><span class="sxs-lookup"><span data-stu-id="f94ce-134">Aborted</span></span>|<span data-ttu-id="f94ce-135">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="f94ce-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f94ce-136">已完成</span><span class="sxs-lookup"><span data-stu-id="f94ce-136">Completed</span></span>|<span data-ttu-id="f94ce-137">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="f94ce-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f94ce-138">Deleted</span><span class="sxs-lookup"><span data-stu-id="f94ce-138">Deleted</span></span>|<span data-ttu-id="f94ce-139">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="f94ce-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f94ce-140">閒置</span><span class="sxs-lookup"><span data-stu-id="f94ce-140">Idle</span></span>|<span data-ttu-id="f94ce-141">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="f94ce-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f94ce-142">已保存</span><span class="sxs-lookup"><span data-stu-id="f94ce-142">Persisted</span></span>|<span data-ttu-id="f94ce-143">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="f94ce-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f94ce-144">已繼續</span><span class="sxs-lookup"><span data-stu-id="f94ce-144">Resumed</span></span>|<span data-ttu-id="f94ce-145">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="f94ce-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f94ce-146">自</span><span class="sxs-lookup"><span data-stu-id="f94ce-146">Started</span></span>|<span data-ttu-id="f94ce-147">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="f94ce-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f94ce-148">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="f94ce-148">UnhandledException</span></span>|<span data-ttu-id="f94ce-149">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f94ce-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f94ce-150">已卸載</span><span class="sxs-lookup"><span data-stu-id="f94ce-150">Unloaded</span></span>|<span data-ttu-id="f94ce-151">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="f94ce-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f94ce-152">已取消</span><span class="sxs-lookup"><span data-stu-id="f94ce-152">Canceled</span></span>|<span data-ttu-id="f94ce-153">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="f94ce-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f94ce-154">擱置</span><span class="sxs-lookup"><span data-stu-id="f94ce-154">Suspended</span></span>|<span data-ttu-id="f94ce-155">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="f94ce-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f94ce-156">已終止</span><span class="sxs-lookup"><span data-stu-id="f94ce-156">Terminated</span></span>|<span data-ttu-id="f94ce-157">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="f94ce-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f94ce-158">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="f94ce-158">Unsuspended</span></span>|<span data-ttu-id="f94ce-159">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="f94ce-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f94ce-160">範例</span><span class="sxs-lookup"><span data-stu-id="f94ce-160">Example</span></span>

<span data-ttu-id="f94ce-161">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="f94ce-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="f94ce-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f94ce-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f94ce-163">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="f94ce-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f94ce-164">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="f94ce-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
