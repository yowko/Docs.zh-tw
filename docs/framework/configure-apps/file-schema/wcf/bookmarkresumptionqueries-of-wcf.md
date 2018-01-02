---
title: "WCF 的 &lt;bookmarkResumptionQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c29f4c0cd92b2c4e8263e1893e7deefc2f14624a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="4fef5-102">WCF 的 &lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="4fef5-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="4fef5-103">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="4fef5-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4fef5-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="4fef5-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="4fef5-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4fef5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="4fef5-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4fef5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4fef5-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="4fef5-107">\<tracking></span></span>  
<span data-ttu-id="4fef5-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4fef5-108">\<trackingProfile></span></span>  
<span data-ttu-id="4fef5-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="4fef5-109">\<workflow></span></span>  
<span data-ttu-id="4fef5-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="4fef5-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="4fef5-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="4fef5-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fef5-112">語法</span><span class="sxs-lookup"><span data-stu-id="4fef5-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4fef5-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4fef5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4fef5-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4fef5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fef5-115">屬性</span><span class="sxs-lookup"><span data-stu-id="4fef5-115">Attributes</span></span>  
 <span data-ttu-id="4fef5-116">無。</span><span class="sxs-lookup"><span data-stu-id="4fef5-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4fef5-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4fef5-117">Child Elements</span></span>  
  
|<span data-ttu-id="4fef5-118">項目</span><span class="sxs-lookup"><span data-stu-id="4fef5-118">Element</span></span>|<span data-ttu-id="4fef5-119">描述</span><span class="sxs-lookup"><span data-stu-id="4fef5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fef5-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="4fef5-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="4fef5-121">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="4fef5-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4fef5-122">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="4fef5-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fef5-123">父項目</span><span class="sxs-lookup"><span data-stu-id="4fef5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4fef5-124">項目</span><span class="sxs-lookup"><span data-stu-id="4fef5-124">Element</span></span>|<span data-ttu-id="4fef5-125">描述</span><span class="sxs-lookup"><span data-stu-id="4fef5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fef5-126">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="4fef5-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="4fef5-127">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="4fef5-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fef5-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="4fef5-128">See Also</span></span>  
 <span data-ttu-id="4fef5-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4fef5-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4fef5-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4fef5-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="4fef5-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="4fef5-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4fef5-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4fef5-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
