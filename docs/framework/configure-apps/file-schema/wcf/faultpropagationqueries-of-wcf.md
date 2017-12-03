---
title: "WCF 的 &lt;faultPropagationQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 771908114f4f4e1cc2588e39e7f3d811c336a05a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="c28a2-102">WCF 的 &lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c28a2-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="c28a2-103">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="c28a2-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c28a2-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="c28a2-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c28a2-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="c28a2-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c28a2-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="c28a2-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c28a2-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="c28a2-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="c28a2-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c28a2-108">\<system.serviceModel></span></span>  
<span data-ttu-id="c28a2-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="c28a2-109">\<tracking></span></span>  
<span data-ttu-id="c28a2-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c28a2-110">\<trackingProfile></span></span>  
<span data-ttu-id="c28a2-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c28a2-111">\<workflow></span></span>  
<span data-ttu-id="c28a2-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c28a2-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28a2-113">語法</span><span class="sxs-lookup"><span data-stu-id="c28a2-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c28a2-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c28a2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c28a2-115">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c28a2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c28a2-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c28a2-116">Attributes</span></span>  
 <span data-ttu-id="c28a2-117">無。</span><span class="sxs-lookup"><span data-stu-id="c28a2-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c28a2-118">子項目</span><span class="sxs-lookup"><span data-stu-id="c28a2-118">Child Elements</span></span>  
  
|<span data-ttu-id="c28a2-119">項目</span><span class="sxs-lookup"><span data-stu-id="c28a2-119">Element</span></span>|<span data-ttu-id="c28a2-120">說明</span><span class="sxs-lookup"><span data-stu-id="c28a2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c28a2-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c28a2-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="c28a2-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="c28a2-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c28a2-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="c28a2-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c28a2-124">父項目</span><span class="sxs-lookup"><span data-stu-id="c28a2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c28a2-125">項目</span><span class="sxs-lookup"><span data-stu-id="c28a2-125">Element</span></span>|<span data-ttu-id="c28a2-126">說明</span><span class="sxs-lookup"><span data-stu-id="c28a2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c28a2-127">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c28a2-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c28a2-128">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="c28a2-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c28a2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c28a2-129">See Also</span></span>  
 <span data-ttu-id="c28a2-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c28a2-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c28a2-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c28a2-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="c28a2-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c28a2-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c28a2-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c28a2-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
