---
title: "WCF 的 &lt;bookmarkResumptionQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124b05d8e1ce9831a1efb3c6e62cc5e9fd3058fc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="b327b-102">WCF 的 &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b327b-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="b327b-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="b327b-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b327b-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="b327b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="b327b-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b327b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="b327b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b327b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b327b-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="b327b-107">\<tracking></span></span>  
<span data-ttu-id="b327b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b327b-108">\<trackingProfile></span></span>  
<span data-ttu-id="b327b-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="b327b-109">\<workflow></span></span>  
<span data-ttu-id="b327b-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="b327b-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="b327b-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="b327b-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b327b-112">語法</span><span class="sxs-lookup"><span data-stu-id="b327b-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b327b-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b327b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b327b-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b327b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b327b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b327b-115">Attributes</span></span>  
  
|<span data-ttu-id="b327b-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b327b-116">Attribute</span></span>|<span data-ttu-id="b327b-117">描述</span><span class="sxs-lookup"><span data-stu-id="b327b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b327b-118">name</span><span class="sxs-lookup"><span data-stu-id="b327b-118">name</span></span>|<span data-ttu-id="b327b-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b327b-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b327b-120">子元素</span><span class="sxs-lookup"><span data-stu-id="b327b-120">Child Elements</span></span>  
 <span data-ttu-id="b327b-121">無。</span><span class="sxs-lookup"><span data-stu-id="b327b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b327b-122">父項目</span><span class="sxs-lookup"><span data-stu-id="b327b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b327b-123">項目</span><span class="sxs-lookup"><span data-stu-id="b327b-123">Element</span></span>|<span data-ttu-id="b327b-124">說明</span><span class="sxs-lookup"><span data-stu-id="b327b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b327b-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="b327b-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="b327b-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="b327b-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b327b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b327b-127">See Also</span></span>  
 <span data-ttu-id="b327b-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b327b-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b327b-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b327b-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b327b-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b327b-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b327b-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b327b-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
