---
title: <states> 的 <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 0c8bf5b793684d3e6076114ce9eda7ffe1ef7a81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398635"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="a87bd-102">\<activityStateQuery > 的\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="a87bd-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="a87bd-103">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="a87bd-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="a87bd-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a87bd-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a87bd-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a87bd-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a87bd-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a87bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="a87bd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="a87bd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Q s >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="a87bd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="a87bd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="a87bd-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<狀態 >**</span><span class="sxs-lookup"><span data-stu-id="a87bd-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87bd-113">語法</span><span class="sxs-lookup"><span data-stu-id="a87bd-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a87bd-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a87bd-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a87bd-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a87bd-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a87bd-116">屬性</span><span class="sxs-lookup"><span data-stu-id="a87bd-116">Attributes</span></span>  
 <span data-ttu-id="a87bd-117">無。</span><span class="sxs-lookup"><span data-stu-id="a87bd-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a87bd-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a87bd-118">Child Elements</span></span>  
  
|<span data-ttu-id="a87bd-119">項目</span><span class="sxs-lookup"><span data-stu-id="a87bd-119">Element</span></span>|<span data-ttu-id="a87bd-120">描述</span><span class="sxs-lookup"><span data-stu-id="a87bd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a87bd-121">\<state></span><span class="sxs-lookup"><span data-stu-id="a87bd-121">\<state></span></span>](state-of-states.md)|<span data-ttu-id="a87bd-122">組態項目，其中包含追蹤記錄應發出之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="a87bd-122">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a87bd-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a87bd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a87bd-124">項目</span><span class="sxs-lookup"><span data-stu-id="a87bd-124">Element</span></span>|<span data-ttu-id="a87bd-125">描述</span><span class="sxs-lookup"><span data-stu-id="a87bd-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a87bd-126">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="a87bd-126">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="a87bd-127">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="a87bd-127">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a87bd-128">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a87bd-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a87bd-129">備註</span><span class="sxs-lookup"><span data-stu-id="a87bd-129">Remarks</span></span>  
 <span data-ttu-id="a87bd-130">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="a87bd-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a87bd-131">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="a87bd-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a87bd-132">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素，從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="a87bd-132">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="a87bd-133">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="a87bd-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a87bd-134">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="a87bd-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a87bd-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87bd-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a87bd-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a87bd-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a87bd-137">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a87bd-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
