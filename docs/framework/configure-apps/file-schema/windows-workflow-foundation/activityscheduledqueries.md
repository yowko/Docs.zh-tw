---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: a43242e2f22c48a57c11f6f03657d7d3de27ff48
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398985"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="d5414-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="d5414-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="d5414-102">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d5414-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d5414-103">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="d5414-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d5414-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d5414-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d5414-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d5414-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d5414-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d5414-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d5414-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d5414-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d5414-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="d5414-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="d5414-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d5414-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="d5414-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="d5414-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5414-111">語法</span><span class="sxs-lookup"><span data-stu-id="d5414-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5414-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d5414-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d5414-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d5414-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5414-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d5414-114">Attributes</span></span>  
 <span data-ttu-id="d5414-115">無。</span><span class="sxs-lookup"><span data-stu-id="d5414-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d5414-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d5414-116">Child Elements</span></span>  
  
|<span data-ttu-id="d5414-117">項目</span><span class="sxs-lookup"><span data-stu-id="d5414-117">Element</span></span>|<span data-ttu-id="d5414-118">描述</span><span class="sxs-lookup"><span data-stu-id="d5414-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5414-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="d5414-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="d5414-120">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d5414-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5414-121">父項目</span><span class="sxs-lookup"><span data-stu-id="d5414-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d5414-122">項目</span><span class="sxs-lookup"><span data-stu-id="d5414-122">Element</span></span>|<span data-ttu-id="d5414-123">描述</span><span class="sxs-lookup"><span data-stu-id="d5414-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5414-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d5414-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="d5414-125">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="d5414-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5414-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5414-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d5414-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d5414-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d5414-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d5414-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
