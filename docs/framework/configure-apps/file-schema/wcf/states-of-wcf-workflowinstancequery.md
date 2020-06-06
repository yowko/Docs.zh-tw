---
title: <states>在 WCF 中，<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855035"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="63cd9-102">\<states>在 WCF 中，\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="63cd9-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="63cd9-103">表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="63cd9-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="63cd9-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="63cd9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="63cd9-105">語法</span><span class="sxs-lookup"><span data-stu-id="63cd9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63cd9-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="63cd9-106">Attributes and elements</span></span>

<span data-ttu-id="63cd9-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="63cd9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63cd9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="63cd9-108">Attributes</span></span>  

<span data-ttu-id="63cd9-109">無。</span><span class="sxs-lookup"><span data-stu-id="63cd9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63cd9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="63cd9-110">Child elements</span></span>
  
|<span data-ttu-id="63cd9-111">元素</span><span class="sxs-lookup"><span data-stu-id="63cd9-111">Element</span></span>|<span data-ttu-id="63cd9-112">描述</span><span class="sxs-lookup"><span data-stu-id="63cd9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="63cd9-113">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="63cd9-113">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63cd9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="63cd9-114">Parent elements</span></span>  
  
|<span data-ttu-id="63cd9-115">元素</span><span class="sxs-lookup"><span data-stu-id="63cd9-115">Element</span></span>|<span data-ttu-id="63cd9-116">描述</span><span class="sxs-lookup"><span data-stu-id="63cd9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="63cd9-117">追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="63cd9-117">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63cd9-118">備註</span><span class="sxs-lookup"><span data-stu-id="63cd9-118">Remarks</span></span>

<span data-ttu-id="63cd9-119">按照此集合中的狀態篩選傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="63cd9-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="63cd9-120">下表說明可能的狀態值。</span><span class="sxs-lookup"><span data-stu-id="63cd9-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="63cd9-121">州</span><span class="sxs-lookup"><span data-stu-id="63cd9-121">State</span></span>|<span data-ttu-id="63cd9-122">描述</span><span class="sxs-lookup"><span data-stu-id="63cd9-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63cd9-123">已中止</span><span class="sxs-lookup"><span data-stu-id="63cd9-123">Aborted</span></span>|<span data-ttu-id="63cd9-124">工作流程執行個體已中止。</span><span class="sxs-lookup"><span data-stu-id="63cd9-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="63cd9-125">已完成</span><span class="sxs-lookup"><span data-stu-id="63cd9-125">Completed</span></span>|<span data-ttu-id="63cd9-126">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="63cd9-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="63cd9-127">已刪除</span><span class="sxs-lookup"><span data-stu-id="63cd9-127">Deleted</span></span>|<span data-ttu-id="63cd9-128">工作流程執行個體已刪除。</span><span class="sxs-lookup"><span data-stu-id="63cd9-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="63cd9-129">閒置</span><span class="sxs-lookup"><span data-stu-id="63cd9-129">Idle</span></span>|<span data-ttu-id="63cd9-130">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="63cd9-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="63cd9-131">已保存</span><span class="sxs-lookup"><span data-stu-id="63cd9-131">Persisted</span></span>|<span data-ttu-id="63cd9-132">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="63cd9-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="63cd9-133">已繼續</span><span class="sxs-lookup"><span data-stu-id="63cd9-133">Resumed</span></span>|<span data-ttu-id="63cd9-134">工作流程執行個體已繼續。</span><span class="sxs-lookup"><span data-stu-id="63cd9-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="63cd9-135">已開始</span><span class="sxs-lookup"><span data-stu-id="63cd9-135">Started</span></span>|<span data-ttu-id="63cd9-136">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="63cd9-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="63cd9-137">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="63cd9-137">UnhandledException</span></span>|<span data-ttu-id="63cd9-138">工作流程執行個體發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63cd9-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="63cd9-139">已卸載</span><span class="sxs-lookup"><span data-stu-id="63cd9-139">Unloaded</span></span>|<span data-ttu-id="63cd9-140">工作流程執行個體已卸載。</span><span class="sxs-lookup"><span data-stu-id="63cd9-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="63cd9-141">已取消</span><span class="sxs-lookup"><span data-stu-id="63cd9-141">Canceled</span></span>|<span data-ttu-id="63cd9-142">工作流程執行個體已取消。</span><span class="sxs-lookup"><span data-stu-id="63cd9-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="63cd9-143">暫止</span><span class="sxs-lookup"><span data-stu-id="63cd9-143">Suspended</span></span>|<span data-ttu-id="63cd9-144">工作流程執行個體已暫停。</span><span class="sxs-lookup"><span data-stu-id="63cd9-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="63cd9-145">已終止</span><span class="sxs-lookup"><span data-stu-id="63cd9-145">Terminated</span></span>|<span data-ttu-id="63cd9-146">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="63cd9-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="63cd9-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="63cd9-147">Unsuspended</span></span>|<span data-ttu-id="63cd9-148">工作流程執行個體已取消暫停。</span><span class="sxs-lookup"><span data-stu-id="63cd9-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63cd9-149">範例</span><span class="sxs-lookup"><span data-stu-id="63cd9-149">Example</span></span>

<span data-ttu-id="63cd9-150">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="63cd9-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="63cd9-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63cd9-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="63cd9-152">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="63cd9-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63cd9-153">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="63cd9-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
