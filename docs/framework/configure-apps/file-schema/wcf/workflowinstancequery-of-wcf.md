---
title: <workflowInstanceQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 7e15d7654aeafa5fa7b87922283d6520d5493242
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915229"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="ceea0-102">\<WCF 的 workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="ceea0-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="ceea0-103">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="ceea0-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="ceea0-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ceea0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ceea0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ceea0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ceea0-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="ceea0-106">\<tracking></span></span>  
<span data-ttu-id="ceea0-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="ceea0-107">\<profiles></span></span>  
<span data-ttu-id="ceea0-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ceea0-108">\<trackingProfile></span></span>  
<span data-ttu-id="ceea0-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ceea0-109">\<workflow></span></span>  
<span data-ttu-id="ceea0-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="ceea0-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="ceea0-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="ceea0-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceea0-112">語法</span><span class="sxs-lookup"><span data-stu-id="ceea0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceea0-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="ceea0-113">Attributes and elements</span></span>  

<span data-ttu-id="ceea0-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ceea0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceea0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ceea0-115">Attributes</span></span>  

<span data-ttu-id="ceea0-116">無。</span><span class="sxs-lookup"><span data-stu-id="ceea0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ceea0-117">子元素</span><span class="sxs-lookup"><span data-stu-id="ceea0-117">Child elements</span></span>  
  
|<span data-ttu-id="ceea0-118">項目</span><span class="sxs-lookup"><span data-stu-id="ceea0-118">Element</span></span>|<span data-ttu-id="ceea0-119">描述</span><span class="sxs-lookup"><span data-stu-id="ceea0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceea0-120">\<states></span><span class="sxs-lookup"><span data-stu-id="ceea0-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="ceea0-121">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="ceea0-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceea0-122">父元素</span><span class="sxs-lookup"><span data-stu-id="ceea0-122">Parent elements</span></span>  
  
|<span data-ttu-id="ceea0-123">元素</span><span class="sxs-lookup"><span data-stu-id="ceea0-123">Element</span></span>|<span data-ttu-id="ceea0-124">描述</span><span class="sxs-lookup"><span data-stu-id="ceea0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceea0-125">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="ceea0-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="ceea0-126">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="ceea0-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceea0-127">備註</span><span class="sxs-lookup"><span data-stu-id="ceea0-127">Remarks</span></span>  

<span data-ttu-id="ceea0-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="ceea0-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="ceea0-129">範例</span><span class="sxs-lookup"><span data-stu-id="ceea0-129">Example</span></span>  

<span data-ttu-id="ceea0-130">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ceea0-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="ceea0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ceea0-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ceea0-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ceea0-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ceea0-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ceea0-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
