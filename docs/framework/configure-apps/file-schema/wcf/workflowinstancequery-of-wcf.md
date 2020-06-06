---
title: <workflowInstanceQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854736"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="6b0d8-102">\<workflowInstanceQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="6b0d8-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="6b0d8-103">表示追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="6b0d8-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="6b0d8-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6b0d8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="6b0d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="6b0d8-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b0d8-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="6b0d8-106">Attributes and elements</span></span>  

<span data-ttu-id="6b0d8-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b0d8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b0d8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6b0d8-108">Attributes</span></span>  

<span data-ttu-id="6b0d8-109">無。</span><span class="sxs-lookup"><span data-stu-id="6b0d8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b0d8-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6b0d8-110">Child elements</span></span>  
  
|<span data-ttu-id="6b0d8-111">元素</span><span class="sxs-lookup"><span data-stu-id="6b0d8-111">Element</span></span>|<span data-ttu-id="6b0d8-112">描述</span><span class="sxs-lookup"><span data-stu-id="6b0d8-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="6b0d8-113">建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。</span><span class="sxs-lookup"><span data-stu-id="6b0d8-113">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b0d8-114">父元素</span><span class="sxs-lookup"><span data-stu-id="6b0d8-114">Parent elements</span></span>  
  
|<span data-ttu-id="6b0d8-115">元素</span><span class="sxs-lookup"><span data-stu-id="6b0d8-115">Element</span></span>|<span data-ttu-id="6b0d8-116">描述</span><span class="sxs-lookup"><span data-stu-id="6b0d8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="6b0d8-117">代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="6b0d8-117">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b0d8-118">備註</span><span class="sxs-lookup"><span data-stu-id="6b0d8-118">Remarks</span></span>  

<span data-ttu-id="6b0d8-119"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="6b0d8-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="6b0d8-120">範例</span><span class="sxs-lookup"><span data-stu-id="6b0d8-120">Example</span></span>  

<span data-ttu-id="6b0d8-121">下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="6b0d8-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b0d8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b0d8-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6b0d8-123">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="6b0d8-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6b0d8-124">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="6b0d8-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
