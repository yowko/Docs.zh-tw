---
title: WCF 的 &lt;activityScheduledQuery&gt;
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: fd7830bc178de0693f0632cea3b390d792408ec1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147872"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="cb52c-102">WCF 的 &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="cb52c-102">&lt;activityScheduledQuery&gt; of WCF</span></span>

<span data-ttu-id="cb52c-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="cb52c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cb52c-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="cb52c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="cb52c-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cb52c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cb52c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cb52c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="cb52c-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="cb52c-107">\<tracking></span></span>  
<span data-ttu-id="cb52c-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="cb52c-108">\<profiles></span></span>  
<span data-ttu-id="cb52c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cb52c-109">\<trackingProfile></span></span>  
<span data-ttu-id="cb52c-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="cb52c-110">\<workflow></span></span>  
<span data-ttu-id="cb52c-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="cb52c-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="cb52c-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="cb52c-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb52c-113">語法</span><span class="sxs-lookup"><span data-stu-id="cb52c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb52c-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="cb52c-114">Attributes and elements</span></span>  

<span data-ttu-id="cb52c-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cb52c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb52c-116">屬性</span><span class="sxs-lookup"><span data-stu-id="cb52c-116">Attributes</span></span>  
  
|<span data-ttu-id="cb52c-117">屬性</span><span class="sxs-lookup"><span data-stu-id="cb52c-117">Attribute</span></span>|<span data-ttu-id="cb52c-118">描述</span><span class="sxs-lookup"><span data-stu-id="cb52c-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="cb52c-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="cb52c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="cb52c-120">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="cb52c-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb52c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="cb52c-121">Child elements</span></span>

<span data-ttu-id="cb52c-122">無。</span><span class="sxs-lookup"><span data-stu-id="cb52c-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="cb52c-123">父元素</span><span class="sxs-lookup"><span data-stu-id="cb52c-123">Parent elements</span></span>  
  
|<span data-ttu-id="cb52c-124">元素</span><span class="sxs-lookup"><span data-stu-id="cb52c-124">Element</span></span>|<span data-ttu-id="cb52c-125">描述</span><span class="sxs-lookup"><span data-stu-id="cb52c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb52c-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="cb52c-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="cb52c-127">查詢集合，可用來追蹤由父活動排程執行的活動。</span><span class="sxs-lookup"><span data-stu-id="cb52c-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb52c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb52c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="cb52c-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="cb52c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cb52c-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="cb52c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
