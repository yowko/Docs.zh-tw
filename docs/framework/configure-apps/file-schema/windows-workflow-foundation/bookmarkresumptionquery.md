---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e52b4ef5104397d3c4b8abc89a1d637b17fcde9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="a42f4-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="a42f4-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="a42f4-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="a42f4-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a42f4-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="a42f4-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="a42f4-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a42f4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a42f4-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a42f4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a42f4-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="a42f4-107">\<tracking></span></span>  
<span data-ttu-id="a42f4-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a42f4-108">\<trackingProfile></span></span>  
<span data-ttu-id="a42f4-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="a42f4-109">\<workflow></span></span>  
<span data-ttu-id="a42f4-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a42f4-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="a42f4-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="a42f4-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42f4-112">語法</span><span class="sxs-lookup"><span data-stu-id="a42f4-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a42f4-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a42f4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a42f4-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a42f4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a42f4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="a42f4-115">Attributes</span></span>  
  
|<span data-ttu-id="a42f4-116">屬性</span><span class="sxs-lookup"><span data-stu-id="a42f4-116">Attribute</span></span>|<span data-ttu-id="a42f4-117">描述</span><span class="sxs-lookup"><span data-stu-id="a42f4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a42f4-118">name</span><span class="sxs-lookup"><span data-stu-id="a42f4-118">name</span></span>|<span data-ttu-id="a42f4-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="a42f4-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a42f4-120">子元素</span><span class="sxs-lookup"><span data-stu-id="a42f4-120">Child Elements</span></span>  
 <span data-ttu-id="a42f4-121">無。</span><span class="sxs-lookup"><span data-stu-id="a42f4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a42f4-122">父項目</span><span class="sxs-lookup"><span data-stu-id="a42f4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a42f4-123">項目</span><span class="sxs-lookup"><span data-stu-id="a42f4-123">Element</span></span>|<span data-ttu-id="a42f4-124">說明</span><span class="sxs-lookup"><span data-stu-id="a42f4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a42f4-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a42f4-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="a42f4-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="a42f4-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a42f4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a42f4-127">See Also</span></span>  
 <span data-ttu-id="a42f4-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a42f4-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a42f4-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a42f4-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="a42f4-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a42f4-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a42f4-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a42f4-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
