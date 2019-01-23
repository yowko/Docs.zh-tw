---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 5bc2e3ffeb93bdfcd45638d6b50e218c03706f42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520681"
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="501e5-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="501e5-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="501e5-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="501e5-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="501e5-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="501e5-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="501e5-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="501e5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="501e5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="501e5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="501e5-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="501e5-107">\<tracking></span></span>  
<span data-ttu-id="501e5-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="501e5-108">\<trackingProfile></span></span>  
<span data-ttu-id="501e5-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="501e5-109">\<workflow></span></span>  
<span data-ttu-id="501e5-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="501e5-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="501e5-111">語法</span><span class="sxs-lookup"><span data-stu-id="501e5-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="501e5-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="501e5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="501e5-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="501e5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="501e5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="501e5-114">Attributes</span></span>  
 <span data-ttu-id="501e5-115">無。</span><span class="sxs-lookup"><span data-stu-id="501e5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="501e5-116">子元素</span><span class="sxs-lookup"><span data-stu-id="501e5-116">Child Elements</span></span>  
  
|<span data-ttu-id="501e5-117">項目</span><span class="sxs-lookup"><span data-stu-id="501e5-117">Element</span></span>|<span data-ttu-id="501e5-118">描述</span><span class="sxs-lookup"><span data-stu-id="501e5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="501e5-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="501e5-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="501e5-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="501e5-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="501e5-121">父項目</span><span class="sxs-lookup"><span data-stu-id="501e5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="501e5-122">項目</span><span class="sxs-lookup"><span data-stu-id="501e5-122">Element</span></span>|<span data-ttu-id="501e5-123">描述</span><span class="sxs-lookup"><span data-stu-id="501e5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="501e5-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="501e5-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="501e5-125">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="501e5-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="501e5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="501e5-126">See also</span></span>
- [<span data-ttu-id="501e5-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="501e5-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="501e5-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="501e5-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
