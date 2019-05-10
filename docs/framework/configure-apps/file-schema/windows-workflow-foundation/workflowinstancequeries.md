---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: fc92b030e8f6643a856446142842c492db703253
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624803"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="bd6ad-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="bd6ad-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="bd6ad-102">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="bd6ad-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="bd6ad-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bd6ad-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bd6ad-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bd6ad-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bd6ad-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="bd6ad-105">\<tracking></span></span>  
<span data-ttu-id="bd6ad-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bd6ad-106">\<trackingProfile></span></span>  
<span data-ttu-id="bd6ad-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="bd6ad-107">\<workflow></span></span>  
<span data-ttu-id="bd6ad-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="bd6ad-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd6ad-109">語法</span><span class="sxs-lookup"><span data-stu-id="bd6ad-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd6ad-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd6ad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd6ad-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bd6ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd6ad-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bd6ad-112">Attributes</span></span>  
 <span data-ttu-id="bd6ad-113">無。</span><span class="sxs-lookup"><span data-stu-id="bd6ad-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd6ad-114">子元素</span><span class="sxs-lookup"><span data-stu-id="bd6ad-114">Child Elements</span></span>  
  
|<span data-ttu-id="bd6ad-115">項目</span><span class="sxs-lookup"><span data-stu-id="bd6ad-115">Element</span></span>|<span data-ttu-id="bd6ad-116">描述</span><span class="sxs-lookup"><span data-stu-id="bd6ad-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd6ad-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="bd6ad-117">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="bd6ad-118">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="bd6ad-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd6ad-119">父項目</span><span class="sxs-lookup"><span data-stu-id="bd6ad-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bd6ad-120">項目</span><span class="sxs-lookup"><span data-stu-id="bd6ad-120">Element</span></span>|<span data-ttu-id="bd6ad-121">描述</span><span class="sxs-lookup"><span data-stu-id="bd6ad-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd6ad-122">\<workflow></span><span class="sxs-lookup"><span data-stu-id="bd6ad-122">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="bd6ad-123">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="bd6ad-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd6ad-124">備註</span><span class="sxs-lookup"><span data-stu-id="bd6ad-124">Remarks</span></span>  
 <span data-ttu-id="bd6ad-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="bd6ad-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="bd6ad-126">範例</span><span class="sxs-lookup"><span data-stu-id="bd6ad-126">Example</span></span>  
 <span data-ttu-id="bd6ad-127">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="bd6ad-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd6ad-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd6ad-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bd6ad-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="bd6ad-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bd6ad-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="bd6ad-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
