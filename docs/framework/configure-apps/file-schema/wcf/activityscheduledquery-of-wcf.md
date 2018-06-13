---
title: WCF 的 &lt;activityScheduledQuery&gt;
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 4efd6ba13e8a54d3338c25b077477d4abdbe9ab5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746234"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="eb97c-102">WCF 的 &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="eb97c-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="eb97c-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="eb97c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="eb97c-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="eb97c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="eb97c-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="eb97c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="eb97c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb97c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="eb97c-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="eb97c-107">\<tracking></span></span>  
<span data-ttu-id="eb97c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eb97c-108">\<trackingProfile></span></span>  
<span data-ttu-id="eb97c-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="eb97c-109">\<workflow></span></span>  
<span data-ttu-id="eb97c-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="eb97c-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="eb97c-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="eb97c-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb97c-112">語法</span><span class="sxs-lookup"><span data-stu-id="eb97c-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb97c-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb97c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="eb97c-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="eb97c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb97c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="eb97c-115">Attributes</span></span>  
  
|<span data-ttu-id="eb97c-116">屬性</span><span class="sxs-lookup"><span data-stu-id="eb97c-116">Attribute</span></span>|<span data-ttu-id="eb97c-117">描述</span><span class="sxs-lookup"><span data-stu-id="eb97c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb97c-118">activityName</span><span class="sxs-lookup"><span data-stu-id="eb97c-118">activityName</span></span>|<span data-ttu-id="eb97c-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="eb97c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="eb97c-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="eb97c-120">childActivityName</span></span>|<span data-ttu-id="eb97c-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="eb97c-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb97c-122">子項目</span><span class="sxs-lookup"><span data-stu-id="eb97c-122">Child Elements</span></span>  
 <span data-ttu-id="eb97c-123">無。</span><span class="sxs-lookup"><span data-stu-id="eb97c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb97c-124">父項目</span><span class="sxs-lookup"><span data-stu-id="eb97c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eb97c-125">項目</span><span class="sxs-lookup"><span data-stu-id="eb97c-125">Element</span></span>|<span data-ttu-id="eb97c-126">描述</span><span class="sxs-lookup"><span data-stu-id="eb97c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb97c-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="eb97c-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="eb97c-128">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="eb97c-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb97c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb97c-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="eb97c-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="eb97c-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="eb97c-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="eb97c-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
