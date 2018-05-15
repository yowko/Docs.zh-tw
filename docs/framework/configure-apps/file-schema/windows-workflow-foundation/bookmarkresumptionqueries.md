---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: b0ce29213f1f281e8581b90dda17aba1bdc29072
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="d8790-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="d8790-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="d8790-103">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="d8790-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8790-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="d8790-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="d8790-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8790-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d8790-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d8790-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d8790-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d8790-107">\<tracking></span></span>  
<span data-ttu-id="d8790-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d8790-108">\<trackingProfile></span></span>  
<span data-ttu-id="d8790-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d8790-109">\<workflow></span></span>  
<span data-ttu-id="d8790-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="d8790-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="d8790-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="d8790-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8790-112">語法</span><span class="sxs-lookup"><span data-stu-id="d8790-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8790-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8790-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d8790-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8790-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8790-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d8790-115">Attributes</span></span>  
 <span data-ttu-id="d8790-116">無。</span><span class="sxs-lookup"><span data-stu-id="d8790-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8790-117">子項目</span><span class="sxs-lookup"><span data-stu-id="d8790-117">Child Elements</span></span>  
  
|<span data-ttu-id="d8790-118">項目</span><span class="sxs-lookup"><span data-stu-id="d8790-118">Element</span></span>|<span data-ttu-id="d8790-119">描述</span><span class="sxs-lookup"><span data-stu-id="d8790-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8790-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="d8790-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="d8790-121">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="d8790-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8790-122">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="d8790-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8790-123">父項目</span><span class="sxs-lookup"><span data-stu-id="d8790-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d8790-124">項目</span><span class="sxs-lookup"><span data-stu-id="d8790-124">Element</span></span>|<span data-ttu-id="d8790-125">描述</span><span class="sxs-lookup"><span data-stu-id="d8790-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8790-126">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d8790-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d8790-127">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="d8790-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8790-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8790-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="d8790-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d8790-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d8790-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d8790-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
