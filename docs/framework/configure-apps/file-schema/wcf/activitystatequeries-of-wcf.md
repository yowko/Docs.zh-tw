---
title: "WCF 的 &lt;activityStateQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5261e0769e63513720cc2df185920d424fa1a8f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="5862d-102">WCF 的 &lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="5862d-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="5862d-103">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="5862d-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="5862d-104">比方說，您可能想要追蹤的每一次 「 傳送電子郵件 」 活動完成的工作流程執行個體中。</span><span class="sxs-lookup"><span data-stu-id="5862d-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="5862d-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="5862d-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="5862d-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="5862d-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="5862d-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="5862d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="5862d-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5862d-108">\<system.serviceModel></span></span>  
<span data-ttu-id="5862d-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="5862d-109">\<tracking></span></span>  
<span data-ttu-id="5862d-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5862d-110">\<trackingProfile></span></span>  
<span data-ttu-id="5862d-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="5862d-111">\<workflow></span></span>  
<span data-ttu-id="5862d-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="5862d-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5862d-113">語法</span><span class="sxs-lookup"><span data-stu-id="5862d-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5862d-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5862d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5862d-115">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5862d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5862d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="5862d-116">Attributes</span></span>  
 <span data-ttu-id="5862d-117">無。</span><span class="sxs-lookup"><span data-stu-id="5862d-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5862d-118">子元素</span><span class="sxs-lookup"><span data-stu-id="5862d-118">Child Elements</span></span>  
  
|<span data-ttu-id="5862d-119">項目</span><span class="sxs-lookup"><span data-stu-id="5862d-119">Element</span></span>|<span data-ttu-id="5862d-120">描述</span><span class="sxs-lookup"><span data-stu-id="5862d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5862d-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="5862d-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="5862d-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="5862d-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5862d-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="5862d-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5862d-124">父項目</span><span class="sxs-lookup"><span data-stu-id="5862d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5862d-125">項目</span><span class="sxs-lookup"><span data-stu-id="5862d-125">Element</span></span>|<span data-ttu-id="5862d-126">描述</span><span class="sxs-lookup"><span data-stu-id="5862d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5862d-127">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="5862d-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5862d-128">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="5862d-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5862d-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="5862d-129">See Also</span></span>  
 <span data-ttu-id="5862d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="5862d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="5862d-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5862d-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="5862d-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="5862d-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5862d-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5862d-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
