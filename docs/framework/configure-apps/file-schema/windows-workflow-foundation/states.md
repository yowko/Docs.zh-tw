---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398611"
---
# <a name="states"></a><span data-ttu-id="0966d-101">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="0966d-101">\<states></span></span>
<span data-ttu-id="0966d-102">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="0966d-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="0966d-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0966d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0966d-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0966d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="0966d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="0966d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="0966d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="0966d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="0966d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="0966d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<狀態 >**</span><span class="sxs-lookup"><span data-stu-id="0966d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0966d-112">語法</span><span class="sxs-lookup"><span data-stu-id="0966d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0966d-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0966d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0966d-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0966d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0966d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0966d-115">Attributes</span></span>  
 <span data-ttu-id="0966d-116">無。</span><span class="sxs-lookup"><span data-stu-id="0966d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0966d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0966d-117">Child Elements</span></span>  
  
|<span data-ttu-id="0966d-118">項目</span><span class="sxs-lookup"><span data-stu-id="0966d-118">Element</span></span>|<span data-ttu-id="0966d-119">描述</span><span class="sxs-lookup"><span data-stu-id="0966d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0966d-120">\<state></span><span class="sxs-lookup"><span data-stu-id="0966d-120">\<state></span></span>](states.md)|<span data-ttu-id="0966d-121">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="0966d-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0966d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="0966d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0966d-123">項目</span><span class="sxs-lookup"><span data-stu-id="0966d-123">Element</span></span>|<span data-ttu-id="0966d-124">說明</span><span class="sxs-lookup"><span data-stu-id="0966d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0966d-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="0966d-125">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="0966d-126">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="0966d-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0966d-127">備註</span><span class="sxs-lookup"><span data-stu-id="0966d-127">Remarks</span></span>  
 <span data-ttu-id="0966d-128">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="0966d-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="0966d-129">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="0966d-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="0966d-130">State</span><span class="sxs-lookup"><span data-stu-id="0966d-130">State</span></span>|<span data-ttu-id="0966d-131">描述</span><span class="sxs-lookup"><span data-stu-id="0966d-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0966d-132">已中止</span><span class="sxs-lookup"><span data-stu-id="0966d-132">Aborted</span></span>|<span data-ttu-id="0966d-133">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="0966d-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="0966d-134">已完成</span><span class="sxs-lookup"><span data-stu-id="0966d-134">Completed</span></span>|<span data-ttu-id="0966d-135">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="0966d-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="0966d-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="0966d-136">Deleted</span></span>|<span data-ttu-id="0966d-137">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="0966d-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="0966d-138">閒置</span><span class="sxs-lookup"><span data-stu-id="0966d-138">Idle</span></span>|<span data-ttu-id="0966d-139">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="0966d-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="0966d-140">已保存</span><span class="sxs-lookup"><span data-stu-id="0966d-140">Persisted</span></span>|<span data-ttu-id="0966d-141">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="0966d-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="0966d-142">已繼續</span><span class="sxs-lookup"><span data-stu-id="0966d-142">Resumed</span></span>|<span data-ttu-id="0966d-143">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="0966d-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="0966d-144">自</span><span class="sxs-lookup"><span data-stu-id="0966d-144">Started</span></span>|<span data-ttu-id="0966d-145">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="0966d-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="0966d-146">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="0966d-146">UnhandledException</span></span>|<span data-ttu-id="0966d-147">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0966d-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="0966d-148">已卸載</span><span class="sxs-lookup"><span data-stu-id="0966d-148">Unloaded</span></span>|<span data-ttu-id="0966d-149">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="0966d-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="0966d-150">已取消</span><span class="sxs-lookup"><span data-stu-id="0966d-150">Canceled</span></span>|<span data-ttu-id="0966d-151">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="0966d-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="0966d-152">擱置</span><span class="sxs-lookup"><span data-stu-id="0966d-152">Suspended</span></span>|<span data-ttu-id="0966d-153">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="0966d-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="0966d-154">已終止</span><span class="sxs-lookup"><span data-stu-id="0966d-154">Terminated</span></span>|<span data-ttu-id="0966d-155">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="0966d-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="0966d-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="0966d-156">Unsuspended</span></span>|<span data-ttu-id="0966d-157">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="0966d-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0966d-158">範例</span><span class="sxs-lookup"><span data-stu-id="0966d-158">Example</span></span>  
 <span data-ttu-id="0966d-159">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="0966d-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0966d-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0966d-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0966d-161">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="0966d-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0966d-162">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0966d-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
