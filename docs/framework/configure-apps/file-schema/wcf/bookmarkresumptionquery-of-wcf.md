---
title: WCF 的 &lt;bookmarkResumptionQuery&gt;
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: f0721e7e14d543b1ff212fe59ed6a2de0a8a9968
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308404"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="3c93d-102">WCF 的 &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="3c93d-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>

<span data-ttu-id="3c93d-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="3c93d-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3c93d-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="3c93d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="3c93d-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3c93d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="3c93d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3c93d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3c93d-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="3c93d-107">\<tracking></span></span>  
<span data-ttu-id="3c93d-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="3c93d-108">\<profiles></span></span>  
<span data-ttu-id="3c93d-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3c93d-109">\<trackingProfile></span></span>  
<span data-ttu-id="3c93d-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="3c93d-110">\<workflow></span></span>  
<span data-ttu-id="3c93d-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3c93d-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3c93d-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3c93d-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c93d-113">語法</span><span class="sxs-lookup"><span data-stu-id="3c93d-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="3c93d-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="3c93d-114">Attributes and elements</span></span>

<span data-ttu-id="3c93d-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c93d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c93d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="3c93d-116">Attributes</span></span>  
  
|<span data-ttu-id="3c93d-117">屬性</span><span class="sxs-lookup"><span data-stu-id="3c93d-117">Attribute</span></span>|<span data-ttu-id="3c93d-118">描述</span><span class="sxs-lookup"><span data-stu-id="3c93d-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3c93d-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c93d-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c93d-120">子元素</span><span class="sxs-lookup"><span data-stu-id="3c93d-120">Child elements</span></span>

<span data-ttu-id="3c93d-121">無。</span><span class="sxs-lookup"><span data-stu-id="3c93d-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="3c93d-122">父元素</span><span class="sxs-lookup"><span data-stu-id="3c93d-122">Parent elements</span></span>  
  
|<span data-ttu-id="3c93d-123">元素</span><span class="sxs-lookup"><span data-stu-id="3c93d-123">Element</span></span>|<span data-ttu-id="3c93d-124">描述</span><span class="sxs-lookup"><span data-stu-id="3c93d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c93d-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="3c93d-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="3c93d-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="3c93d-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c93d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c93d-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3c93d-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="3c93d-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3c93d-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="3c93d-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
