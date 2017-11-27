---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a4a58a15db72129f17655e7043f2ee3ae7ffa2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="598ce-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="598ce-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="598ce-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="598ce-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="598ce-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="598ce-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="598ce-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="598ce-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="598ce-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="598ce-106">\<system.serviceModel></span></span>  
<span data-ttu-id="598ce-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="598ce-107">\<tracking></span></span>  
<span data-ttu-id="598ce-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="598ce-108">\<trackingProfile></span></span>  
<span data-ttu-id="598ce-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="598ce-109">\<workflow></span></span>  
<span data-ttu-id="598ce-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="598ce-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="598ce-111">語法</span><span class="sxs-lookup"><span data-stu-id="598ce-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="598ce-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="598ce-112">Attributes and Elements</span></span>  
 <span data-ttu-id="598ce-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="598ce-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="598ce-114">屬性</span><span class="sxs-lookup"><span data-stu-id="598ce-114">Attributes</span></span>  
 <span data-ttu-id="598ce-115">無。</span><span class="sxs-lookup"><span data-stu-id="598ce-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="598ce-116">子項目</span><span class="sxs-lookup"><span data-stu-id="598ce-116">Child Elements</span></span>  
  
|<span data-ttu-id="598ce-117">項目</span><span class="sxs-lookup"><span data-stu-id="598ce-117">Element</span></span>|<span data-ttu-id="598ce-118">說明</span><span class="sxs-lookup"><span data-stu-id="598ce-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="598ce-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="598ce-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="598ce-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="598ce-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="598ce-121">父項目</span><span class="sxs-lookup"><span data-stu-id="598ce-121">Parent Elements</span></span>  
  
|<span data-ttu-id="598ce-122">項目</span><span class="sxs-lookup"><span data-stu-id="598ce-122">Element</span></span>|<span data-ttu-id="598ce-123">說明</span><span class="sxs-lookup"><span data-stu-id="598ce-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="598ce-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="598ce-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="598ce-125">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="598ce-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="598ce-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="598ce-126">See Also</span></span>  
 <span data-ttu-id="598ce-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="598ce-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="598ce-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="598ce-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="598ce-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="598ce-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="598ce-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="598ce-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
