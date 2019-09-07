---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398644"
---
# <a name="state"></a><span data-ttu-id="63013-101">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="63013-101">\<state></span></span>
<span data-ttu-id="63013-102">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="63013-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="63013-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="63013-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="63013-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="63013-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63013-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="63013-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="63013-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="63013-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="63013-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="63013-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="63013-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="63013-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="63013-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="63013-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="63013-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="63013-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="63013-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<狀態 >** ](states.md)</span><span class="sxs-lookup"><span data-stu-id="63013-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)</span></span>\
<span data-ttu-id="63013-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<狀態 >**</span><span class="sxs-lookup"><span data-stu-id="63013-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63013-113">語法</span><span class="sxs-lookup"><span data-stu-id="63013-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63013-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="63013-114">Attributes and Elements</span></span>  
 <span data-ttu-id="63013-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="63013-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63013-116">屬性</span><span class="sxs-lookup"><span data-stu-id="63013-116">Attributes</span></span>  
  
|<span data-ttu-id="63013-117">屬性</span><span class="sxs-lookup"><span data-stu-id="63013-117">Attribute</span></span>|<span data-ttu-id="63013-118">說明</span><span class="sxs-lookup"><span data-stu-id="63013-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63013-119">NAME</span><span class="sxs-lookup"><span data-stu-id="63013-119">name</span></span>|<span data-ttu-id="63013-120">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="63013-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63013-121">子元素</span><span class="sxs-lookup"><span data-stu-id="63013-121">Child Elements</span></span>  
 <span data-ttu-id="63013-122">無。</span><span class="sxs-lookup"><span data-stu-id="63013-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63013-123">父項目</span><span class="sxs-lookup"><span data-stu-id="63013-123">Parent Elements</span></span>  
  
|<span data-ttu-id="63013-124">項目</span><span class="sxs-lookup"><span data-stu-id="63013-124">Element</span></span>|<span data-ttu-id="63013-125">說明</span><span class="sxs-lookup"><span data-stu-id="63013-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63013-126">\<states></span><span class="sxs-lookup"><span data-stu-id="63013-126">\<states></span></span>](states.md)|<span data-ttu-id="63013-127">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="63013-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63013-128">備註</span><span class="sxs-lookup"><span data-stu-id="63013-128">Remarks</span></span>  
 <span data-ttu-id="63013-129">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="63013-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="63013-130">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="63013-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="63013-131">State</span><span class="sxs-lookup"><span data-stu-id="63013-131">State</span></span>|<span data-ttu-id="63013-132">描述</span><span class="sxs-lookup"><span data-stu-id="63013-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63013-133">已中止</span><span class="sxs-lookup"><span data-stu-id="63013-133">Aborted</span></span>|<span data-ttu-id="63013-134">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="63013-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="63013-135">已完成</span><span class="sxs-lookup"><span data-stu-id="63013-135">Completed</span></span>|<span data-ttu-id="63013-136">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="63013-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="63013-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="63013-137">Deleted</span></span>|<span data-ttu-id="63013-138">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="63013-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="63013-139">閒置</span><span class="sxs-lookup"><span data-stu-id="63013-139">Idle</span></span>|<span data-ttu-id="63013-140">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="63013-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="63013-141">已保存</span><span class="sxs-lookup"><span data-stu-id="63013-141">Persisted</span></span>|<span data-ttu-id="63013-142">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="63013-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="63013-143">已繼續</span><span class="sxs-lookup"><span data-stu-id="63013-143">Resumed</span></span>|<span data-ttu-id="63013-144">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="63013-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="63013-145">自</span><span class="sxs-lookup"><span data-stu-id="63013-145">Started</span></span>|<span data-ttu-id="63013-146">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="63013-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="63013-147">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="63013-147">UnhandledException</span></span>|<span data-ttu-id="63013-148">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63013-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="63013-149">已卸載</span><span class="sxs-lookup"><span data-stu-id="63013-149">Unloaded</span></span>|<span data-ttu-id="63013-150">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="63013-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="63013-151">已取消</span><span class="sxs-lookup"><span data-stu-id="63013-151">Canceled</span></span>|<span data-ttu-id="63013-152">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="63013-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="63013-153">擱置</span><span class="sxs-lookup"><span data-stu-id="63013-153">Suspended</span></span>|<span data-ttu-id="63013-154">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="63013-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="63013-155">已終止</span><span class="sxs-lookup"><span data-stu-id="63013-155">Terminated</span></span>|<span data-ttu-id="63013-156">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="63013-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="63013-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="63013-157">Unsuspended</span></span>|<span data-ttu-id="63013-158">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="63013-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63013-159">範例</span><span class="sxs-lookup"><span data-stu-id="63013-159">Example</span></span>  
 <span data-ttu-id="63013-160">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="63013-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63013-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63013-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="63013-162">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="63013-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63013-163">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="63013-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
