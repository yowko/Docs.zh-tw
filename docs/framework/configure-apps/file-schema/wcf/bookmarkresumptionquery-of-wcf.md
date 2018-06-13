---
title: WCF 的 &lt;bookmarkResumptionQuery&gt;
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 083b42efdd2b10dad870b6590fc20331a090f8aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748252"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="1ce8d-102">WCF 的 &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="1ce8d-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="1ce8d-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="1ce8d-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1ce8d-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="1ce8d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="1ce8d-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1ce8d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="1ce8d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1ce8d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1ce8d-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="1ce8d-107">\<tracking></span></span>  
<span data-ttu-id="1ce8d-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1ce8d-108">\<trackingProfile></span></span>  
<span data-ttu-id="1ce8d-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="1ce8d-109">\<workflow></span></span>  
<span data-ttu-id="1ce8d-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="1ce8d-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="1ce8d-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="1ce8d-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ce8d-112">語法</span><span class="sxs-lookup"><span data-stu-id="1ce8d-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ce8d-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ce8d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1ce8d-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1ce8d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ce8d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1ce8d-115">Attributes</span></span>  
  
|<span data-ttu-id="1ce8d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="1ce8d-116">Attribute</span></span>|<span data-ttu-id="1ce8d-117">描述</span><span class="sxs-lookup"><span data-stu-id="1ce8d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ce8d-118">name</span><span class="sxs-lookup"><span data-stu-id="1ce8d-118">name</span></span>|<span data-ttu-id="1ce8d-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ce8d-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ce8d-120">子項目</span><span class="sxs-lookup"><span data-stu-id="1ce8d-120">Child Elements</span></span>  
 <span data-ttu-id="1ce8d-121">無。</span><span class="sxs-lookup"><span data-stu-id="1ce8d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ce8d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="1ce8d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1ce8d-123">項目</span><span class="sxs-lookup"><span data-stu-id="1ce8d-123">Element</span></span>|<span data-ttu-id="1ce8d-124">描述</span><span class="sxs-lookup"><span data-stu-id="1ce8d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ce8d-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="1ce8d-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="1ce8d-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="1ce8d-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ce8d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ce8d-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="1ce8d-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="1ce8d-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1ce8d-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="1ce8d-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
