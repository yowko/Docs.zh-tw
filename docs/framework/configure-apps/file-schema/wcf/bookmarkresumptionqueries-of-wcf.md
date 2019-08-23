---
title: <bookmarkResumptionQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 5ec9827e9862866096265da576c91b10573012d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919745"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="dc4df-102">\<WCF 的 bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="dc4df-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="dc4df-103">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="dc4df-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="dc4df-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="dc4df-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="dc4df-105">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4df-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="dc4df-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dc4df-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dc4df-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="dc4df-107">\<tracking></span></span>  
<span data-ttu-id="dc4df-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="dc4df-108">\<profiles></span></span>  
<span data-ttu-id="dc4df-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dc4df-109">\<trackingProfile></span></span>  
<span data-ttu-id="dc4df-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="dc4df-110">\<workflow></span></span>  
<span data-ttu-id="dc4df-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="dc4df-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="dc4df-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="dc4df-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4df-113">語法</span><span class="sxs-lookup"><span data-stu-id="dc4df-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc4df-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="dc4df-114">Attributes and elements</span></span>  
  
<span data-ttu-id="dc4df-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dc4df-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc4df-116">屬性</span><span class="sxs-lookup"><span data-stu-id="dc4df-116">Attributes</span></span>  
  
<span data-ttu-id="dc4df-117">無。</span><span class="sxs-lookup"><span data-stu-id="dc4df-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc4df-118">子元素</span><span class="sxs-lookup"><span data-stu-id="dc4df-118">Child elements</span></span>  
  
|<span data-ttu-id="dc4df-119">項目</span><span class="sxs-lookup"><span data-stu-id="dc4df-119">Element</span></span>|<span data-ttu-id="dc4df-120">描述</span><span class="sxs-lookup"><span data-stu-id="dc4df-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc4df-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="dc4df-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="dc4df-122">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="dc4df-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="dc4df-123">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="dc4df-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc4df-124">父元素</span><span class="sxs-lookup"><span data-stu-id="dc4df-124">Parent elements</span></span>  
  
|<span data-ttu-id="dc4df-125">元素</span><span class="sxs-lookup"><span data-stu-id="dc4df-125">Element</span></span>|<span data-ttu-id="dc4df-126">描述</span><span class="sxs-lookup"><span data-stu-id="dc4df-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc4df-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="dc4df-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="dc4df-128">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="dc4df-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc4df-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4df-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dc4df-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="dc4df-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dc4df-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="dc4df-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
