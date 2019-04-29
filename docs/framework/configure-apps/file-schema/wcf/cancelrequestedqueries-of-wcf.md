---
title: <cancelRequestedQueries> WCF 的
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: a9364fc53c7eb62a240206f6c81bd434b25c3f40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704371"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="33da0-102">\<cancelRequestedQueries > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="33da0-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="33da0-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="33da0-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="33da0-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="33da0-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="33da0-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="33da0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="33da0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="33da0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="33da0-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="33da0-107">\<tracking></span></span>  
<span data-ttu-id="33da0-108">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="33da0-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="33da0-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="33da0-109">\<workflow></span></span>  
<span data-ttu-id="33da0-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="33da0-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33da0-111">語法</span><span class="sxs-lookup"><span data-stu-id="33da0-111">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33da0-112">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="33da0-112">Attributes and elements</span></span>  

<span data-ttu-id="33da0-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="33da0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33da0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="33da0-114">Attributes</span></span>

<span data-ttu-id="33da0-115">無。</span><span class="sxs-lookup"><span data-stu-id="33da0-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="33da0-116">子元素</span><span class="sxs-lookup"><span data-stu-id="33da0-116">Child elements</span></span>
  
|<span data-ttu-id="33da0-117">項目</span><span class="sxs-lookup"><span data-stu-id="33da0-117">Element</span></span>|<span data-ttu-id="33da0-118">描述</span><span class="sxs-lookup"><span data-stu-id="33da0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33da0-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="33da0-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="33da0-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="33da0-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33da0-121">父元素</span><span class="sxs-lookup"><span data-stu-id="33da0-121">Parent elements</span></span>  
  
|<span data-ttu-id="33da0-122">元素</span><span class="sxs-lookup"><span data-stu-id="33da0-122">Element</span></span>|<span data-ttu-id="33da0-123">描述</span><span class="sxs-lookup"><span data-stu-id="33da0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33da0-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="33da0-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="33da0-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="33da0-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33da0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33da0-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="33da0-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="33da0-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="33da0-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="33da0-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
