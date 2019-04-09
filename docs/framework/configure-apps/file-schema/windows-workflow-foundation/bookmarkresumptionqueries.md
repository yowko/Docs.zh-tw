---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 186990577ec4eedc7cae3710c455816c3162fc94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109405"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="f9474-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="f9474-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="f9474-102">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="f9474-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f9474-103">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="f9474-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="f9474-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f9474-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f9474-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f9474-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f9474-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="f9474-106">\<tracking></span></span>  
<span data-ttu-id="f9474-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f9474-107">\<trackingProfile></span></span>  
<span data-ttu-id="f9474-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f9474-108">\<workflow></span></span>  
<span data-ttu-id="f9474-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="f9474-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="f9474-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f9474-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9474-111">語法</span><span class="sxs-lookup"><span data-stu-id="f9474-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9474-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f9474-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f9474-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f9474-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9474-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f9474-114">Attributes</span></span>  
 <span data-ttu-id="f9474-115">無。</span><span class="sxs-lookup"><span data-stu-id="f9474-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9474-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f9474-116">Child Elements</span></span>  
  
|<span data-ttu-id="f9474-117">項目</span><span class="sxs-lookup"><span data-stu-id="f9474-117">Element</span></span>|<span data-ttu-id="f9474-118">描述</span><span class="sxs-lookup"><span data-stu-id="f9474-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9474-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f9474-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="f9474-120">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="f9474-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f9474-121">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="f9474-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9474-122">父項目</span><span class="sxs-lookup"><span data-stu-id="f9474-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f9474-123">項目</span><span class="sxs-lookup"><span data-stu-id="f9474-123">Element</span></span>|<span data-ttu-id="f9474-124">描述</span><span class="sxs-lookup"><span data-stu-id="f9474-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9474-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f9474-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f9474-126">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="f9474-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9474-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9474-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f9474-128">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="f9474-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f9474-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="f9474-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
