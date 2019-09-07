---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398917"
---
# <a name="arguments"></a><span data-ttu-id="e3b2b-101">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e3b2b-101">\<arguments></span></span>
<span data-ttu-id="e3b2b-102">表示與某個活動狀態查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="e3b2b-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e3b2b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3b2b-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e3b2b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e3b2b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e3b2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e3b2b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Q s >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="e3b2b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="e3b2b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="e3b2b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<引數 >**</span><span class="sxs-lookup"><span data-stu-id="e3b2b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b2b-112">語法</span><span class="sxs-lookup"><span data-stu-id="e3b2b-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3b2b-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e3b2b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e3b2b-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3b2b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e3b2b-115">Attributes</span></span>  
 <span data-ttu-id="e3b2b-116">無。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3b2b-117">子元素</span><span class="sxs-lookup"><span data-stu-id="e3b2b-117">Child Elements</span></span>  
  
|<span data-ttu-id="e3b2b-118">項目</span><span class="sxs-lookup"><span data-stu-id="e3b2b-118">Element</span></span>|<span data-ttu-id="e3b2b-119">描述</span><span class="sxs-lookup"><span data-stu-id="e3b2b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3b2b-120">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e3b2b-120">\<argument></span></span>](argument.md)|<span data-ttu-id="e3b2b-121">與活動狀態查詢相關聯的引數。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3b2b-122">父項目</span><span class="sxs-lookup"><span data-stu-id="e3b2b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e3b2b-123">項目</span><span class="sxs-lookup"><span data-stu-id="e3b2b-123">Element</span></span>|<span data-ttu-id="e3b2b-124">描述</span><span class="sxs-lookup"><span data-stu-id="e3b2b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3b2b-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="e3b2b-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="e3b2b-126">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e3b2b-127">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3b2b-128">備註</span><span class="sxs-lookup"><span data-stu-id="e3b2b-128">Remarks</span></span>  
 <span data-ttu-id="e3b2b-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e3b2b-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e3b2b-131">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素，從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e3b2b-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e3b2b-133">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="e3b2b-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3b2b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3b2b-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e3b2b-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e3b2b-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e3b2b-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e3b2b-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
