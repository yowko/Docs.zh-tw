---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163159"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="5ee0b-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="5ee0b-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="5ee0b-102">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="5ee0b-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5ee0b-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="5ee0b-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="5ee0b-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5ee0b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5ee0b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5ee0b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5ee0b-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="5ee0b-106">\<tracking></span></span>  
<span data-ttu-id="5ee0b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5ee0b-107">\<trackingProfile></span></span>  
<span data-ttu-id="5ee0b-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5ee0b-108">\<workflow></span></span>  
<span data-ttu-id="5ee0b-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="5ee0b-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee0b-110">語法</span><span class="sxs-lookup"><span data-stu-id="5ee0b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ee0b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5ee0b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5ee0b-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5ee0b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ee0b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5ee0b-113">Attributes</span></span>  
 <span data-ttu-id="5ee0b-114">無。</span><span class="sxs-lookup"><span data-stu-id="5ee0b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ee0b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="5ee0b-115">Child Elements</span></span>  
  
|<span data-ttu-id="5ee0b-116">項目</span><span class="sxs-lookup"><span data-stu-id="5ee0b-116">Element</span></span>|<span data-ttu-id="5ee0b-117">描述</span><span class="sxs-lookup"><span data-stu-id="5ee0b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ee0b-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="5ee0b-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="5ee0b-119">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="5ee0b-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ee0b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="5ee0b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5ee0b-121">項目</span><span class="sxs-lookup"><span data-stu-id="5ee0b-121">Element</span></span>|<span data-ttu-id="5ee0b-122">描述</span><span class="sxs-lookup"><span data-stu-id="5ee0b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ee0b-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5ee0b-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5ee0b-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="5ee0b-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ee0b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ee0b-125">See also</span></span>

- [<span data-ttu-id="5ee0b-126">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="5ee0b-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5ee0b-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5ee0b-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
