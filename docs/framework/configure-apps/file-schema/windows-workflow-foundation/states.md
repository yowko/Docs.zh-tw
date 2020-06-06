---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398611"
---
# \<states>
<span data-ttu-id="136e5-101">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="136e5-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="136e5-102">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="136e5-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="136e5-103">語法</span><span class="sxs-lookup"><span data-stu-id="136e5-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="136e5-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="136e5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="136e5-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="136e5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="136e5-106">屬性</span><span class="sxs-lookup"><span data-stu-id="136e5-106">Attributes</span></span>  
 <span data-ttu-id="136e5-107">無。</span><span class="sxs-lookup"><span data-stu-id="136e5-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="136e5-108">子元素</span><span class="sxs-lookup"><span data-stu-id="136e5-108">Child Elements</span></span>  
  
|<span data-ttu-id="136e5-109">元素</span><span class="sxs-lookup"><span data-stu-id="136e5-109">Element</span></span>|<span data-ttu-id="136e5-110">描述</span><span class="sxs-lookup"><span data-stu-id="136e5-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="136e5-111">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="136e5-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="136e5-112">父項目</span><span class="sxs-lookup"><span data-stu-id="136e5-112">Parent Elements</span></span>  
  
|<span data-ttu-id="136e5-113">元素</span><span class="sxs-lookup"><span data-stu-id="136e5-113">Element</span></span>|<span data-ttu-id="136e5-114">描述</span><span class="sxs-lookup"><span data-stu-id="136e5-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="136e5-115">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="136e5-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="136e5-116">備註</span><span class="sxs-lookup"><span data-stu-id="136e5-116">Remarks</span></span>  
 <span data-ttu-id="136e5-117">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="136e5-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="136e5-118">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="136e5-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="136e5-119">州</span><span class="sxs-lookup"><span data-stu-id="136e5-119">State</span></span>|<span data-ttu-id="136e5-120">描述</span><span class="sxs-lookup"><span data-stu-id="136e5-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="136e5-121">已中止</span><span class="sxs-lookup"><span data-stu-id="136e5-121">Aborted</span></span>|<span data-ttu-id="136e5-122">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="136e5-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="136e5-123">已完成</span><span class="sxs-lookup"><span data-stu-id="136e5-123">Completed</span></span>|<span data-ttu-id="136e5-124">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="136e5-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="136e5-125">已刪除</span><span class="sxs-lookup"><span data-stu-id="136e5-125">Deleted</span></span>|<span data-ttu-id="136e5-126">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="136e5-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="136e5-127">閒置</span><span class="sxs-lookup"><span data-stu-id="136e5-127">Idle</span></span>|<span data-ttu-id="136e5-128">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="136e5-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="136e5-129">已保存</span><span class="sxs-lookup"><span data-stu-id="136e5-129">Persisted</span></span>|<span data-ttu-id="136e5-130">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="136e5-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="136e5-131">已繼續</span><span class="sxs-lookup"><span data-stu-id="136e5-131">Resumed</span></span>|<span data-ttu-id="136e5-132">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="136e5-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="136e5-133">已開始</span><span class="sxs-lookup"><span data-stu-id="136e5-133">Started</span></span>|<span data-ttu-id="136e5-134">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="136e5-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="136e5-135">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="136e5-135">UnhandledException</span></span>|<span data-ttu-id="136e5-136">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="136e5-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="136e5-137">已卸載</span><span class="sxs-lookup"><span data-stu-id="136e5-137">Unloaded</span></span>|<span data-ttu-id="136e5-138">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="136e5-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="136e5-139">已取消</span><span class="sxs-lookup"><span data-stu-id="136e5-139">Canceled</span></span>|<span data-ttu-id="136e5-140">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="136e5-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="136e5-141">暫止</span><span class="sxs-lookup"><span data-stu-id="136e5-141">Suspended</span></span>|<span data-ttu-id="136e5-142">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="136e5-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="136e5-143">已終止</span><span class="sxs-lookup"><span data-stu-id="136e5-143">Terminated</span></span>|<span data-ttu-id="136e5-144">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="136e5-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="136e5-145">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="136e5-145">Unsuspended</span></span>|<span data-ttu-id="136e5-146">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="136e5-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="136e5-147">範例</span><span class="sxs-lookup"><span data-stu-id="136e5-147">Example</span></span>  
 <span data-ttu-id="136e5-148">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="136e5-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="136e5-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="136e5-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="136e5-150">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="136e5-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="136e5-151">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="136e5-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
