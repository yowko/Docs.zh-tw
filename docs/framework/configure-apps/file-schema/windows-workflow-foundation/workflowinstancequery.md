---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 7541ddcf4df8135d82b1f7f5ae2c02f031090e17
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275060"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="04afa-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="04afa-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="04afa-102">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="04afa-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="04afa-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="04afa-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="04afa-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04afa-104">\<system.serviceModel></span></span>  
<span data-ttu-id="04afa-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="04afa-105">\<tracking></span></span>  
<span data-ttu-id="04afa-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="04afa-106">\<trackingProfile></span></span>  
<span data-ttu-id="04afa-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="04afa-107">\<workflow></span></span>  
<span data-ttu-id="04afa-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="04afa-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="04afa-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="04afa-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04afa-110">語法</span><span class="sxs-lookup"><span data-stu-id="04afa-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04afa-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04afa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="04afa-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="04afa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04afa-113">屬性</span><span class="sxs-lookup"><span data-stu-id="04afa-113">Attributes</span></span>  
 <span data-ttu-id="04afa-114">無。</span><span class="sxs-lookup"><span data-stu-id="04afa-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04afa-115">子元素</span><span class="sxs-lookup"><span data-stu-id="04afa-115">Child Elements</span></span>  
  
|<span data-ttu-id="04afa-116">項目</span><span class="sxs-lookup"><span data-stu-id="04afa-116">Element</span></span>|<span data-ttu-id="04afa-117">描述</span><span class="sxs-lookup"><span data-stu-id="04afa-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04afa-118">\<states></span><span class="sxs-lookup"><span data-stu-id="04afa-118">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="04afa-119">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="04afa-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04afa-120">父項目</span><span class="sxs-lookup"><span data-stu-id="04afa-120">Parent Elements</span></span>  
  
|<span data-ttu-id="04afa-121">項目</span><span class="sxs-lookup"><span data-stu-id="04afa-121">Element</span></span>|<span data-ttu-id="04afa-122">描述</span><span class="sxs-lookup"><span data-stu-id="04afa-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04afa-123">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="04afa-123">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="04afa-124">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="04afa-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04afa-125">備註</span><span class="sxs-lookup"><span data-stu-id="04afa-125">Remarks</span></span>  
 <span data-ttu-id="04afa-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="04afa-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="04afa-127">範例</span><span class="sxs-lookup"><span data-stu-id="04afa-127">Example</span></span>  
 <span data-ttu-id="04afa-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="04afa-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04afa-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04afa-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="04afa-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="04afa-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="04afa-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="04afa-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
