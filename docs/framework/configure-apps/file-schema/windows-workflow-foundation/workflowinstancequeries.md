---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 0a32e6ee22cdf984e64c1b8fa16836c4c56d0380
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932743"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="d3a31-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="d3a31-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="d3a31-102">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="d3a31-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="d3a31-103">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d3a31-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d3a31-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d3a31-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d3a31-105">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d3a31-105">\<tracking></span></span>  
<span data-ttu-id="d3a31-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d3a31-106">\<trackingProfile></span></span>  
<span data-ttu-id="d3a31-107">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d3a31-107">\<workflow></span></span>  
<span data-ttu-id="d3a31-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="d3a31-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a31-109">語法</span><span class="sxs-lookup"><span data-stu-id="d3a31-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3a31-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3a31-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3a31-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d3a31-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3a31-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d3a31-112">Attributes</span></span>  
 <span data-ttu-id="d3a31-113">無。</span><span class="sxs-lookup"><span data-stu-id="d3a31-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3a31-114">子元素</span><span class="sxs-lookup"><span data-stu-id="d3a31-114">Child Elements</span></span>  
  
|<span data-ttu-id="d3a31-115">項目</span><span class="sxs-lookup"><span data-stu-id="d3a31-115">Element</span></span>|<span data-ttu-id="d3a31-116">描述</span><span class="sxs-lookup"><span data-stu-id="d3a31-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3a31-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="d3a31-117">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="d3a31-118">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="d3a31-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3a31-119">父項目</span><span class="sxs-lookup"><span data-stu-id="d3a31-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d3a31-120">項目</span><span class="sxs-lookup"><span data-stu-id="d3a31-120">Element</span></span>|<span data-ttu-id="d3a31-121">說明</span><span class="sxs-lookup"><span data-stu-id="d3a31-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3a31-122">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d3a31-122">\<workflow></span></span>](workflow.md)|<span data-ttu-id="d3a31-123">Configuration 元素, 其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="d3a31-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3a31-124">備註</span><span class="sxs-lookup"><span data-stu-id="d3a31-124">Remarks</span></span>  
 <span data-ttu-id="d3a31-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="d3a31-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="d3a31-126">範例</span><span class="sxs-lookup"><span data-stu-id="d3a31-126">Example</span></span>  
 <span data-ttu-id="d3a31-127">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d3a31-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3a31-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3a31-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d3a31-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d3a31-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d3a31-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d3a31-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
