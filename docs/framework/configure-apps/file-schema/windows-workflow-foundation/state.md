---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398644"
---
# \<state>
<span data-ttu-id="d8ff7-101">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="d8ff7-102">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8ff7-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="d8ff7-103">語法</span><span class="sxs-lookup"><span data-stu-id="d8ff7-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8ff7-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8ff7-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d8ff7-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8ff7-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d8ff7-106">Attributes</span></span>  
  
|<span data-ttu-id="d8ff7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d8ff7-107">Attribute</span></span>|<span data-ttu-id="d8ff7-108">描述</span><span class="sxs-lookup"><span data-stu-id="d8ff7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8ff7-109">NAME</span><span class="sxs-lookup"><span data-stu-id="d8ff7-109">name</span></span>|<span data-ttu-id="d8ff7-110">字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8ff7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d8ff7-111">Child Elements</span></span>  
 <span data-ttu-id="d8ff7-112">無。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8ff7-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d8ff7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d8ff7-114">元素</span><span class="sxs-lookup"><span data-stu-id="d8ff7-114">Element</span></span>|<span data-ttu-id="d8ff7-115">描述</span><span class="sxs-lookup"><span data-stu-id="d8ff7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="d8ff7-116">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ff7-117">備註</span><span class="sxs-lookup"><span data-stu-id="d8ff7-117">Remarks</span></span>  
 <span data-ttu-id="d8ff7-118">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="d8ff7-119">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="d8ff7-120">州</span><span class="sxs-lookup"><span data-stu-id="d8ff7-120">State</span></span>|<span data-ttu-id="d8ff7-121">描述</span><span class="sxs-lookup"><span data-stu-id="d8ff7-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8ff7-122">已中止</span><span class="sxs-lookup"><span data-stu-id="d8ff7-122">Aborted</span></span>|<span data-ttu-id="d8ff7-123">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d8ff7-124">已完成</span><span class="sxs-lookup"><span data-stu-id="d8ff7-124">Completed</span></span>|<span data-ttu-id="d8ff7-125">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="d8ff7-126">已刪除</span><span class="sxs-lookup"><span data-stu-id="d8ff7-126">Deleted</span></span>|<span data-ttu-id="d8ff7-127">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="d8ff7-128">閒置</span><span class="sxs-lookup"><span data-stu-id="d8ff7-128">Idle</span></span>|<span data-ttu-id="d8ff7-129">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="d8ff7-130">已保存</span><span class="sxs-lookup"><span data-stu-id="d8ff7-130">Persisted</span></span>|<span data-ttu-id="d8ff7-131">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="d8ff7-132">已繼續</span><span class="sxs-lookup"><span data-stu-id="d8ff7-132">Resumed</span></span>|<span data-ttu-id="d8ff7-133">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="d8ff7-134">已開始</span><span class="sxs-lookup"><span data-stu-id="d8ff7-134">Started</span></span>|<span data-ttu-id="d8ff7-135">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="d8ff7-136">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="d8ff7-136">UnhandledException</span></span>|<span data-ttu-id="d8ff7-137">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="d8ff7-138">已卸載</span><span class="sxs-lookup"><span data-stu-id="d8ff7-138">Unloaded</span></span>|<span data-ttu-id="d8ff7-139">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="d8ff7-140">已取消</span><span class="sxs-lookup"><span data-stu-id="d8ff7-140">Canceled</span></span>|<span data-ttu-id="d8ff7-141">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="d8ff7-142">暫止</span><span class="sxs-lookup"><span data-stu-id="d8ff7-142">Suspended</span></span>|<span data-ttu-id="d8ff7-143">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="d8ff7-144">已終止</span><span class="sxs-lookup"><span data-stu-id="d8ff7-144">Terminated</span></span>|<span data-ttu-id="d8ff7-145">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="d8ff7-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="d8ff7-146">Unsuspended</span></span>|<span data-ttu-id="d8ff7-147">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8ff7-148">範例</span><span class="sxs-lookup"><span data-stu-id="d8ff7-148">Example</span></span>  
 <span data-ttu-id="d8ff7-149">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d8ff7-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8ff7-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ff7-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d8ff7-151">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d8ff7-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d8ff7-152">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d8ff7-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
