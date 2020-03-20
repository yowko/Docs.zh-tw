---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152420"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="65f83-101">\<活動 計畫查詢></span><span class="sxs-lookup"><span data-stu-id="65f83-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="65f83-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="65f83-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="65f83-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="65f83-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="65f83-104">有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="65f83-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="65f83-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65f83-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="65f83-106">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="65f83-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="65f83-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="65f83-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="65f83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="65f83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="65f83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="65f83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="65f83-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<活動 計畫查詢>**</span><span class="sxs-lookup"><span data-stu-id="65f83-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f83-111">語法</span><span class="sxs-lookup"><span data-stu-id="65f83-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65f83-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="65f83-112">Attributes and Elements</span></span>  
 <span data-ttu-id="65f83-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="65f83-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65f83-114">屬性</span><span class="sxs-lookup"><span data-stu-id="65f83-114">Attributes</span></span>  
 <span data-ttu-id="65f83-115">無。</span><span class="sxs-lookup"><span data-stu-id="65f83-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65f83-116">子元素</span><span class="sxs-lookup"><span data-stu-id="65f83-116">Child Elements</span></span>  
  
|<span data-ttu-id="65f83-117">元素</span><span class="sxs-lookup"><span data-stu-id="65f83-117">Element</span></span>|<span data-ttu-id="65f83-118">描述</span><span class="sxs-lookup"><span data-stu-id="65f83-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65f83-119">\<活動計劃查詢></span><span class="sxs-lookup"><span data-stu-id="65f83-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="65f83-120">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="65f83-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65f83-121">父項目</span><span class="sxs-lookup"><span data-stu-id="65f83-121">Parent Elements</span></span>  
  
|<span data-ttu-id="65f83-122">元素</span><span class="sxs-lookup"><span data-stu-id="65f83-122">Element</span></span>|<span data-ttu-id="65f83-123">描述</span><span class="sxs-lookup"><span data-stu-id="65f83-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65f83-124">\<工作流></span><span class="sxs-lookup"><span data-stu-id="65f83-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="65f83-125">包含**活動定義 Id**屬性標識的特定工作流的所有查詢的配置元素。</span><span class="sxs-lookup"><span data-stu-id="65f83-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65f83-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f83-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="65f83-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="65f83-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="65f83-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="65f83-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
