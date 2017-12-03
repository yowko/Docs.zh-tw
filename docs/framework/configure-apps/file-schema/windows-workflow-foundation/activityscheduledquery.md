---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32b0e1b068e1f6fef3ce18b0e4dfa628ccaa8a79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="ff6a0-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ff6a0-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="ff6a0-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ff6a0-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="ff6a0-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ff6a0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ff6a0-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ff6a0-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-107">\<tracking></span></span>  
<span data-ttu-id="ff6a0-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-108">\<trackingProfile></span></span>  
<span data-ttu-id="ff6a0-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-109">\<workflow></span></span>  
<span data-ttu-id="ff6a0-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="ff6a0-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6a0-112">語法</span><span class="sxs-lookup"><span data-stu-id="ff6a0-112">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff6a0-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff6a0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ff6a0-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff6a0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ff6a0-115">Attributes</span></span>  
  
|<span data-ttu-id="ff6a0-116">屬性</span><span class="sxs-lookup"><span data-stu-id="ff6a0-116">Attribute</span></span>|<span data-ttu-id="ff6a0-117">描述</span><span class="sxs-lookup"><span data-stu-id="ff6a0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff6a0-118">activityName</span><span class="sxs-lookup"><span data-stu-id="ff6a0-118">activityName</span></span>|<span data-ttu-id="ff6a0-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="ff6a0-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="ff6a0-120">childActivityName</span></span>|<span data-ttu-id="ff6a0-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff6a0-122">子元素</span><span class="sxs-lookup"><span data-stu-id="ff6a0-122">Child Elements</span></span>  
 <span data-ttu-id="ff6a0-123">無。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff6a0-124">父項目</span><span class="sxs-lookup"><span data-stu-id="ff6a0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ff6a0-125">項目</span><span class="sxs-lookup"><span data-stu-id="ff6a0-125">Element</span></span>|<span data-ttu-id="ff6a0-126">說明</span><span class="sxs-lookup"><span data-stu-id="ff6a0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff6a0-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ff6a0-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="ff6a0-128">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="ff6a0-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff6a0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff6a0-129">See Also</span></span>  
 <span data-ttu-id="ff6a0-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ff6a0-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ff6a0-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ff6a0-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ff6a0-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ff6a0-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ff6a0-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ff6a0-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
