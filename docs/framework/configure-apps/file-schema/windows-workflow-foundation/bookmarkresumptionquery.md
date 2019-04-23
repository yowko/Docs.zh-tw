---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: e43ba66e2c3ccfbb723b1eea8ef6774ad3f9f2aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140032"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="b6f09-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="b6f09-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="b6f09-102">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="b6f09-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b6f09-103">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="b6f09-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="b6f09-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b6f09-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b6f09-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b6f09-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b6f09-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b6f09-106">\<tracking></span></span>  
<span data-ttu-id="b6f09-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b6f09-107">\<trackingProfile></span></span>  
<span data-ttu-id="b6f09-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b6f09-108">\<workflow></span></span>  
<span data-ttu-id="b6f09-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="b6f09-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="b6f09-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="b6f09-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f09-111">語法</span><span class="sxs-lookup"><span data-stu-id="b6f09-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6f09-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b6f09-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b6f09-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b6f09-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6f09-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b6f09-114">Attributes</span></span>  
  
|<span data-ttu-id="b6f09-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b6f09-115">Attribute</span></span>|<span data-ttu-id="b6f09-116">描述</span><span class="sxs-lookup"><span data-stu-id="b6f09-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6f09-117">名稱</span><span class="sxs-lookup"><span data-stu-id="b6f09-117">name</span></span>|<span data-ttu-id="b6f09-118">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f09-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6f09-119">子元素</span><span class="sxs-lookup"><span data-stu-id="b6f09-119">Child Elements</span></span>  
 <span data-ttu-id="b6f09-120">無。</span><span class="sxs-lookup"><span data-stu-id="b6f09-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6f09-121">父項目</span><span class="sxs-lookup"><span data-stu-id="b6f09-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b6f09-122">項目</span><span class="sxs-lookup"><span data-stu-id="b6f09-122">Element</span></span>|<span data-ttu-id="b6f09-123">描述</span><span class="sxs-lookup"><span data-stu-id="b6f09-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6f09-124">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="b6f09-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="b6f09-125">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="b6f09-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6f09-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6f09-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b6f09-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b6f09-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b6f09-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b6f09-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
