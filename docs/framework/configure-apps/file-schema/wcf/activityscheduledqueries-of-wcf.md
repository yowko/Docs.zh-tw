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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fc263f0d70e7c1016bab819fb157dde6fad66d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="5da23-102">WCF 的 &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="5da23-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="5da23-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="5da23-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="5da23-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="5da23-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="5da23-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5da23-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="5da23-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5da23-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5da23-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="5da23-107">\<tracking></span></span>  
<span data-ttu-id="5da23-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5da23-108">\<trackingProfile></span></span>  
<span data-ttu-id="5da23-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="5da23-109">\<workflow></span></span>  
<span data-ttu-id="5da23-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="5da23-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da23-111">語法</span><span class="sxs-lookup"><span data-stu-id="5da23-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5da23-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5da23-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5da23-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5da23-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5da23-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5da23-114">Attributes</span></span>  
 <span data-ttu-id="5da23-115">無。</span><span class="sxs-lookup"><span data-stu-id="5da23-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5da23-116">子項目</span><span class="sxs-lookup"><span data-stu-id="5da23-116">Child Elements</span></span>  
  
|<span data-ttu-id="5da23-117">項目</span><span class="sxs-lookup"><span data-stu-id="5da23-117">Element</span></span>|<span data-ttu-id="5da23-118">說明</span><span class="sxs-lookup"><span data-stu-id="5da23-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5da23-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="5da23-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="5da23-120">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="5da23-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5da23-121">父項目</span><span class="sxs-lookup"><span data-stu-id="5da23-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5da23-122">項目</span><span class="sxs-lookup"><span data-stu-id="5da23-122">Element</span></span>|<span data-ttu-id="5da23-123">說明</span><span class="sxs-lookup"><span data-stu-id="5da23-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5da23-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="5da23-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5da23-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="5da23-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5da23-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5da23-126">See Also</span></span>  
 <span data-ttu-id="5da23-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="5da23-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="5da23-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="5da23-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="5da23-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="5da23-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5da23-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5da23-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
