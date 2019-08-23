---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: dc04405204be7c5484d47b4a3767f846b11abf9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945507"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="d38f9-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="d38f9-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="d38f9-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d38f9-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d38f9-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="d38f9-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d38f9-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d38f9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d38f9-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d38f9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d38f9-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d38f9-106">\<tracking></span></span>  
<span data-ttu-id="d38f9-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d38f9-107">\<trackingProfile></span></span>  
<span data-ttu-id="d38f9-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d38f9-108">\<workflow></span></span>  
<span data-ttu-id="d38f9-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="d38f9-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="d38f9-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="d38f9-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d38f9-111">語法</span><span class="sxs-lookup"><span data-stu-id="d38f9-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d38f9-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d38f9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d38f9-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d38f9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d38f9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d38f9-114">Attributes</span></span>  
  
|<span data-ttu-id="d38f9-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d38f9-115">Attribute</span></span>|<span data-ttu-id="d38f9-116">說明</span><span class="sxs-lookup"><span data-stu-id="d38f9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d38f9-117">activityName</span><span class="sxs-lookup"><span data-stu-id="d38f9-117">activityName</span></span>|<span data-ttu-id="d38f9-118">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="d38f9-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="d38f9-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="d38f9-119">childActivityName</span></span>|<span data-ttu-id="d38f9-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="d38f9-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d38f9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="d38f9-121">Child Elements</span></span>  
 <span data-ttu-id="d38f9-122">無。</span><span class="sxs-lookup"><span data-stu-id="d38f9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d38f9-123">父項目</span><span class="sxs-lookup"><span data-stu-id="d38f9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d38f9-124">項目</span><span class="sxs-lookup"><span data-stu-id="d38f9-124">Element</span></span>|<span data-ttu-id="d38f9-125">描述</span><span class="sxs-lookup"><span data-stu-id="d38f9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d38f9-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="d38f9-126">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="d38f9-127">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d38f9-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d38f9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d38f9-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d38f9-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d38f9-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d38f9-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d38f9-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
