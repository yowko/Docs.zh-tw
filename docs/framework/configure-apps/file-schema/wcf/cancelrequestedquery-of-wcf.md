---
title: WCF 的 &lt;cancelRequestedQuery&gt;
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 3943d604b586eec37a1d153f10ac049fc9bd5747
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347563"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="2bc4f-102">WCF 的 &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="2bc4f-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>

<span data-ttu-id="2bc4f-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2bc4f-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="2bc4f-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="2bc4f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2bc4f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2bc4f-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="2bc4f-107">\<tracking></span></span>  
<span data-ttu-id="2bc4f-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="2bc4f-108">\<profiles></span></span>  
<span data-ttu-id="2bc4f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2bc4f-109">\<trackingProfile></span></span>  
<span data-ttu-id="2bc4f-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="2bc4f-110">\<workflow></span></span>  
<span data-ttu-id="2bc4f-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="2bc4f-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="2bc4f-112">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="2bc4f-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc4f-113">語法</span><span class="sxs-lookup"><span data-stu-id="2bc4f-113">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                              childActivityName="String"/>
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bc4f-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2bc4f-114">Attributes and elements</span></span>

<span data-ttu-id="2bc4f-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bc4f-116">屬性</span><span class="sxs-lookup"><span data-stu-id="2bc4f-116">Attributes</span></span>  
  
|<span data-ttu-id="2bc4f-117">屬性</span><span class="sxs-lookup"><span data-stu-id="2bc4f-117">Attribute</span></span>|<span data-ttu-id="2bc4f-118">描述</span><span class="sxs-lookup"><span data-stu-id="2bc4f-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="2bc4f-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="2bc4f-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bc4f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2bc4f-121">Child elements</span></span>

<span data-ttu-id="2bc4f-122">無。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2bc4f-123">父元素</span><span class="sxs-lookup"><span data-stu-id="2bc4f-123">Parent elements</span></span>
  
|<span data-ttu-id="2bc4f-124">元素</span><span class="sxs-lookup"><span data-stu-id="2bc4f-124">Element</span></span>|<span data-ttu-id="2bc4f-125">描述</span><span class="sxs-lookup"><span data-stu-id="2bc4f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc4f-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="2bc4f-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="2bc4f-127">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="2bc4f-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bc4f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bc4f-128">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2bc4f-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2bc4f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2bc4f-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2bc4f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
