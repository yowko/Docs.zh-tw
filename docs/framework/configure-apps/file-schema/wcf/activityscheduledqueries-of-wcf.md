---
title: WCF 的 &lt;activityScheduledQueries&gt;
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 35bcb0dc0c33d30eee566869579edb32f131f495
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374367"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="2a6c0-102">WCF 的 &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="2a6c0-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="2a6c0-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="2a6c0-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2a6c0-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="2a6c0-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="2a6c0-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2a6c0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2a6c0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2a6c0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2a6c0-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="2a6c0-107">\<tracking></span></span>  
<span data-ttu-id="2a6c0-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="2a6c0-108">\<profiles></span></span>  
<span data-ttu-id="2a6c0-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2a6c0-109">\<trackingProfile></span></span>  
<span data-ttu-id="2a6c0-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="2a6c0-110">\<workflow></span></span>  
<span data-ttu-id="2a6c0-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="2a6c0-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a6c0-112">語法</span><span class="sxs-lookup"><span data-stu-id="2a6c0-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"   
                                  childActivityName="String"/>
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a6c0-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2a6c0-113">Attributes and elements</span></span>  

<span data-ttu-id="2a6c0-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2a6c0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a6c0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="2a6c0-115">Attributes</span></span>  

<span data-ttu-id="2a6c0-116">無。</span><span class="sxs-lookup"><span data-stu-id="2a6c0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2a6c0-117">子元素</span><span class="sxs-lookup"><span data-stu-id="2a6c0-117">Child elements</span></span>  
  
|<span data-ttu-id="2a6c0-118">項目</span><span class="sxs-lookup"><span data-stu-id="2a6c0-118">Element</span></span>|<span data-ttu-id="2a6c0-119">描述</span><span class="sxs-lookup"><span data-stu-id="2a6c0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a6c0-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="2a6c0-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="2a6c0-121">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="2a6c0-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a6c0-122">父元素</span><span class="sxs-lookup"><span data-stu-id="2a6c0-122">Parent elements</span></span>  
  
|<span data-ttu-id="2a6c0-123">元素</span><span class="sxs-lookup"><span data-stu-id="2a6c0-123">Element</span></span>|<span data-ttu-id="2a6c0-124">描述</span><span class="sxs-lookup"><span data-stu-id="2a6c0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a6c0-125">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="2a6c0-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="2a6c0-126">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="2a6c0-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a6c0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a6c0-127">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="2a6c0-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2a6c0-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2a6c0-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2a6c0-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
