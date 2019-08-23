---
title: <activityScheduledQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 7787ada68210ff832ff3fd1ec93c9d346e4d2eaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926932"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="efc98-102">\<WCF 的 activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="efc98-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="efc98-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="efc98-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="efc98-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="efc98-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="efc98-105">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="efc98-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="efc98-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="efc98-106">\<system.serviceModel></span></span>  
<span data-ttu-id="efc98-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="efc98-107">\<tracking></span></span>  
<span data-ttu-id="efc98-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="efc98-108">\<profiles></span></span>  
<span data-ttu-id="efc98-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="efc98-109">\<trackingProfile></span></span>  
<span data-ttu-id="efc98-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="efc98-110">\<workflow></span></span>  
<span data-ttu-id="efc98-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="efc98-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="efc98-112">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="efc98-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc98-113">語法</span><span class="sxs-lookup"><span data-stu-id="efc98-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efc98-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="efc98-114">Attributes and elements</span></span>  

<span data-ttu-id="efc98-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="efc98-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efc98-116">屬性</span><span class="sxs-lookup"><span data-stu-id="efc98-116">Attributes</span></span>  
  
|<span data-ttu-id="efc98-117">屬性</span><span class="sxs-lookup"><span data-stu-id="efc98-117">Attribute</span></span>|<span data-ttu-id="efc98-118">描述</span><span class="sxs-lookup"><span data-stu-id="efc98-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="efc98-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="efc98-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="efc98-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="efc98-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efc98-121">子元素</span><span class="sxs-lookup"><span data-stu-id="efc98-121">Child elements</span></span>

<span data-ttu-id="efc98-122">無。</span><span class="sxs-lookup"><span data-stu-id="efc98-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="efc98-123">父元素</span><span class="sxs-lookup"><span data-stu-id="efc98-123">Parent elements</span></span>  
  
|<span data-ttu-id="efc98-124">元素</span><span class="sxs-lookup"><span data-stu-id="efc98-124">Element</span></span>|<span data-ttu-id="efc98-125">描述</span><span class="sxs-lookup"><span data-stu-id="efc98-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efc98-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="efc98-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="efc98-127">查詢的集合, 用來追蹤由父活動排程執行的活動。</span><span class="sxs-lookup"><span data-stu-id="efc98-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efc98-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efc98-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="efc98-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="efc98-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="efc98-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="efc98-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
