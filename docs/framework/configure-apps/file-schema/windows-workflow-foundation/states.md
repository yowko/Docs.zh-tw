---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: e759f86e7746eaf3fdd72ed923612b24ef9b0c23
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150813"
---
# \<states>

<span data-ttu-id="05a30-101">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="05a30-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="05a30-102">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="05a30-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="05a30-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="05a30-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05a30-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="05a30-104">Attributes and Elements</span></span>  

 <span data-ttu-id="05a30-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="05a30-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05a30-106">屬性</span><span class="sxs-lookup"><span data-stu-id="05a30-106">Attributes</span></span>  

 <span data-ttu-id="05a30-107">無。</span><span class="sxs-lookup"><span data-stu-id="05a30-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05a30-108">子元素</span><span class="sxs-lookup"><span data-stu-id="05a30-108">Child Elements</span></span>  
  
|<span data-ttu-id="05a30-109">項目</span><span class="sxs-lookup"><span data-stu-id="05a30-109">Element</span></span>|<span data-ttu-id="05a30-110">描述</span><span class="sxs-lookup"><span data-stu-id="05a30-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="05a30-111">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="05a30-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05a30-112">父項目</span><span class="sxs-lookup"><span data-stu-id="05a30-112">Parent Elements</span></span>  
  
|<span data-ttu-id="05a30-113">項目</span><span class="sxs-lookup"><span data-stu-id="05a30-113">Element</span></span>|<span data-ttu-id="05a30-114">描述</span><span class="sxs-lookup"><span data-stu-id="05a30-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="05a30-115">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="05a30-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05a30-116">備註</span><span class="sxs-lookup"><span data-stu-id="05a30-116">Remarks</span></span>  

 <span data-ttu-id="05a30-117">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="05a30-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="05a30-118">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="05a30-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="05a30-119">州</span><span class="sxs-lookup"><span data-stu-id="05a30-119">State</span></span>|<span data-ttu-id="05a30-120">描述</span><span class="sxs-lookup"><span data-stu-id="05a30-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05a30-121">已中止</span><span class="sxs-lookup"><span data-stu-id="05a30-121">Aborted</span></span>|<span data-ttu-id="05a30-122">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="05a30-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="05a30-123">已完成</span><span class="sxs-lookup"><span data-stu-id="05a30-123">Completed</span></span>|<span data-ttu-id="05a30-124">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="05a30-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="05a30-125">已刪除</span><span class="sxs-lookup"><span data-stu-id="05a30-125">Deleted</span></span>|<span data-ttu-id="05a30-126">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="05a30-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="05a30-127">閒置</span><span class="sxs-lookup"><span data-stu-id="05a30-127">Idle</span></span>|<span data-ttu-id="05a30-128">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="05a30-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="05a30-129">已保存</span><span class="sxs-lookup"><span data-stu-id="05a30-129">Persisted</span></span>|<span data-ttu-id="05a30-130">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="05a30-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="05a30-131">已繼續</span><span class="sxs-lookup"><span data-stu-id="05a30-131">Resumed</span></span>|<span data-ttu-id="05a30-132">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="05a30-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="05a30-133">已開始</span><span class="sxs-lookup"><span data-stu-id="05a30-133">Started</span></span>|<span data-ttu-id="05a30-134">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="05a30-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="05a30-135">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="05a30-135">UnhandledException</span></span>|<span data-ttu-id="05a30-136">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="05a30-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="05a30-137">已卸載</span><span class="sxs-lookup"><span data-stu-id="05a30-137">Unloaded</span></span>|<span data-ttu-id="05a30-138">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="05a30-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="05a30-139">已取消</span><span class="sxs-lookup"><span data-stu-id="05a30-139">Canceled</span></span>|<span data-ttu-id="05a30-140">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="05a30-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="05a30-141">暫止</span><span class="sxs-lookup"><span data-stu-id="05a30-141">Suspended</span></span>|<span data-ttu-id="05a30-142">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="05a30-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="05a30-143">已終止</span><span class="sxs-lookup"><span data-stu-id="05a30-143">Terminated</span></span>|<span data-ttu-id="05a30-144">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="05a30-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="05a30-145">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="05a30-145">Unsuspended</span></span>|<span data-ttu-id="05a30-146">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="05a30-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05a30-147">範例</span><span class="sxs-lookup"><span data-stu-id="05a30-147">Example</span></span>  

 <span data-ttu-id="05a30-148">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="05a30-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05a30-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05a30-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="05a30-150">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="05a30-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="05a30-151">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="05a30-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
