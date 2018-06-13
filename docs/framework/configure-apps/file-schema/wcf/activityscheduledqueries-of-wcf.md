---
title: WCF 的 &lt;activityScheduledQueries&gt;
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 946406e5513a0fee6793071c397f61bf1fe71c65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744885"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="a072f-102">WCF 的 &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="a072f-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="a072f-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a072f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a072f-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="a072f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="a072f-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a072f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="a072f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a072f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a072f-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="a072f-107">\<tracking></span></span>  
<span data-ttu-id="a072f-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a072f-108">\<trackingProfile></span></span>  
<span data-ttu-id="a072f-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="a072f-109">\<workflow></span></span>  
<span data-ttu-id="a072f-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="a072f-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a072f-111">語法</span><span class="sxs-lookup"><span data-stu-id="a072f-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a072f-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a072f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a072f-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a072f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a072f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a072f-114">Attributes</span></span>  
 <span data-ttu-id="a072f-115">無。</span><span class="sxs-lookup"><span data-stu-id="a072f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a072f-116">子項目</span><span class="sxs-lookup"><span data-stu-id="a072f-116">Child Elements</span></span>  
  
|<span data-ttu-id="a072f-117">項目</span><span class="sxs-lookup"><span data-stu-id="a072f-117">Element</span></span>|<span data-ttu-id="a072f-118">描述</span><span class="sxs-lookup"><span data-stu-id="a072f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a072f-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="a072f-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="a072f-120">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a072f-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a072f-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a072f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a072f-122">項目</span><span class="sxs-lookup"><span data-stu-id="a072f-122">Element</span></span>|<span data-ttu-id="a072f-123">描述</span><span class="sxs-lookup"><span data-stu-id="a072f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a072f-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="a072f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a072f-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="a072f-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a072f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a072f-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="a072f-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a072f-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a072f-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a072f-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
