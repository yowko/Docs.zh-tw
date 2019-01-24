---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 2285dfae84f078483c03d85801051e29b79e74c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561838"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="e6e68-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e6e68-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="e6e68-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="e6e68-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e6e68-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="e6e68-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e6e68-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e6e68-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e6e68-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e6e68-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e6e68-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e6e68-107">\<tracking></span></span>  
<span data-ttu-id="e6e68-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e6e68-108">\<trackingProfile></span></span>  
<span data-ttu-id="e6e68-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e6e68-109">\<workflow></span></span>  
<span data-ttu-id="e6e68-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="e6e68-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e68-111">語法</span><span class="sxs-lookup"><span data-stu-id="e6e68-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6e68-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6e68-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e6e68-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e6e68-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6e68-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e6e68-114">Attributes</span></span>  
 <span data-ttu-id="e6e68-115">無。</span><span class="sxs-lookup"><span data-stu-id="e6e68-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6e68-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e6e68-116">Child Elements</span></span>  
  
|<span data-ttu-id="e6e68-117">項目</span><span class="sxs-lookup"><span data-stu-id="e6e68-117">Element</span></span>|<span data-ttu-id="e6e68-118">描述</span><span class="sxs-lookup"><span data-stu-id="e6e68-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6e68-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e6e68-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="e6e68-120">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="e6e68-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6e68-121">父項目</span><span class="sxs-lookup"><span data-stu-id="e6e68-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e6e68-122">項目</span><span class="sxs-lookup"><span data-stu-id="e6e68-122">Element</span></span>|<span data-ttu-id="e6e68-123">描述</span><span class="sxs-lookup"><span data-stu-id="e6e68-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6e68-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e6e68-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e6e68-125">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="e6e68-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6e68-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6e68-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e6e68-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e6e68-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e6e68-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e6e68-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
