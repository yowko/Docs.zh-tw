---
title: '&lt;workflowInstanceQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 8ee8c74e88f1605ae3858db787c38976de9cc976
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693700"
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="c51f1-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c51f1-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="c51f1-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="c51f1-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="c51f1-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c51f1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c51f1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c51f1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c51f1-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c51f1-106">\<tracking></span></span>  
<span data-ttu-id="c51f1-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c51f1-107">\<trackingProfile></span></span>  
<span data-ttu-id="c51f1-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c51f1-108">\<workflow></span></span>  
<span data-ttu-id="c51f1-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="c51f1-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51f1-110">語法</span><span class="sxs-lookup"><span data-stu-id="c51f1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c51f1-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c51f1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c51f1-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c51f1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c51f1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c51f1-113">Attributes</span></span>  
 <span data-ttu-id="c51f1-114">無。</span><span class="sxs-lookup"><span data-stu-id="c51f1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c51f1-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c51f1-115">Child Elements</span></span>  
  
|<span data-ttu-id="c51f1-116">項目</span><span class="sxs-lookup"><span data-stu-id="c51f1-116">Element</span></span>|<span data-ttu-id="c51f1-117">描述</span><span class="sxs-lookup"><span data-stu-id="c51f1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c51f1-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="c51f1-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="c51f1-119">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="c51f1-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c51f1-120">父項目</span><span class="sxs-lookup"><span data-stu-id="c51f1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c51f1-121">項目</span><span class="sxs-lookup"><span data-stu-id="c51f1-121">Element</span></span>|<span data-ttu-id="c51f1-122">描述</span><span class="sxs-lookup"><span data-stu-id="c51f1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c51f1-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c51f1-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c51f1-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="c51f1-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c51f1-125">備註</span><span class="sxs-lookup"><span data-stu-id="c51f1-125">Remarks</span></span>  
 <span data-ttu-id="c51f1-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="c51f1-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="c51f1-127">範例</span><span class="sxs-lookup"><span data-stu-id="c51f1-127">Example</span></span>  
 <span data-ttu-id="c51f1-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="c51f1-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c51f1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c51f1-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c51f1-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c51f1-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c51f1-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c51f1-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
