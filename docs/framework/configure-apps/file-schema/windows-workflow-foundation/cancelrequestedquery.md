---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: d9c3f91edb41bd034bcd978b075d62f74b6e308d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945878"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="2867b-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="2867b-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="2867b-102">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="2867b-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2867b-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="2867b-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="2867b-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="2867b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2867b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2867b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2867b-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="2867b-106">\<tracking></span></span>  
<span data-ttu-id="2867b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2867b-107">\<trackingProfile></span></span>  
<span data-ttu-id="2867b-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="2867b-108">\<workflow></span></span>  
<span data-ttu-id="2867b-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="2867b-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="2867b-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="2867b-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2867b-111">語法</span><span class="sxs-lookup"><span data-stu-id="2867b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2867b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2867b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2867b-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2867b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2867b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2867b-114">Attributes</span></span>  
  
|<span data-ttu-id="2867b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="2867b-115">Attribute</span></span>|<span data-ttu-id="2867b-116">描述</span><span class="sxs-lookup"><span data-stu-id="2867b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2867b-117">activityName</span><span class="sxs-lookup"><span data-stu-id="2867b-117">activityName</span></span>|<span data-ttu-id="2867b-118">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2867b-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="2867b-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="2867b-119">childActivityName</span></span>|<span data-ttu-id="2867b-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2867b-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2867b-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2867b-121">Child Elements</span></span>  
 <span data-ttu-id="2867b-122">無。</span><span class="sxs-lookup"><span data-stu-id="2867b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2867b-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2867b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2867b-124">項目</span><span class="sxs-lookup"><span data-stu-id="2867b-124">Element</span></span>|<span data-ttu-id="2867b-125">描述</span><span class="sxs-lookup"><span data-stu-id="2867b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2867b-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="2867b-126">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="2867b-127">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="2867b-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2867b-128">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="2867b-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2867b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2867b-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2867b-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2867b-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2867b-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2867b-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
