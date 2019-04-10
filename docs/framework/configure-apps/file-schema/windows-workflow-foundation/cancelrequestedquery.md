---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5f2e46d5e4cdd64c37219476790b9ff92c606b6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215309"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="03355-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="03355-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="03355-102">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="03355-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="03355-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="03355-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="03355-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="03355-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="03355-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="03355-105">\<system.serviceModel></span></span>  
<span data-ttu-id="03355-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="03355-106">\<tracking></span></span>  
<span data-ttu-id="03355-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="03355-107">\<trackingProfile></span></span>  
<span data-ttu-id="03355-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="03355-108">\<workflow></span></span>  
<span data-ttu-id="03355-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="03355-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="03355-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="03355-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03355-111">語法</span><span class="sxs-lookup"><span data-stu-id="03355-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03355-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03355-112">Attributes and Elements</span></span>  
 <span data-ttu-id="03355-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="03355-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03355-114">屬性</span><span class="sxs-lookup"><span data-stu-id="03355-114">Attributes</span></span>  
  
|<span data-ttu-id="03355-115">屬性</span><span class="sxs-lookup"><span data-stu-id="03355-115">Attribute</span></span>|<span data-ttu-id="03355-116">描述</span><span class="sxs-lookup"><span data-stu-id="03355-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03355-117">activityName</span><span class="sxs-lookup"><span data-stu-id="03355-117">activityName</span></span>|<span data-ttu-id="03355-118">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="03355-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="03355-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="03355-119">childActivityName</span></span>|<span data-ttu-id="03355-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="03355-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03355-121">子元素</span><span class="sxs-lookup"><span data-stu-id="03355-121">Child Elements</span></span>  
 <span data-ttu-id="03355-122">無。</span><span class="sxs-lookup"><span data-stu-id="03355-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03355-123">父項目</span><span class="sxs-lookup"><span data-stu-id="03355-123">Parent Elements</span></span>  
  
|<span data-ttu-id="03355-124">項目</span><span class="sxs-lookup"><span data-stu-id="03355-124">Element</span></span>|<span data-ttu-id="03355-125">描述</span><span class="sxs-lookup"><span data-stu-id="03355-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03355-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="03355-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="03355-127">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="03355-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="03355-128">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="03355-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03355-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03355-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="03355-130">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="03355-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="03355-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="03355-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
