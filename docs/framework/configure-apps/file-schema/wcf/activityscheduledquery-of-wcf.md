---
title: "WCF 的 &lt;activityScheduledQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb421993c39e66e437a0ecbb35091532df61716
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="8201e-102">WCF 的 &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="8201e-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="8201e-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="8201e-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="8201e-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="8201e-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="8201e-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8201e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8201e-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8201e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8201e-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="8201e-107">\<tracking></span></span>  
<span data-ttu-id="8201e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8201e-108">\<trackingProfile></span></span>  
<span data-ttu-id="8201e-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="8201e-109">\<workflow></span></span>  
<span data-ttu-id="8201e-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="8201e-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="8201e-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="8201e-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8201e-112">語法</span><span class="sxs-lookup"><span data-stu-id="8201e-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8201e-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8201e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8201e-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8201e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8201e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="8201e-115">Attributes</span></span>  
  
|<span data-ttu-id="8201e-116">屬性</span><span class="sxs-lookup"><span data-stu-id="8201e-116">Attribute</span></span>|<span data-ttu-id="8201e-117">描述</span><span class="sxs-lookup"><span data-stu-id="8201e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8201e-118">activityName</span><span class="sxs-lookup"><span data-stu-id="8201e-118">activityName</span></span>|<span data-ttu-id="8201e-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="8201e-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="8201e-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="8201e-120">childActivityName</span></span>|<span data-ttu-id="8201e-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="8201e-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8201e-122">子元素</span><span class="sxs-lookup"><span data-stu-id="8201e-122">Child Elements</span></span>  
 <span data-ttu-id="8201e-123">無。</span><span class="sxs-lookup"><span data-stu-id="8201e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8201e-124">父項目</span><span class="sxs-lookup"><span data-stu-id="8201e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8201e-125">項目</span><span class="sxs-lookup"><span data-stu-id="8201e-125">Element</span></span>|<span data-ttu-id="8201e-126">描述</span><span class="sxs-lookup"><span data-stu-id="8201e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8201e-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="8201e-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="8201e-128">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="8201e-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8201e-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="8201e-129">See Also</span></span>  
 <span data-ttu-id="8201e-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="8201e-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="8201e-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="8201e-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="8201e-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="8201e-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8201e-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="8201e-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
