---
title: <cancelRequestedQuery> WCF 的
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: bd6157e63761efa954744ab08ea6c66535def514
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673345"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="a3269-102">\<cancelRequestedQuery > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="a3269-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="a3269-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="a3269-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a3269-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a3269-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="a3269-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a3269-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="a3269-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a3269-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a3269-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="a3269-107">\<tracking></span></span>  
<span data-ttu-id="a3269-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="a3269-108">\<profiles></span></span>  
<span data-ttu-id="a3269-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a3269-109">\<trackingProfile></span></span>  
<span data-ttu-id="a3269-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a3269-110">\<workflow></span></span>  
<span data-ttu-id="a3269-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a3269-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="a3269-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="a3269-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3269-113">語法</span><span class="sxs-lookup"><span data-stu-id="a3269-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3269-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a3269-114">Attributes and elements</span></span>

<span data-ttu-id="a3269-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a3269-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3269-116">屬性</span><span class="sxs-lookup"><span data-stu-id="a3269-116">Attributes</span></span>  
  
|<span data-ttu-id="a3269-117">屬性</span><span class="sxs-lookup"><span data-stu-id="a3269-117">Attribute</span></span>|<span data-ttu-id="a3269-118">描述</span><span class="sxs-lookup"><span data-stu-id="a3269-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="a3269-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="a3269-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="a3269-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="a3269-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3269-121">子元素</span><span class="sxs-lookup"><span data-stu-id="a3269-121">Child elements</span></span>

<span data-ttu-id="a3269-122">無。</span><span class="sxs-lookup"><span data-stu-id="a3269-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="a3269-123">父元素</span><span class="sxs-lookup"><span data-stu-id="a3269-123">Parent elements</span></span>
  
|<span data-ttu-id="a3269-124">元素</span><span class="sxs-lookup"><span data-stu-id="a3269-124">Element</span></span>|<span data-ttu-id="a3269-125">描述</span><span class="sxs-lookup"><span data-stu-id="a3269-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3269-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a3269-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="a3269-127">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="a3269-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3269-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3269-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a3269-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a3269-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a3269-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a3269-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
