---
title: <workflowInstanceQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854767"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="81954-102">\<workflowInstanceQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="81954-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="81954-103">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="81954-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="81954-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="81954-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="81954-105">語法</span><span class="sxs-lookup"><span data-stu-id="81954-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81954-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="81954-106">Attributes and elements</span></span>

<span data-ttu-id="81954-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="81954-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81954-108">屬性</span><span class="sxs-lookup"><span data-stu-id="81954-108">Attributes</span></span>  

<span data-ttu-id="81954-109">無。</span><span class="sxs-lookup"><span data-stu-id="81954-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="81954-110">子元素</span><span class="sxs-lookup"><span data-stu-id="81954-110">Child elements</span></span>  
  
|<span data-ttu-id="81954-111">元素</span><span class="sxs-lookup"><span data-stu-id="81954-111">Element</span></span>|<span data-ttu-id="81954-112">描述</span><span class="sxs-lookup"><span data-stu-id="81954-112">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="81954-113">用來追蹤工作流程執行個體生命週期變更的查詢。</span><span class="sxs-lookup"><span data-stu-id="81954-113">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81954-114">父元素</span><span class="sxs-lookup"><span data-stu-id="81954-114">Parent elements</span></span>  
  
|<span data-ttu-id="81954-115">元素</span><span class="sxs-lookup"><span data-stu-id="81954-115">Element</span></span>|<span data-ttu-id="81954-116">描述</span><span class="sxs-lookup"><span data-stu-id="81954-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="81954-117">Configuration 元素，其中包含[activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="81954-117">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81954-118">備註</span><span class="sxs-lookup"><span data-stu-id="81954-118">Remarks</span></span>

<span data-ttu-id="81954-119"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="81954-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="81954-120">範例</span><span class="sxs-lookup"><span data-stu-id="81954-120">Example</span></span>  

<span data-ttu-id="81954-121">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="81954-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="81954-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81954-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="81954-123">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="81954-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="81954-124">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="81954-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
