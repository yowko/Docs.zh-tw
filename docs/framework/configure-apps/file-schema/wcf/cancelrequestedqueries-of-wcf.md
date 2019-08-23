---
title: <cancelRequestedQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 0f04fc928358c96ca3112422f1a6ccd039269e47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926239"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="b9373-102">\<WCF 的 cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b9373-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="b9373-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="b9373-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b9373-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="b9373-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="b9373-105">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b9373-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b9373-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b9373-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b9373-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="b9373-107">\<tracking></span></span>  
<span data-ttu-id="b9373-108">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b9373-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="b9373-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="b9373-109">\<workflow></span></span>  
<span data-ttu-id="b9373-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="b9373-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9373-111">語法</span><span class="sxs-lookup"><span data-stu-id="b9373-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9373-112">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="b9373-112">Attributes and elements</span></span>  

<span data-ttu-id="b9373-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b9373-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9373-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b9373-114">Attributes</span></span>

<span data-ttu-id="b9373-115">無。</span><span class="sxs-lookup"><span data-stu-id="b9373-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="b9373-116">子元素</span><span class="sxs-lookup"><span data-stu-id="b9373-116">Child elements</span></span>
  
|<span data-ttu-id="b9373-117">項目</span><span class="sxs-lookup"><span data-stu-id="b9373-117">Element</span></span>|<span data-ttu-id="b9373-118">描述</span><span class="sxs-lookup"><span data-stu-id="b9373-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9373-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="b9373-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="b9373-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="b9373-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9373-121">父元素</span><span class="sxs-lookup"><span data-stu-id="b9373-121">Parent elements</span></span>  
  
|<span data-ttu-id="b9373-122">元素</span><span class="sxs-lookup"><span data-stu-id="b9373-122">Element</span></span>|<span data-ttu-id="b9373-123">說明</span><span class="sxs-lookup"><span data-stu-id="b9373-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9373-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b9373-124">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b9373-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="b9373-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9373-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9373-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="b9373-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b9373-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b9373-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b9373-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
