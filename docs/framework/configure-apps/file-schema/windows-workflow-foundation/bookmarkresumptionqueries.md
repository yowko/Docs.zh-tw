---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: f048612673a9b6b69c3cdded6526c76359c444e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945981"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="d8925-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="d8925-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="d8925-102">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="d8925-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8925-103">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="d8925-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="d8925-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8925-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d8925-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d8925-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d8925-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d8925-106">\<tracking></span></span>  
<span data-ttu-id="d8925-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d8925-107">\<trackingProfile></span></span>  
<span data-ttu-id="d8925-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d8925-108">\<workflow></span></span>  
<span data-ttu-id="d8925-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="d8925-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="d8925-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="d8925-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8925-111">語法</span><span class="sxs-lookup"><span data-stu-id="d8925-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8925-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8925-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d8925-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8925-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8925-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d8925-114">Attributes</span></span>  
 <span data-ttu-id="d8925-115">無。</span><span class="sxs-lookup"><span data-stu-id="d8925-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8925-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d8925-116">Child Elements</span></span>  
  
|<span data-ttu-id="d8925-117">項目</span><span class="sxs-lookup"><span data-stu-id="d8925-117">Element</span></span>|<span data-ttu-id="d8925-118">描述</span><span class="sxs-lookup"><span data-stu-id="d8925-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8925-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="d8925-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="d8925-120">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="d8925-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8925-121">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="d8925-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8925-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d8925-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d8925-123">項目</span><span class="sxs-lookup"><span data-stu-id="d8925-123">Element</span></span>|<span data-ttu-id="d8925-124">說明</span><span class="sxs-lookup"><span data-stu-id="d8925-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8925-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d8925-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="d8925-126">Configuration 元素, 其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="d8925-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8925-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8925-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d8925-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d8925-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d8925-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d8925-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
