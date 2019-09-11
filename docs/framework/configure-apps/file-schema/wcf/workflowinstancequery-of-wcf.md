---
title: <workflowInstanceQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854736"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="f4a24-102">\<WCF 的 workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f4a24-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="f4a24-103">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="f4a24-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f4a24-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f4a24-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4a24-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f4a24-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="f4a24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="f4a24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="f4a24-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="f4a24-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="f4a24-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f4a24-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="f4a24-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="f4a24-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a24-113">語法</span><span class="sxs-lookup"><span data-stu-id="f4a24-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4a24-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f4a24-114">Attributes and elements</span></span>  

<span data-ttu-id="f4a24-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f4a24-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4a24-116">屬性</span><span class="sxs-lookup"><span data-stu-id="f4a24-116">Attributes</span></span>  

<span data-ttu-id="f4a24-117">無。</span><span class="sxs-lookup"><span data-stu-id="f4a24-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4a24-118">子元素</span><span class="sxs-lookup"><span data-stu-id="f4a24-118">Child elements</span></span>  
  
|<span data-ttu-id="f4a24-119">項目</span><span class="sxs-lookup"><span data-stu-id="f4a24-119">Element</span></span>|<span data-ttu-id="f4a24-120">描述</span><span class="sxs-lookup"><span data-stu-id="f4a24-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4a24-121">\<states></span><span class="sxs-lookup"><span data-stu-id="f4a24-121">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="f4a24-122">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="f4a24-122">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4a24-123">父元素</span><span class="sxs-lookup"><span data-stu-id="f4a24-123">Parent elements</span></span>  
  
|<span data-ttu-id="f4a24-124">元素</span><span class="sxs-lookup"><span data-stu-id="f4a24-124">Element</span></span>|<span data-ttu-id="f4a24-125">描述</span><span class="sxs-lookup"><span data-stu-id="f4a24-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4a24-126">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f4a24-126">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="f4a24-127">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="f4a24-127">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4a24-128">備註</span><span class="sxs-lookup"><span data-stu-id="f4a24-128">Remarks</span></span>  

<span data-ttu-id="f4a24-129"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="f4a24-129">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f4a24-130">範例</span><span class="sxs-lookup"><span data-stu-id="f4a24-130">Example</span></span>  

<span data-ttu-id="f4a24-131">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="f4a24-131">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="f4a24-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4a24-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f4a24-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="f4a24-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f4a24-134">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="f4a24-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
