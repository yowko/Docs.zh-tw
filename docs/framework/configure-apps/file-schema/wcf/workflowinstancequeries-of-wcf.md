---
title: <workflowInstanceQueries> WCF 的
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 89e122b87743a81a80ce63b382ae235c1c4863bc
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759245"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="5a370-102">\<workflowInstanceQueries > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="5a370-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="5a370-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="5a370-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="5a370-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5a370-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5a370-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5a370-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5a370-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="5a370-106">\<tracking></span></span>  
<span data-ttu-id="5a370-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="5a370-107">\<profiles></span></span>  
<span data-ttu-id="5a370-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5a370-108">\<trackingProfile></span></span>  
<span data-ttu-id="5a370-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5a370-109">\<workflow></span></span>  
<span data-ttu-id="5a370-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="5a370-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a370-111">語法</span><span class="sxs-lookup"><span data-stu-id="5a370-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a370-112">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="5a370-112">Attributes and elements</span></span>

<span data-ttu-id="5a370-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5a370-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a370-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5a370-114">Attributes</span></span>  

<span data-ttu-id="5a370-115">無。</span><span class="sxs-lookup"><span data-stu-id="5a370-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a370-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5a370-116">Child elements</span></span>  
  
|<span data-ttu-id="5a370-117">項目</span><span class="sxs-lookup"><span data-stu-id="5a370-117">Element</span></span>|<span data-ttu-id="5a370-118">描述</span><span class="sxs-lookup"><span data-stu-id="5a370-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a370-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="5a370-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="5a370-120">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="5a370-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a370-121">父元素</span><span class="sxs-lookup"><span data-stu-id="5a370-121">Parent elements</span></span>  
  
|<span data-ttu-id="5a370-122">元素</span><span class="sxs-lookup"><span data-stu-id="5a370-122">Element</span></span>|<span data-ttu-id="5a370-123">描述</span><span class="sxs-lookup"><span data-stu-id="5a370-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a370-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5a370-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5a370-125">包含所有的查詢所識別的特定工作流程的組態項目[activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)屬性。</span><span class="sxs-lookup"><span data-stu-id="5a370-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a370-126">備註</span><span class="sxs-lookup"><span data-stu-id="5a370-126">Remarks</span></span>

<span data-ttu-id="5a370-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="5a370-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="5a370-128">範例</span><span class="sxs-lookup"><span data-stu-id="5a370-128">Example</span></span>  

<span data-ttu-id="5a370-129">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="5a370-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="5a370-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a370-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5a370-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="5a370-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5a370-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5a370-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
