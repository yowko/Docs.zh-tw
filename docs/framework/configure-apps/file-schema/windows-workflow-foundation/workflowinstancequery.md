---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: f0a3c3a27b40000432b40b7008f81251fe771ca2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913134"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="090c3-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="090c3-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="090c3-102">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="090c3-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="090c3-103">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="090c3-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="090c3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="090c3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="090c3-105">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="090c3-105">\<tracking></span></span>  
<span data-ttu-id="090c3-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="090c3-106">\<trackingProfile></span></span>  
<span data-ttu-id="090c3-107">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="090c3-107">\<workflow></span></span>  
<span data-ttu-id="090c3-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="090c3-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="090c3-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="090c3-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090c3-110">語法</span><span class="sxs-lookup"><span data-stu-id="090c3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="090c3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="090c3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="090c3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="090c3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="090c3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="090c3-113">Attributes</span></span>  
 <span data-ttu-id="090c3-114">無。</span><span class="sxs-lookup"><span data-stu-id="090c3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="090c3-115">子元素</span><span class="sxs-lookup"><span data-stu-id="090c3-115">Child Elements</span></span>  
  
|<span data-ttu-id="090c3-116">項目</span><span class="sxs-lookup"><span data-stu-id="090c3-116">Element</span></span>|<span data-ttu-id="090c3-117">描述</span><span class="sxs-lookup"><span data-stu-id="090c3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="090c3-118">\<states></span><span class="sxs-lookup"><span data-stu-id="090c3-118">\<states></span></span>](states.md)|<span data-ttu-id="090c3-119">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="090c3-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="090c3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="090c3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="090c3-121">項目</span><span class="sxs-lookup"><span data-stu-id="090c3-121">Element</span></span>|<span data-ttu-id="090c3-122">描述</span><span class="sxs-lookup"><span data-stu-id="090c3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="090c3-123">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="090c3-123">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="090c3-124">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="090c3-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="090c3-125">備註</span><span class="sxs-lookup"><span data-stu-id="090c3-125">Remarks</span></span>  
 <span data-ttu-id="090c3-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="090c3-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="090c3-127">範例</span><span class="sxs-lookup"><span data-stu-id="090c3-127">Example</span></span>  
 <span data-ttu-id="090c3-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="090c3-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="090c3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="090c3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="090c3-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="090c3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="090c3-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="090c3-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
