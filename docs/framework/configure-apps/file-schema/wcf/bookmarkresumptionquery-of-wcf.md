---
title: <bookmarkResumptionQuery> WCF 的
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 38c87cefc49821b03d119299ef60e3fbbad21d7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704384"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="dda07-102">\<bookmarkResumptionQuery > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="dda07-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="dda07-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="dda07-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="dda07-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="dda07-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="dda07-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dda07-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="dda07-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dda07-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dda07-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="dda07-107">\<tracking></span></span>  
<span data-ttu-id="dda07-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="dda07-108">\<profiles></span></span>  
<span data-ttu-id="dda07-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dda07-109">\<trackingProfile></span></span>  
<span data-ttu-id="dda07-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="dda07-110">\<workflow></span></span>  
<span data-ttu-id="dda07-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="dda07-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="dda07-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="dda07-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda07-113">語法</span><span class="sxs-lookup"><span data-stu-id="dda07-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dda07-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="dda07-114">Attributes and elements</span></span>

<span data-ttu-id="dda07-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dda07-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dda07-116">屬性</span><span class="sxs-lookup"><span data-stu-id="dda07-116">Attributes</span></span>  
  
|<span data-ttu-id="dda07-117">屬性</span><span class="sxs-lookup"><span data-stu-id="dda07-117">Attribute</span></span>|<span data-ttu-id="dda07-118">描述</span><span class="sxs-lookup"><span data-stu-id="dda07-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="dda07-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="dda07-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dda07-120">子元素</span><span class="sxs-lookup"><span data-stu-id="dda07-120">Child elements</span></span>

<span data-ttu-id="dda07-121">無。</span><span class="sxs-lookup"><span data-stu-id="dda07-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="dda07-122">父元素</span><span class="sxs-lookup"><span data-stu-id="dda07-122">Parent elements</span></span>  
  
|<span data-ttu-id="dda07-123">元素</span><span class="sxs-lookup"><span data-stu-id="dda07-123">Element</span></span>|<span data-ttu-id="dda07-124">描述</span><span class="sxs-lookup"><span data-stu-id="dda07-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dda07-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="dda07-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="dda07-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="dda07-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dda07-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dda07-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dda07-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="dda07-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dda07-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="dda07-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
