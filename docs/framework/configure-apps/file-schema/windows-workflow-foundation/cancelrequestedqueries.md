---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163159"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="3267c-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="3267c-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="3267c-102">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="3267c-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3267c-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="3267c-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="3267c-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3267c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3267c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3267c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3267c-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3267c-106">\<tracking></span></span>  
<span data-ttu-id="3267c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3267c-107">\<trackingProfile></span></span>  
<span data-ttu-id="3267c-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3267c-108">\<workflow></span></span>  
<span data-ttu-id="3267c-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="3267c-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3267c-110">語法</span><span class="sxs-lookup"><span data-stu-id="3267c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3267c-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3267c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3267c-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3267c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3267c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3267c-113">Attributes</span></span>  
 <span data-ttu-id="3267c-114">無。</span><span class="sxs-lookup"><span data-stu-id="3267c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3267c-115">子元素</span><span class="sxs-lookup"><span data-stu-id="3267c-115">Child Elements</span></span>  
  
|<span data-ttu-id="3267c-116">項目</span><span class="sxs-lookup"><span data-stu-id="3267c-116">Element</span></span>|<span data-ttu-id="3267c-117">描述</span><span class="sxs-lookup"><span data-stu-id="3267c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3267c-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="3267c-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="3267c-119">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="3267c-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3267c-120">父項目</span><span class="sxs-lookup"><span data-stu-id="3267c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3267c-121">項目</span><span class="sxs-lookup"><span data-stu-id="3267c-121">Element</span></span>|<span data-ttu-id="3267c-122">描述</span><span class="sxs-lookup"><span data-stu-id="3267c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3267c-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3267c-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="3267c-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="3267c-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3267c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3267c-125">See also</span></span>

- [<span data-ttu-id="3267c-126">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="3267c-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3267c-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="3267c-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
