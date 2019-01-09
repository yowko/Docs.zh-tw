---
title: WCF 的 &lt;bookmarkResumptionQuery&gt;
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 6463404e17edff8eb1efe3f96e44b5b9997ffca3
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147807"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="fadfb-102">WCF 的 &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="fadfb-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>

<span data-ttu-id="fadfb-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="fadfb-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fadfb-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="fadfb-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="fadfb-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fadfb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="fadfb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fadfb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fadfb-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="fadfb-107">\<tracking></span></span>  
<span data-ttu-id="fadfb-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="fadfb-108">\<profiles></span></span>  
<span data-ttu-id="fadfb-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fadfb-109">\<trackingProfile></span></span>  
<span data-ttu-id="fadfb-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="fadfb-110">\<workflow></span></span>  
<span data-ttu-id="fadfb-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="fadfb-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="fadfb-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="fadfb-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fadfb-113">語法</span><span class="sxs-lookup"><span data-stu-id="fadfb-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fadfb-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="fadfb-114">Attributes and elements</span></span>

<span data-ttu-id="fadfb-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fadfb-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fadfb-116">屬性</span><span class="sxs-lookup"><span data-stu-id="fadfb-116">Attributes</span></span>  
  
|<span data-ttu-id="fadfb-117">屬性</span><span class="sxs-lookup"><span data-stu-id="fadfb-117">Attribute</span></span>|<span data-ttu-id="fadfb-118">描述</span><span class="sxs-lookup"><span data-stu-id="fadfb-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="fadfb-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="fadfb-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fadfb-120">子元素</span><span class="sxs-lookup"><span data-stu-id="fadfb-120">Child elements</span></span>

<span data-ttu-id="fadfb-121">無。</span><span class="sxs-lookup"><span data-stu-id="fadfb-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="fadfb-122">父元素</span><span class="sxs-lookup"><span data-stu-id="fadfb-122">Parent elements</span></span>  
  
|<span data-ttu-id="fadfb-123">元素</span><span class="sxs-lookup"><span data-stu-id="fadfb-123">Element</span></span>|<span data-ttu-id="fadfb-124">描述</span><span class="sxs-lookup"><span data-stu-id="fadfb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fadfb-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="fadfb-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="fadfb-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="fadfb-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fadfb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fadfb-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fadfb-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="fadfb-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fadfb-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="fadfb-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
