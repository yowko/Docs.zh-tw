---
title: <workflowInstanceQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854767"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="5d0c9-102">\<WCF 的 workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="5d0c9-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="5d0c9-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="5d0c9-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="5d0c9-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5d0c9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5d0c9-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d0c9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d0c9-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5d0c9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5d0c9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="5d0c9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="5d0c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="5d0c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="5d0c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="5d0c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="5d0c9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="5d0c9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="5d0c9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="5d0c9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d0c9-112">語法</span><span class="sxs-lookup"><span data-stu-id="5d0c9-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d0c9-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="5d0c9-113">Attributes and elements</span></span>

<span data-ttu-id="5d0c9-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5d0c9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d0c9-115">屬性</span><span class="sxs-lookup"><span data-stu-id="5d0c9-115">Attributes</span></span>  

<span data-ttu-id="5d0c9-116">無。</span><span class="sxs-lookup"><span data-stu-id="5d0c9-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d0c9-117">子元素</span><span class="sxs-lookup"><span data-stu-id="5d0c9-117">Child elements</span></span>  
  
|<span data-ttu-id="5d0c9-118">項目</span><span class="sxs-lookup"><span data-stu-id="5d0c9-118">Element</span></span>|<span data-ttu-id="5d0c9-119">描述</span><span class="sxs-lookup"><span data-stu-id="5d0c9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d0c9-120">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="5d0c9-120">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="5d0c9-121">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="5d0c9-121">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d0c9-122">父元素</span><span class="sxs-lookup"><span data-stu-id="5d0c9-122">Parent elements</span></span>  
  
|<span data-ttu-id="5d0c9-123">元素</span><span class="sxs-lookup"><span data-stu-id="5d0c9-123">Element</span></span>|<span data-ttu-id="5d0c9-124">說明</span><span class="sxs-lookup"><span data-stu-id="5d0c9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d0c9-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5d0c9-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="5d0c9-126">Configuration 元素，其中包含[activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="5d0c9-126">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d0c9-127">備註</span><span class="sxs-lookup"><span data-stu-id="5d0c9-127">Remarks</span></span>

<span data-ttu-id="5d0c9-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="5d0c9-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="5d0c9-129">範例</span><span class="sxs-lookup"><span data-stu-id="5d0c9-129">Example</span></span>  

<span data-ttu-id="5d0c9-130">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="5d0c9-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="5d0c9-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d0c9-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5d0c9-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="5d0c9-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5d0c9-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5d0c9-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
