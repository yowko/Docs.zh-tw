---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 049ca79355f13fd4ffacedbb7501d760361f0a81
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282018"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="eeb35-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="eeb35-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="eeb35-102">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="eeb35-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="eeb35-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="eeb35-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="eeb35-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="eeb35-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="eeb35-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eeb35-105">\<system.serviceModel></span></span>  
<span data-ttu-id="eeb35-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="eeb35-106">\<tracking></span></span>  
<span data-ttu-id="eeb35-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eeb35-107">\<trackingProfile></span></span>  
<span data-ttu-id="eeb35-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="eeb35-108">\<workflow></span></span>  
<span data-ttu-id="eeb35-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="eeb35-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="eeb35-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="eeb35-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeb35-111">語法</span><span class="sxs-lookup"><span data-stu-id="eeb35-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eeb35-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eeb35-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eeb35-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="eeb35-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eeb35-114">屬性</span><span class="sxs-lookup"><span data-stu-id="eeb35-114">Attributes</span></span>  
  
|<span data-ttu-id="eeb35-115">屬性</span><span class="sxs-lookup"><span data-stu-id="eeb35-115">Attribute</span></span>|<span data-ttu-id="eeb35-116">描述</span><span class="sxs-lookup"><span data-stu-id="eeb35-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eeb35-117">activityName</span><span class="sxs-lookup"><span data-stu-id="eeb35-117">activityName</span></span>|<span data-ttu-id="eeb35-118">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="eeb35-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="eeb35-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="eeb35-119">childActivityName</span></span>|<span data-ttu-id="eeb35-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="eeb35-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eeb35-121">子元素</span><span class="sxs-lookup"><span data-stu-id="eeb35-121">Child Elements</span></span>  
 <span data-ttu-id="eeb35-122">無。</span><span class="sxs-lookup"><span data-stu-id="eeb35-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eeb35-123">父項目</span><span class="sxs-lookup"><span data-stu-id="eeb35-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eeb35-124">項目</span><span class="sxs-lookup"><span data-stu-id="eeb35-124">Element</span></span>|<span data-ttu-id="eeb35-125">描述</span><span class="sxs-lookup"><span data-stu-id="eeb35-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eeb35-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="eeb35-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="eeb35-127">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="eeb35-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="eeb35-128">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="eeb35-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eeb35-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eeb35-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="eeb35-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="eeb35-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="eeb35-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="eeb35-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
