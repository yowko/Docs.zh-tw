---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 2199e66342c6fa3afca9d8ccd3b620560b123ede
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260836"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="c9e5c-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="c9e5c-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="c9e5c-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c9e5c-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="c9e5c-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c9e5c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c9e5c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9e5c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c9e5c-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c9e5c-106">\<tracking></span></span>  
<span data-ttu-id="c9e5c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c9e5c-107">\<trackingProfile></span></span>  
<span data-ttu-id="c9e5c-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c9e5c-108">\<workflow></span></span>  
<span data-ttu-id="c9e5c-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="c9e5c-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="c9e5c-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="c9e5c-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e5c-111">語法</span><span class="sxs-lookup"><span data-stu-id="c9e5c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9e5c-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9e5c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c9e5c-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9e5c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c9e5c-114">Attributes</span></span>  
  
|<span data-ttu-id="c9e5c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c9e5c-115">Attribute</span></span>|<span data-ttu-id="c9e5c-116">描述</span><span class="sxs-lookup"><span data-stu-id="c9e5c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9e5c-117">activityName</span><span class="sxs-lookup"><span data-stu-id="c9e5c-117">activityName</span></span>|<span data-ttu-id="c9e5c-118">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="c9e5c-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="c9e5c-119">childActivityName</span></span>|<span data-ttu-id="c9e5c-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9e5c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c9e5c-121">Child Elements</span></span>  
 <span data-ttu-id="c9e5c-122">無。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9e5c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c9e5c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c9e5c-124">項目</span><span class="sxs-lookup"><span data-stu-id="c9e5c-124">Element</span></span>|<span data-ttu-id="c9e5c-125">描述</span><span class="sxs-lookup"><span data-stu-id="c9e5c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9e5c-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="c9e5c-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="c9e5c-127">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="c9e5c-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9e5c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9e5c-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c9e5c-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c9e5c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c9e5c-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c9e5c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
