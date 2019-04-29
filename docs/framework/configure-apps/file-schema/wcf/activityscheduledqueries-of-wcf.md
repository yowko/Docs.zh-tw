---
title: <activityScheduledQueries> WCF 的
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 1c9c292080016d7a2d0014ed07be371c0e247621
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701121"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="05e6f-102">\<activityScheduledQueries > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="05e6f-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="05e6f-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="05e6f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="05e6f-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="05e6f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="05e6f-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="05e6f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="05e6f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="05e6f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="05e6f-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="05e6f-107">\<tracking></span></span>  
<span data-ttu-id="05e6f-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="05e6f-108">\<profiles></span></span>  
<span data-ttu-id="05e6f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="05e6f-109">\<trackingProfile></span></span>  
<span data-ttu-id="05e6f-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="05e6f-110">\<workflow></span></span>  
<span data-ttu-id="05e6f-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="05e6f-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e6f-112">語法</span><span class="sxs-lookup"><span data-stu-id="05e6f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05e6f-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="05e6f-113">Attributes and elements</span></span>  

<span data-ttu-id="05e6f-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="05e6f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05e6f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="05e6f-115">Attributes</span></span>  

<span data-ttu-id="05e6f-116">無。</span><span class="sxs-lookup"><span data-stu-id="05e6f-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05e6f-117">子元素</span><span class="sxs-lookup"><span data-stu-id="05e6f-117">Child elements</span></span>  
  
|<span data-ttu-id="05e6f-118">項目</span><span class="sxs-lookup"><span data-stu-id="05e6f-118">Element</span></span>|<span data-ttu-id="05e6f-119">描述</span><span class="sxs-lookup"><span data-stu-id="05e6f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05e6f-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="05e6f-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="05e6f-121">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="05e6f-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05e6f-122">父元素</span><span class="sxs-lookup"><span data-stu-id="05e6f-122">Parent elements</span></span>  
  
|<span data-ttu-id="05e6f-123">元素</span><span class="sxs-lookup"><span data-stu-id="05e6f-123">Element</span></span>|<span data-ttu-id="05e6f-124">描述</span><span class="sxs-lookup"><span data-stu-id="05e6f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05e6f-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="05e6f-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="05e6f-126">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="05e6f-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05e6f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05e6f-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="05e6f-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="05e6f-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="05e6f-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="05e6f-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
