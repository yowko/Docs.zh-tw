---
title: "WCF 的 &lt;cancelRequestedQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2af49aab76e82a97aeee92b4799b91011f70c509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="74ae8-102">WCF 的 &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="74ae8-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="74ae8-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="74ae8-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="74ae8-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="74ae8-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="74ae8-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="74ae8-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="74ae8-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="74ae8-106">\<system.serviceModel></span></span>  
<span data-ttu-id="74ae8-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="74ae8-107">\<tracking></span></span>  
<span data-ttu-id="74ae8-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="74ae8-108">\<trackingProfile></span></span>  
<span data-ttu-id="74ae8-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="74ae8-109">\<workflow></span></span>  
<span data-ttu-id="74ae8-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="74ae8-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="74ae8-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="74ae8-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ae8-112">語法</span><span class="sxs-lookup"><span data-stu-id="74ae8-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74ae8-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="74ae8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="74ae8-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="74ae8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74ae8-115">屬性</span><span class="sxs-lookup"><span data-stu-id="74ae8-115">Attributes</span></span>  
  
|<span data-ttu-id="74ae8-116">屬性</span><span class="sxs-lookup"><span data-stu-id="74ae8-116">Attribute</span></span>|<span data-ttu-id="74ae8-117">描述</span><span class="sxs-lookup"><span data-stu-id="74ae8-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74ae8-118">activityName</span><span class="sxs-lookup"><span data-stu-id="74ae8-118">activityName</span></span>|<span data-ttu-id="74ae8-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="74ae8-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="74ae8-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="74ae8-120">childActivityName</span></span>|<span data-ttu-id="74ae8-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="74ae8-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74ae8-122">子元素</span><span class="sxs-lookup"><span data-stu-id="74ae8-122">Child Elements</span></span>  
 <span data-ttu-id="74ae8-123">無。</span><span class="sxs-lookup"><span data-stu-id="74ae8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74ae8-124">父項目</span><span class="sxs-lookup"><span data-stu-id="74ae8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="74ae8-125">項目</span><span class="sxs-lookup"><span data-stu-id="74ae8-125">Element</span></span>|<span data-ttu-id="74ae8-126">描述</span><span class="sxs-lookup"><span data-stu-id="74ae8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74ae8-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="74ae8-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="74ae8-128">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="74ae8-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="74ae8-129">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="74ae8-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74ae8-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="74ae8-130">See Also</span></span>  
 <span data-ttu-id="74ae8-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="74ae8-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="74ae8-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="74ae8-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="74ae8-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="74ae8-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="74ae8-134">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="74ae8-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
