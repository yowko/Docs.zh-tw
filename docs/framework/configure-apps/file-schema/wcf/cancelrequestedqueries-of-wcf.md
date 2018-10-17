---
title: WCF 的 &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 40fbcafd641e93be6ba21635f4f6e6428be62c12
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49373318"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="c471f-102">WCF 的 &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c471f-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="c471f-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="c471f-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c471f-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="c471f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="c471f-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c471f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c471f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c471f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c471f-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="c471f-107">\<tracking></span></span>  
<span data-ttu-id="c471f-108">\<設定檔 > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c471f-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="c471f-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c471f-109">\<workflow></span></span>  
<span data-ttu-id="c471f-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="c471f-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c471f-111">語法</span><span class="sxs-lookup"><span data-stu-id="c471f-111">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String"/>
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c471f-112">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c471f-112">Attributes and elements</span></span>  

<span data-ttu-id="c471f-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c471f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c471f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c471f-114">Attributes</span></span>

<span data-ttu-id="c471f-115">無。</span><span class="sxs-lookup"><span data-stu-id="c471f-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="c471f-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c471f-116">Child elements</span></span>
  
|<span data-ttu-id="c471f-117">項目</span><span class="sxs-lookup"><span data-stu-id="c471f-117">Element</span></span>|<span data-ttu-id="c471f-118">描述</span><span class="sxs-lookup"><span data-stu-id="c471f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c471f-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="c471f-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="c471f-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="c471f-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c471f-121">父元素</span><span class="sxs-lookup"><span data-stu-id="c471f-121">Parent elements</span></span>  
  
|<span data-ttu-id="c471f-122">元素</span><span class="sxs-lookup"><span data-stu-id="c471f-122">Element</span></span>|<span data-ttu-id="c471f-123">描述</span><span class="sxs-lookup"><span data-stu-id="c471f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c471f-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c471f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c471f-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="c471f-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c471f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c471f-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="c471f-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c471f-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c471f-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c471f-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
