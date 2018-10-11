---
title: WCF 的 &lt;activityScheduledQuery&gt;
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 9a53d72316dad0178f24e05656a4fb4531b88aec
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087761"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="d0712-102">WCF 的 &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="d0712-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="d0712-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d0712-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d0712-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="d0712-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d0712-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d0712-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d0712-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0712-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d0712-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d0712-107">\<tracking></span></span>  
<span data-ttu-id="d0712-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d0712-108">\<trackingProfile></span></span>  
<span data-ttu-id="d0712-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d0712-109">\<workflow></span></span>  
<span data-ttu-id="d0712-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="d0712-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="d0712-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="d0712-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0712-112">語法</span><span class="sxs-lookup"><span data-stu-id="d0712-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0712-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0712-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d0712-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d0712-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0712-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d0712-115">Attributes</span></span>  
  
|<span data-ttu-id="d0712-116">屬性</span><span class="sxs-lookup"><span data-stu-id="d0712-116">Attribute</span></span>|<span data-ttu-id="d0712-117">描述</span><span class="sxs-lookup"><span data-stu-id="d0712-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0712-118">activityName</span><span class="sxs-lookup"><span data-stu-id="d0712-118">activityName</span></span>|<span data-ttu-id="d0712-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="d0712-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="d0712-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="d0712-120">childActivityName</span></span>|<span data-ttu-id="d0712-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="d0712-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0712-122">子元素</span><span class="sxs-lookup"><span data-stu-id="d0712-122">Child Elements</span></span>  
 <span data-ttu-id="d0712-123">無。</span><span class="sxs-lookup"><span data-stu-id="d0712-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0712-124">父項目</span><span class="sxs-lookup"><span data-stu-id="d0712-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d0712-125">項目</span><span class="sxs-lookup"><span data-stu-id="d0712-125">Element</span></span>|<span data-ttu-id="d0712-126">描述</span><span class="sxs-lookup"><span data-stu-id="d0712-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0712-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="d0712-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="d0712-128">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d0712-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0712-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0712-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="d0712-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d0712-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d0712-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d0712-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
