---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: aa6ee435c66303b5089b459ecc4ed3023297636d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398962"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="84bfc-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="84bfc-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="84bfc-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="84bfc-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="84bfc-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="84bfc-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="84bfc-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="84bfc-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84bfc-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="84bfc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="84bfc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="84bfc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="84bfc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="84bfc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="84bfc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="84bfc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84bfc-112">語法</span><span class="sxs-lookup"><span data-stu-id="84bfc-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84bfc-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="84bfc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="84bfc-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84bfc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84bfc-115">屬性</span><span class="sxs-lookup"><span data-stu-id="84bfc-115">Attributes</span></span>  
  
|<span data-ttu-id="84bfc-116">屬性</span><span class="sxs-lookup"><span data-stu-id="84bfc-116">Attribute</span></span>|<span data-ttu-id="84bfc-117">描述</span><span class="sxs-lookup"><span data-stu-id="84bfc-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84bfc-118">activityName</span><span class="sxs-lookup"><span data-stu-id="84bfc-118">activityName</span></span>|<span data-ttu-id="84bfc-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="84bfc-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="84bfc-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="84bfc-120">childActivityName</span></span>|<span data-ttu-id="84bfc-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="84bfc-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84bfc-122">子元素</span><span class="sxs-lookup"><span data-stu-id="84bfc-122">Child Elements</span></span>  
 <span data-ttu-id="84bfc-123">無。</span><span class="sxs-lookup"><span data-stu-id="84bfc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84bfc-124">父項目</span><span class="sxs-lookup"><span data-stu-id="84bfc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="84bfc-125">項目</span><span class="sxs-lookup"><span data-stu-id="84bfc-125">Element</span></span>|<span data-ttu-id="84bfc-126">說明</span><span class="sxs-lookup"><span data-stu-id="84bfc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84bfc-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="84bfc-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="84bfc-128">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="84bfc-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84bfc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84bfc-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="84bfc-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="84bfc-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="84bfc-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="84bfc-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
