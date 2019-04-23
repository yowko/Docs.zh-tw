---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 7217fb886cc96e1ad19f96e2c6542277cfc7979e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175756"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="2beac-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="2beac-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="2beac-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="2beac-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2beac-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="2beac-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="2beac-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2beac-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2beac-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2beac-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2beac-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="2beac-106">\<tracking></span></span>  
<span data-ttu-id="2beac-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2beac-107">\<trackingProfile></span></span>  
<span data-ttu-id="2beac-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="2beac-108">\<workflow></span></span>  
<span data-ttu-id="2beac-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="2beac-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2beac-110">語法</span><span class="sxs-lookup"><span data-stu-id="2beac-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2beac-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2beac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2beac-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2beac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2beac-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2beac-113">Attributes</span></span>  
 <span data-ttu-id="2beac-114">無。</span><span class="sxs-lookup"><span data-stu-id="2beac-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2beac-115">子元素</span><span class="sxs-lookup"><span data-stu-id="2beac-115">Child Elements</span></span>  
  
|<span data-ttu-id="2beac-116">項目</span><span class="sxs-lookup"><span data-stu-id="2beac-116">Element</span></span>|<span data-ttu-id="2beac-117">描述</span><span class="sxs-lookup"><span data-stu-id="2beac-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2beac-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="2beac-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="2beac-119">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="2beac-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2beac-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2beac-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2beac-121">項目</span><span class="sxs-lookup"><span data-stu-id="2beac-121">Element</span></span>|<span data-ttu-id="2beac-122">描述</span><span class="sxs-lookup"><span data-stu-id="2beac-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2beac-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="2beac-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="2beac-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="2beac-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2beac-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2beac-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2beac-126">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2beac-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2beac-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2beac-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
