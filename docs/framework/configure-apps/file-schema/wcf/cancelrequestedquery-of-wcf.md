---
title: WCF 的 &lt;cancelRequestedQuery&gt;
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 72fd23097760375738c2116b4535940873436986
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498264"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="3b420-102">WCF 的 &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="3b420-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>

<span data-ttu-id="3b420-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="3b420-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3b420-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="3b420-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="3b420-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="3b420-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="3b420-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3b420-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3b420-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3b420-107">\<tracking></span></span>  
<span data-ttu-id="3b420-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="3b420-108">\<profiles></span></span>  
<span data-ttu-id="3b420-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3b420-109">\<trackingProfile></span></span>  
<span data-ttu-id="3b420-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3b420-110">\<workflow></span></span>  
<span data-ttu-id="3b420-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="3b420-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="3b420-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="3b420-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b420-113">語法</span><span class="sxs-lookup"><span data-stu-id="3b420-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b420-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="3b420-114">Attributes and elements</span></span>

<span data-ttu-id="3b420-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3b420-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b420-116">屬性</span><span class="sxs-lookup"><span data-stu-id="3b420-116">Attributes</span></span>  
  
|<span data-ttu-id="3b420-117">屬性</span><span class="sxs-lookup"><span data-stu-id="3b420-117">Attribute</span></span>|<span data-ttu-id="3b420-118">描述</span><span class="sxs-lookup"><span data-stu-id="3b420-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="3b420-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3b420-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="3b420-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3b420-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b420-121">子元素</span><span class="sxs-lookup"><span data-stu-id="3b420-121">Child elements</span></span>

<span data-ttu-id="3b420-122">無。</span><span class="sxs-lookup"><span data-stu-id="3b420-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="3b420-123">父元素</span><span class="sxs-lookup"><span data-stu-id="3b420-123">Parent elements</span></span>
  
|<span data-ttu-id="3b420-124">元素</span><span class="sxs-lookup"><span data-stu-id="3b420-124">Element</span></span>|<span data-ttu-id="3b420-125">描述</span><span class="sxs-lookup"><span data-stu-id="3b420-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b420-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="3b420-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="3b420-127">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="3b420-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b420-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b420-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3b420-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="3b420-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3b420-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="3b420-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
