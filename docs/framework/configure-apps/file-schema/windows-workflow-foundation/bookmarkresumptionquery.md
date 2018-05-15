---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 88f9639e4ecc3105a0e58d92e443d9582f261970
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="43798-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="43798-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="43798-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="43798-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="43798-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="43798-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="43798-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="43798-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="43798-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="43798-106">\<system.serviceModel></span></span>  
<span data-ttu-id="43798-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="43798-107">\<tracking></span></span>  
<span data-ttu-id="43798-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="43798-108">\<trackingProfile></span></span>  
<span data-ttu-id="43798-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="43798-109">\<workflow></span></span>  
<span data-ttu-id="43798-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="43798-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="43798-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="43798-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43798-112">語法</span><span class="sxs-lookup"><span data-stu-id="43798-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43798-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43798-113">Attributes and Elements</span></span>  
 <span data-ttu-id="43798-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="43798-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43798-115">屬性</span><span class="sxs-lookup"><span data-stu-id="43798-115">Attributes</span></span>  
  
|<span data-ttu-id="43798-116">屬性</span><span class="sxs-lookup"><span data-stu-id="43798-116">Attribute</span></span>|<span data-ttu-id="43798-117">描述</span><span class="sxs-lookup"><span data-stu-id="43798-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43798-118">name</span><span class="sxs-lookup"><span data-stu-id="43798-118">name</span></span>|<span data-ttu-id="43798-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="43798-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43798-120">子項目</span><span class="sxs-lookup"><span data-stu-id="43798-120">Child Elements</span></span>  
 <span data-ttu-id="43798-121">無。</span><span class="sxs-lookup"><span data-stu-id="43798-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43798-122">父項目</span><span class="sxs-lookup"><span data-stu-id="43798-122">Parent Elements</span></span>  
  
|<span data-ttu-id="43798-123">項目</span><span class="sxs-lookup"><span data-stu-id="43798-123">Element</span></span>|<span data-ttu-id="43798-124">描述</span><span class="sxs-lookup"><span data-stu-id="43798-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43798-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="43798-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="43798-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="43798-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43798-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43798-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="43798-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="43798-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="43798-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="43798-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
