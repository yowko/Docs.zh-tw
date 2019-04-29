---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 7217fb886cc96e1ad19f96e2c6542277cfc7979e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790425"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="a8ee8-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="a8ee8-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="a8ee8-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a8ee8-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a8ee8-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8ee8-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="a8ee8-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a8ee8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a8ee8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a8ee8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a8ee8-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="a8ee8-106">\<tracking></span></span>  
<span data-ttu-id="a8ee8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a8ee8-107">\<trackingProfile></span></span>  
<span data-ttu-id="a8ee8-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a8ee8-108">\<workflow></span></span>  
<span data-ttu-id="a8ee8-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="a8ee8-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ee8-110">語法</span><span class="sxs-lookup"><span data-stu-id="a8ee8-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8ee8-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8ee8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a8ee8-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a8ee8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8ee8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a8ee8-113">Attributes</span></span>  
 <span data-ttu-id="a8ee8-114">無。</span><span class="sxs-lookup"><span data-stu-id="a8ee8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8ee8-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a8ee8-115">Child Elements</span></span>  
  
|<span data-ttu-id="a8ee8-116">項目</span><span class="sxs-lookup"><span data-stu-id="a8ee8-116">Element</span></span>|<span data-ttu-id="a8ee8-117">描述</span><span class="sxs-lookup"><span data-stu-id="a8ee8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8ee8-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="a8ee8-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="a8ee8-119">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a8ee8-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8ee8-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a8ee8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a8ee8-121">項目</span><span class="sxs-lookup"><span data-stu-id="a8ee8-121">Element</span></span>|<span data-ttu-id="a8ee8-122">描述</span><span class="sxs-lookup"><span data-stu-id="a8ee8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8ee8-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a8ee8-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a8ee8-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="a8ee8-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8ee8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ee8-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a8ee8-126">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a8ee8-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a8ee8-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a8ee8-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
