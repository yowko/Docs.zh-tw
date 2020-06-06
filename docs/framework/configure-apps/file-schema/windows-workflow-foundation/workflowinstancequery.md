---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397506"
---
# \<workflowInstanceQuery>
<span data-ttu-id="d0fcf-101">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-101">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="d0fcf-102">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d0fcf-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="d0fcf-103">語法</span><span class="sxs-lookup"><span data-stu-id="d0fcf-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0fcf-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0fcf-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d0fcf-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0fcf-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d0fcf-106">Attributes</span></span>  
 <span data-ttu-id="d0fcf-107">無。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0fcf-108">子元素</span><span class="sxs-lookup"><span data-stu-id="d0fcf-108">Child Elements</span></span>  
  
|<span data-ttu-id="d0fcf-109">元素</span><span class="sxs-lookup"><span data-stu-id="d0fcf-109">Element</span></span>|<span data-ttu-id="d0fcf-110">描述</span><span class="sxs-lookup"><span data-stu-id="d0fcf-110">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="d0fcf-111">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-111">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0fcf-112">父項目</span><span class="sxs-lookup"><span data-stu-id="d0fcf-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d0fcf-113">元素</span><span class="sxs-lookup"><span data-stu-id="d0fcf-113">Element</span></span>|<span data-ttu-id="d0fcf-114">描述</span><span class="sxs-lookup"><span data-stu-id="d0fcf-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="d0fcf-115">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-115">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0fcf-116">備註</span><span class="sxs-lookup"><span data-stu-id="d0fcf-116">Remarks</span></span>  
 <span data-ttu-id="d0fcf-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="d0fcf-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="d0fcf-118">範例</span><span class="sxs-lookup"><span data-stu-id="d0fcf-118">Example</span></span>  
 <span data-ttu-id="d0fcf-119">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0fcf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0fcf-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d0fcf-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d0fcf-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d0fcf-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d0fcf-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
