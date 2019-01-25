---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a3d24536589288ce9585901f3d955075bc856c97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520304"
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="c5eae-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="c5eae-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="c5eae-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="c5eae-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c5eae-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="c5eae-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c5eae-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="c5eae-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c5eae-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5eae-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c5eae-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c5eae-107">\<tracking></span></span>  
<span data-ttu-id="c5eae-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c5eae-108">\<trackingProfile></span></span>  
<span data-ttu-id="c5eae-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c5eae-109">\<workflow></span></span>  
<span data-ttu-id="c5eae-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="c5eae-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="c5eae-111">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="c5eae-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5eae-112">語法</span><span class="sxs-lookup"><span data-stu-id="c5eae-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5eae-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5eae-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c5eae-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c5eae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5eae-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c5eae-115">Attributes</span></span>  
  
|<span data-ttu-id="c5eae-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c5eae-116">Attribute</span></span>|<span data-ttu-id="c5eae-117">描述</span><span class="sxs-lookup"><span data-stu-id="c5eae-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5eae-118">activityName</span><span class="sxs-lookup"><span data-stu-id="c5eae-118">activityName</span></span>|<span data-ttu-id="c5eae-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c5eae-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="c5eae-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="c5eae-120">childActivityName</span></span>|<span data-ttu-id="c5eae-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c5eae-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5eae-122">子元素</span><span class="sxs-lookup"><span data-stu-id="c5eae-122">Child Elements</span></span>  
 <span data-ttu-id="c5eae-123">無。</span><span class="sxs-lookup"><span data-stu-id="c5eae-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5eae-124">父項目</span><span class="sxs-lookup"><span data-stu-id="c5eae-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c5eae-125">項目</span><span class="sxs-lookup"><span data-stu-id="c5eae-125">Element</span></span>|<span data-ttu-id="c5eae-126">描述</span><span class="sxs-lookup"><span data-stu-id="c5eae-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5eae-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="c5eae-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="c5eae-128">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="c5eae-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c5eae-129">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="c5eae-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5eae-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5eae-130">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c5eae-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c5eae-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c5eae-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c5eae-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
