---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 628dbf801cae5f61dc7d518c27df3380dd2d3d23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945940"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="cf05b-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="cf05b-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="cf05b-102">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="cf05b-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="cf05b-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="cf05b-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="cf05b-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cf05b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cf05b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cf05b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cf05b-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="cf05b-106">\<tracking></span></span>  
<span data-ttu-id="cf05b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cf05b-107">\<trackingProfile></span></span>  
<span data-ttu-id="cf05b-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="cf05b-108">\<workflow></span></span>  
<span data-ttu-id="cf05b-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="cf05b-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf05b-110">語法</span><span class="sxs-lookup"><span data-stu-id="cf05b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf05b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf05b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf05b-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cf05b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf05b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cf05b-113">Attributes</span></span>  
 <span data-ttu-id="cf05b-114">無。</span><span class="sxs-lookup"><span data-stu-id="cf05b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf05b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="cf05b-115">Child Elements</span></span>  
  
|<span data-ttu-id="cf05b-116">項目</span><span class="sxs-lookup"><span data-stu-id="cf05b-116">Element</span></span>|<span data-ttu-id="cf05b-117">描述</span><span class="sxs-lookup"><span data-stu-id="cf05b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf05b-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="cf05b-118">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="cf05b-119">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="cf05b-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf05b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cf05b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cf05b-121">項目</span><span class="sxs-lookup"><span data-stu-id="cf05b-121">Element</span></span>|<span data-ttu-id="cf05b-122">說明</span><span class="sxs-lookup"><span data-stu-id="cf05b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf05b-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cf05b-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cf05b-124">Configuration 元素, 其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="cf05b-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf05b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf05b-125">See also</span></span>

- [<span data-ttu-id="cf05b-126">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="cf05b-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cf05b-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="cf05b-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
