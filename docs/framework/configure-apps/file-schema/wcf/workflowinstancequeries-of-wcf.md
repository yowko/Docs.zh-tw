---
title: WCF 的 &lt;workflowInstanceQueries&gt;
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 300637031c64f7c9e072f04835fc3590348ddc9e
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047393"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="e0558-102">WCF 的 &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e0558-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>

<span data-ttu-id="e0558-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="e0558-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="e0558-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e0558-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e0558-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e0558-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e0558-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="e0558-106">\<tracking></span></span>  
<span data-ttu-id="e0558-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="e0558-107">\<profiles></span></span>  
<span data-ttu-id="e0558-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e0558-108">\<trackingProfile></span></span>  
<span data-ttu-id="e0558-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="e0558-109">\<workflow></span></span>  
<span data-ttu-id="e0558-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="e0558-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0558-111">語法</span><span class="sxs-lookup"><span data-stu-id="e0558-111">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0558-112">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e0558-112">Attributes and elements</span></span>

<span data-ttu-id="e0558-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e0558-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0558-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e0558-114">Attributes</span></span>  

<span data-ttu-id="e0558-115">無。</span><span class="sxs-lookup"><span data-stu-id="e0558-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0558-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e0558-116">Child elements</span></span>  
  
|<span data-ttu-id="e0558-117">項目</span><span class="sxs-lookup"><span data-stu-id="e0558-117">Element</span></span>|<span data-ttu-id="e0558-118">描述</span><span class="sxs-lookup"><span data-stu-id="e0558-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0558-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="e0558-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="e0558-120">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="e0558-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0558-121">父元素</span><span class="sxs-lookup"><span data-stu-id="e0558-121">Parent elements</span></span>  
  
|<span data-ttu-id="e0558-122">元素</span><span class="sxs-lookup"><span data-stu-id="e0558-122">Element</span></span>|<span data-ttu-id="e0558-123">描述</span><span class="sxs-lookup"><span data-stu-id="e0558-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0558-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="e0558-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e0558-125">包含所有的查詢所識別的特定工作流程的組態項目[activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx)屬性。</span><span class="sxs-lookup"><span data-stu-id="e0558-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0558-126">備註</span><span class="sxs-lookup"><span data-stu-id="e0558-126">Remarks</span></span>

<span data-ttu-id="e0558-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="e0558-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="e0558-128">範例</span><span class="sxs-lookup"><span data-stu-id="e0558-128">Example</span></span>  

<span data-ttu-id="e0558-129">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e0558-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>  
    <states>  
      <state name="Started"/>  
    </states>  
  </workflowInstanceQuery>  
</workflowInstanceQueries>
```
  
## <a name="see-also"></a><span data-ttu-id="e0558-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0558-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e0558-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e0558-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e0558-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e0558-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
