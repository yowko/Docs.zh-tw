---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397585"
---
# <a name="variables"></a><span data-ttu-id="58933-101">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="58933-101">\<variables></span></span>
<span data-ttu-id="58933-102">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="58933-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="58933-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="58933-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="58933-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58933-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="58933-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="58933-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="58933-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="58933-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="58933-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="58933-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="58933-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="58933-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="58933-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Q s >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="58933-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="58933-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="58933-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="58933-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<變數 >**</span><span class="sxs-lookup"><span data-stu-id="58933-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58933-112">語法</span><span class="sxs-lookup"><span data-stu-id="58933-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58933-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58933-113">Attributes and Elements</span></span>  
 <span data-ttu-id="58933-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="58933-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58933-115">屬性</span><span class="sxs-lookup"><span data-stu-id="58933-115">Attributes</span></span>  
 <span data-ttu-id="58933-116">無。</span><span class="sxs-lookup"><span data-stu-id="58933-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58933-117">子元素</span><span class="sxs-lookup"><span data-stu-id="58933-117">Child Elements</span></span>  
  
|<span data-ttu-id="58933-118">項目</span><span class="sxs-lookup"><span data-stu-id="58933-118">Element</span></span>|<span data-ttu-id="58933-119">描述</span><span class="sxs-lookup"><span data-stu-id="58933-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58933-120">\<variable></span><span class="sxs-lookup"><span data-stu-id="58933-120">\<variable></span></span>](variable.md)|<span data-ttu-id="58933-121">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="58933-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58933-122">父項目</span><span class="sxs-lookup"><span data-stu-id="58933-122">Parent Elements</span></span>  
  
|<span data-ttu-id="58933-123">項目</span><span class="sxs-lookup"><span data-stu-id="58933-123">Element</span></span>|<span data-ttu-id="58933-124">說明</span><span class="sxs-lookup"><span data-stu-id="58933-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58933-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="58933-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="58933-126">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="58933-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="58933-127">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="58933-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58933-128">備註</span><span class="sxs-lookup"><span data-stu-id="58933-128">Remarks</span></span>  
 <span data-ttu-id="58933-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="58933-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="58933-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="58933-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="58933-131">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素，從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="58933-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="58933-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="58933-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="58933-133">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="58933-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58933-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58933-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="58933-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="58933-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="58933-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="58933-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
