---
title: <activityScheduledQuery> WCF 的
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 5087d56092296f8c68b719ec0945993adeb3de0a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272899"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="1d99c-102">\<activityScheduledQuery > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="1d99c-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="1d99c-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="1d99c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1d99c-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="1d99c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="1d99c-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1d99c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1d99c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d99c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1d99c-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="1d99c-107">\<tracking></span></span>  
<span data-ttu-id="1d99c-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="1d99c-108">\<profiles></span></span>  
<span data-ttu-id="1d99c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1d99c-109">\<trackingProfile></span></span>  
<span data-ttu-id="1d99c-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="1d99c-110">\<workflow></span></span>  
<span data-ttu-id="1d99c-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="1d99c-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="1d99c-112">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="1d99c-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d99c-113">語法</span><span class="sxs-lookup"><span data-stu-id="1d99c-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d99c-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="1d99c-114">Attributes and elements</span></span>  

<span data-ttu-id="1d99c-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1d99c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d99c-116">屬性</span><span class="sxs-lookup"><span data-stu-id="1d99c-116">Attributes</span></span>  
  
|<span data-ttu-id="1d99c-117">屬性</span><span class="sxs-lookup"><span data-stu-id="1d99c-117">Attribute</span></span>|<span data-ttu-id="1d99c-118">描述</span><span class="sxs-lookup"><span data-stu-id="1d99c-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="1d99c-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="1d99c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="1d99c-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="1d99c-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d99c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="1d99c-121">Child elements</span></span>

<span data-ttu-id="1d99c-122">無。</span><span class="sxs-lookup"><span data-stu-id="1d99c-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="1d99c-123">父元素</span><span class="sxs-lookup"><span data-stu-id="1d99c-123">Parent elements</span></span>  
  
|<span data-ttu-id="1d99c-124">元素</span><span class="sxs-lookup"><span data-stu-id="1d99c-124">Element</span></span>|<span data-ttu-id="1d99c-125">描述</span><span class="sxs-lookup"><span data-stu-id="1d99c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d99c-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="1d99c-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="1d99c-127">查詢集合，可用來追蹤由父活動排程執行的活動。</span><span class="sxs-lookup"><span data-stu-id="1d99c-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d99c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d99c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="1d99c-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="1d99c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1d99c-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="1d99c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
