---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 169fa900b5be9a9577818b68b540184afd4a6681
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169722"
---
# \<state>

<span data-ttu-id="94b89-101">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="94b89-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="94b89-102">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="94b89-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="94b89-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="94b89-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94b89-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="94b89-104">Attributes and Elements</span></span>  

 <span data-ttu-id="94b89-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94b89-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94b89-106">屬性</span><span class="sxs-lookup"><span data-stu-id="94b89-106">Attributes</span></span>  
  
|<span data-ttu-id="94b89-107">屬性</span><span class="sxs-lookup"><span data-stu-id="94b89-107">Attribute</span></span>|<span data-ttu-id="94b89-108">描述</span><span class="sxs-lookup"><span data-stu-id="94b89-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94b89-109">NAME</span><span class="sxs-lookup"><span data-stu-id="94b89-109">name</span></span>|<span data-ttu-id="94b89-110">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="94b89-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94b89-111">子元素</span><span class="sxs-lookup"><span data-stu-id="94b89-111">Child Elements</span></span>  

 <span data-ttu-id="94b89-112">無。</span><span class="sxs-lookup"><span data-stu-id="94b89-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94b89-113">父項目</span><span class="sxs-lookup"><span data-stu-id="94b89-113">Parent Elements</span></span>  
  
|<span data-ttu-id="94b89-114">項目</span><span class="sxs-lookup"><span data-stu-id="94b89-114">Element</span></span>|<span data-ttu-id="94b89-115">描述</span><span class="sxs-lookup"><span data-stu-id="94b89-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="94b89-116">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="94b89-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94b89-117">備註</span><span class="sxs-lookup"><span data-stu-id="94b89-117">Remarks</span></span>  

 <span data-ttu-id="94b89-118">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="94b89-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="94b89-119">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="94b89-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="94b89-120">州</span><span class="sxs-lookup"><span data-stu-id="94b89-120">State</span></span>|<span data-ttu-id="94b89-121">描述</span><span class="sxs-lookup"><span data-stu-id="94b89-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94b89-122">已中止</span><span class="sxs-lookup"><span data-stu-id="94b89-122">Aborted</span></span>|<span data-ttu-id="94b89-123">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="94b89-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="94b89-124">已完成</span><span class="sxs-lookup"><span data-stu-id="94b89-124">Completed</span></span>|<span data-ttu-id="94b89-125">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="94b89-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="94b89-126">已刪除</span><span class="sxs-lookup"><span data-stu-id="94b89-126">Deleted</span></span>|<span data-ttu-id="94b89-127">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="94b89-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="94b89-128">閒置</span><span class="sxs-lookup"><span data-stu-id="94b89-128">Idle</span></span>|<span data-ttu-id="94b89-129">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="94b89-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="94b89-130">已保存</span><span class="sxs-lookup"><span data-stu-id="94b89-130">Persisted</span></span>|<span data-ttu-id="94b89-131">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="94b89-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="94b89-132">已繼續</span><span class="sxs-lookup"><span data-stu-id="94b89-132">Resumed</span></span>|<span data-ttu-id="94b89-133">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="94b89-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="94b89-134">已開始</span><span class="sxs-lookup"><span data-stu-id="94b89-134">Started</span></span>|<span data-ttu-id="94b89-135">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="94b89-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="94b89-136">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="94b89-136">UnhandledException</span></span>|<span data-ttu-id="94b89-137">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="94b89-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="94b89-138">已卸載</span><span class="sxs-lookup"><span data-stu-id="94b89-138">Unloaded</span></span>|<span data-ttu-id="94b89-139">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="94b89-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="94b89-140">已取消</span><span class="sxs-lookup"><span data-stu-id="94b89-140">Canceled</span></span>|<span data-ttu-id="94b89-141">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="94b89-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="94b89-142">暫止</span><span class="sxs-lookup"><span data-stu-id="94b89-142">Suspended</span></span>|<span data-ttu-id="94b89-143">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="94b89-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="94b89-144">已終止</span><span class="sxs-lookup"><span data-stu-id="94b89-144">Terminated</span></span>|<span data-ttu-id="94b89-145">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="94b89-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="94b89-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="94b89-146">Unsuspended</span></span>|<span data-ttu-id="94b89-147">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="94b89-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="94b89-148">範例</span><span class="sxs-lookup"><span data-stu-id="94b89-148">Example</span></span>  

 <span data-ttu-id="94b89-149">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="94b89-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94b89-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94b89-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="94b89-151">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="94b89-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="94b89-152">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="94b89-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
