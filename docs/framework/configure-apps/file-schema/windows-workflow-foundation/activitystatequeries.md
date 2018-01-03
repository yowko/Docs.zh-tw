---
title: '&lt;activityStateQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56845a0f596ca83f1abb31e481e38ccc3f808580
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="fbdd2-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="fbdd2-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="fbdd2-103">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="fbdd2-104">比方說，您可能想要追蹤的每一次 「 傳送電子郵件 」 活動完成的工作流程執行個體中。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="fbdd2-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="fbdd2-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="fbdd2-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="fbdd2-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-108">\<system.serviceModel></span></span>  
<span data-ttu-id="fbdd2-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-109">\<tracking></span></span>  
<span data-ttu-id="fbdd2-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-110">\<trackingProfile></span></span>  
<span data-ttu-id="fbdd2-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-111">\<workflow></span></span>  
<span data-ttu-id="fbdd2-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbdd2-113">語法</span><span class="sxs-lookup"><span data-stu-id="fbdd2-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbdd2-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fbdd2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="fbdd2-115">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbdd2-116">屬性</span><span class="sxs-lookup"><span data-stu-id="fbdd2-116">Attributes</span></span>  
 <span data-ttu-id="fbdd2-117">無。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbdd2-118">子元素</span><span class="sxs-lookup"><span data-stu-id="fbdd2-118">Child Elements</span></span>  
  
|<span data-ttu-id="fbdd2-119">項目</span><span class="sxs-lookup"><span data-stu-id="fbdd2-119">Element</span></span>|<span data-ttu-id="fbdd2-120">描述</span><span class="sxs-lookup"><span data-stu-id="fbdd2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbdd2-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="fbdd2-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fbdd2-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbdd2-124">父項目</span><span class="sxs-lookup"><span data-stu-id="fbdd2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fbdd2-125">項目</span><span class="sxs-lookup"><span data-stu-id="fbdd2-125">Element</span></span>|<span data-ttu-id="fbdd2-126">描述</span><span class="sxs-lookup"><span data-stu-id="fbdd2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbdd2-127">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="fbdd2-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fbdd2-128">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="fbdd2-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbdd2-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbdd2-129">See Also</span></span>  
 <span data-ttu-id="fbdd2-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fbdd2-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="fbdd2-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fbdd2-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="fbdd2-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="fbdd2-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="fbdd2-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="fbdd2-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
