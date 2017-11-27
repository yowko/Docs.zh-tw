---
title: "WCF 的 &lt;activityScheduledQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97726c7faa08477351d4496650b6c08b643cdb76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="b68ca-102">WCF 的 &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="b68ca-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="b68ca-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="b68ca-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b68ca-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="b68ca-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="b68ca-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b68ca-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="b68ca-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b68ca-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b68ca-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="b68ca-107">\<tracking></span></span>  
<span data-ttu-id="b68ca-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b68ca-108">\<trackingProfile></span></span>  
<span data-ttu-id="b68ca-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="b68ca-109">\<workflow></span></span>  
<span data-ttu-id="b68ca-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="b68ca-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68ca-111">語法</span><span class="sxs-lookup"><span data-stu-id="b68ca-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b68ca-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b68ca-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b68ca-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b68ca-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b68ca-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b68ca-114">Attributes</span></span>  
 <span data-ttu-id="b68ca-115">無。</span><span class="sxs-lookup"><span data-stu-id="b68ca-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b68ca-116">子項目</span><span class="sxs-lookup"><span data-stu-id="b68ca-116">Child Elements</span></span>  
  
|<span data-ttu-id="b68ca-117">項目</span><span class="sxs-lookup"><span data-stu-id="b68ca-117">Element</span></span>|<span data-ttu-id="b68ca-118">說明</span><span class="sxs-lookup"><span data-stu-id="b68ca-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b68ca-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b68ca-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="b68ca-120">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="b68ca-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b68ca-121">父項目</span><span class="sxs-lookup"><span data-stu-id="b68ca-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b68ca-122">項目</span><span class="sxs-lookup"><span data-stu-id="b68ca-122">Element</span></span>|<span data-ttu-id="b68ca-123">說明</span><span class="sxs-lookup"><span data-stu-id="b68ca-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b68ca-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="b68ca-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b68ca-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="b68ca-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b68ca-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68ca-126">See Also</span></span>  
 <span data-ttu-id="b68ca-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="b68ca-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="b68ca-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="b68ca-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="b68ca-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b68ca-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b68ca-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b68ca-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
