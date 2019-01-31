---
title: <bookmarkResumptionQueries> WCF 的
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 4b11543e240b482d52c157083d1184db4f81bb04
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261265"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="608ef-102">\<bookmarkResumptionQueries > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="608ef-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="608ef-103">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="608ef-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="608ef-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="608ef-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="608ef-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="608ef-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="608ef-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="608ef-106">\<system.serviceModel></span></span>  
<span data-ttu-id="608ef-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="608ef-107">\<tracking></span></span>  
<span data-ttu-id="608ef-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="608ef-108">\<profiles></span></span>  
<span data-ttu-id="608ef-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="608ef-109">\<trackingProfile></span></span>  
<span data-ttu-id="608ef-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="608ef-110">\<workflow></span></span>  
<span data-ttu-id="608ef-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="608ef-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="608ef-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="608ef-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="608ef-113">語法</span><span class="sxs-lookup"><span data-stu-id="608ef-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="608ef-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="608ef-114">Attributes and elements</span></span>  
  
<span data-ttu-id="608ef-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="608ef-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="608ef-116">屬性</span><span class="sxs-lookup"><span data-stu-id="608ef-116">Attributes</span></span>  
  
<span data-ttu-id="608ef-117">無。</span><span class="sxs-lookup"><span data-stu-id="608ef-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="608ef-118">子元素</span><span class="sxs-lookup"><span data-stu-id="608ef-118">Child elements</span></span>  
  
|<span data-ttu-id="608ef-119">項目</span><span class="sxs-lookup"><span data-stu-id="608ef-119">Element</span></span>|<span data-ttu-id="608ef-120">描述</span><span class="sxs-lookup"><span data-stu-id="608ef-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="608ef-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="608ef-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="608ef-122">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="608ef-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="608ef-123">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="608ef-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="608ef-124">父元素</span><span class="sxs-lookup"><span data-stu-id="608ef-124">Parent elements</span></span>  
  
|<span data-ttu-id="608ef-125">元素</span><span class="sxs-lookup"><span data-stu-id="608ef-125">Element</span></span>|<span data-ttu-id="608ef-126">描述</span><span class="sxs-lookup"><span data-stu-id="608ef-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="608ef-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="608ef-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="608ef-128">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="608ef-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="608ef-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="608ef-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="608ef-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="608ef-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="608ef-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="608ef-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
