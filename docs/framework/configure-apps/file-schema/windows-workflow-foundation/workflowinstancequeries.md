---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 11e301de1ab3dbd4c97f236bfd07c5de4a632272
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398582"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="383a4-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="383a4-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="383a4-102">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="383a4-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="383a4-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="383a4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="383a4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="383a4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="383a4-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="383a4-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="383a4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="383a4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="383a4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="383a4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="383a4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="383a4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="383a4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="383a4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="383a4-110">語法</span><span class="sxs-lookup"><span data-stu-id="383a4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="383a4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="383a4-111">Attributes and Elements</span></span>  

<span data-ttu-id="383a4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="383a4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="383a4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="383a4-113">Attributes</span></span>  

<span data-ttu-id="383a4-114">無。</span><span class="sxs-lookup"><span data-stu-id="383a4-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="383a4-115">子元素</span><span class="sxs-lookup"><span data-stu-id="383a4-115">Child Elements</span></span>  
  
|<span data-ttu-id="383a4-116">項目</span><span class="sxs-lookup"><span data-stu-id="383a4-116">Element</span></span>|<span data-ttu-id="383a4-117">說明</span><span class="sxs-lookup"><span data-stu-id="383a4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="383a4-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="383a4-118">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="383a4-119">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="383a4-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="383a4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="383a4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="383a4-121">項目</span><span class="sxs-lookup"><span data-stu-id="383a4-121">Element</span></span>|<span data-ttu-id="383a4-122">說明</span><span class="sxs-lookup"><span data-stu-id="383a4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="383a4-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="383a4-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="383a4-124">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="383a4-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="383a4-125">備註</span><span class="sxs-lookup"><span data-stu-id="383a4-125">Remarks</span></span>  

<span data-ttu-id="383a4-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="383a4-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="383a4-127">範例</span><span class="sxs-lookup"><span data-stu-id="383a4-127">Example</span></span>  

<span data-ttu-id="383a4-128">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="383a4-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="383a4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="383a4-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="383a4-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="383a4-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="383a4-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="383a4-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
