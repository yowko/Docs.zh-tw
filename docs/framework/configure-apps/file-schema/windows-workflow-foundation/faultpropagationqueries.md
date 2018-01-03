---
title: '&lt;faultPropagationQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da7cf3a439e365c3ee087ffa1739c96041777e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="ac472-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="ac472-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="ac472-103">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="ac472-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ac472-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="ac472-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ac472-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="ac472-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ac472-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="ac472-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="ac472-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ac472-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ac472-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ac472-108">\<system.serviceModel></span></span>  
<span data-ttu-id="ac472-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="ac472-109">\<tracking></span></span>  
<span data-ttu-id="ac472-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ac472-110">\<trackingProfile></span></span>  
<span data-ttu-id="ac472-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ac472-111">\<workflow></span></span>  
<span data-ttu-id="ac472-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ac472-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac472-113">語法</span><span class="sxs-lookup"><span data-stu-id="ac472-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac472-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ac472-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ac472-115">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ac472-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac472-116">屬性</span><span class="sxs-lookup"><span data-stu-id="ac472-116">Attributes</span></span>  
 <span data-ttu-id="ac472-117">無。</span><span class="sxs-lookup"><span data-stu-id="ac472-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ac472-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ac472-118">Child Elements</span></span>  
  
|<span data-ttu-id="ac472-119">項目</span><span class="sxs-lookup"><span data-stu-id="ac472-119">Element</span></span>|<span data-ttu-id="ac472-120">描述</span><span class="sxs-lookup"><span data-stu-id="ac472-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac472-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="ac472-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="ac472-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="ac472-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ac472-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="ac472-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac472-124">父項目</span><span class="sxs-lookup"><span data-stu-id="ac472-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ac472-125">項目</span><span class="sxs-lookup"><span data-stu-id="ac472-125">Element</span></span>|<span data-ttu-id="ac472-126">描述</span><span class="sxs-lookup"><span data-stu-id="ac472-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac472-127">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ac472-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ac472-128">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="ac472-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac472-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac472-129">See Also</span></span>  
 <span data-ttu-id="ac472-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ac472-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ac472-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ac472-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ac472-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ac472-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ac472-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ac472-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
