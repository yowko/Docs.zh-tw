---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 89de9ef10449fbae78a8c5b558101a2cf6477b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945527"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="cf94d-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="cf94d-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="cf94d-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="cf94d-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cf94d-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="cf94d-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="cf94d-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cf94d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cf94d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cf94d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cf94d-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="cf94d-106">\<tracking></span></span>  
<span data-ttu-id="cf94d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cf94d-107">\<trackingProfile></span></span>  
<span data-ttu-id="cf94d-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="cf94d-108">\<workflow></span></span>  
<span data-ttu-id="cf94d-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="cf94d-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf94d-110">語法</span><span class="sxs-lookup"><span data-stu-id="cf94d-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf94d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf94d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf94d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cf94d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf94d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cf94d-113">Attributes</span></span>  
 <span data-ttu-id="cf94d-114">無。</span><span class="sxs-lookup"><span data-stu-id="cf94d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf94d-115">子元素</span><span class="sxs-lookup"><span data-stu-id="cf94d-115">Child Elements</span></span>  
  
|<span data-ttu-id="cf94d-116">項目</span><span class="sxs-lookup"><span data-stu-id="cf94d-116">Element</span></span>|<span data-ttu-id="cf94d-117">描述</span><span class="sxs-lookup"><span data-stu-id="cf94d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf94d-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="cf94d-118">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="cf94d-119">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="cf94d-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf94d-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cf94d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cf94d-121">項目</span><span class="sxs-lookup"><span data-stu-id="cf94d-121">Element</span></span>|<span data-ttu-id="cf94d-122">說明</span><span class="sxs-lookup"><span data-stu-id="cf94d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf94d-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cf94d-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cf94d-124">Configuration 元素, 其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="cf94d-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf94d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf94d-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cf94d-126">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="cf94d-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cf94d-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="cf94d-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
