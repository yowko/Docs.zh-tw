---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397506"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="21867-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="21867-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="21867-102">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="21867-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="21867-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="21867-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="21867-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="21867-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="21867-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="21867-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="21867-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="21867-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="21867-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="21867-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="21867-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="21867-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="21867-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="21867-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="21867-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="21867-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21867-111">語法</span><span class="sxs-lookup"><span data-stu-id="21867-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21867-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="21867-112">Attributes and Elements</span></span>  
 <span data-ttu-id="21867-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="21867-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21867-114">屬性</span><span class="sxs-lookup"><span data-stu-id="21867-114">Attributes</span></span>  
 <span data-ttu-id="21867-115">無。</span><span class="sxs-lookup"><span data-stu-id="21867-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21867-116">子元素</span><span class="sxs-lookup"><span data-stu-id="21867-116">Child Elements</span></span>  
  
|<span data-ttu-id="21867-117">項目</span><span class="sxs-lookup"><span data-stu-id="21867-117">Element</span></span>|<span data-ttu-id="21867-118">描述</span><span class="sxs-lookup"><span data-stu-id="21867-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21867-119">\<states></span><span class="sxs-lookup"><span data-stu-id="21867-119">\<states></span></span>](states.md)|<span data-ttu-id="21867-120">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="21867-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21867-121">父項目</span><span class="sxs-lookup"><span data-stu-id="21867-121">Parent Elements</span></span>  
  
|<span data-ttu-id="21867-122">項目</span><span class="sxs-lookup"><span data-stu-id="21867-122">Element</span></span>|<span data-ttu-id="21867-123">描述</span><span class="sxs-lookup"><span data-stu-id="21867-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21867-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="21867-124">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="21867-125">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="21867-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21867-126">備註</span><span class="sxs-lookup"><span data-stu-id="21867-126">Remarks</span></span>  
 <span data-ttu-id="21867-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="21867-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="21867-128">範例</span><span class="sxs-lookup"><span data-stu-id="21867-128">Example</span></span>  
 <span data-ttu-id="21867-129">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="21867-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21867-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21867-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="21867-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="21867-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="21867-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="21867-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
