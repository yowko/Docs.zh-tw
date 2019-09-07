---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: ed08f5533cd6b3839775d061452cb17110cc627e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398896"
---
# <a name="argument"></a><span data-ttu-id="e7624-101">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e7624-101">\<argument></span></span>
<span data-ttu-id="e7624-102">表示與活動狀態查詢相關聯之引數的組態項目。</span><span class="sxs-lookup"><span data-stu-id="e7624-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="e7624-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e7624-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e7624-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7624-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e7624-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e7624-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e7624-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e7624-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Q s >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="e7624-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="e7624-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<引數 >** ](arguments.md)</span><span class="sxs-lookup"><span data-stu-id="e7624-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)</span></span>\
<span data-ttu-id="e7624-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<引數 >**</span><span class="sxs-lookup"><span data-stu-id="e7624-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7624-113">語法</span><span class="sxs-lookup"><span data-stu-id="e7624-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7624-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7624-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e7624-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e7624-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7624-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e7624-116">Attributes</span></span>  
  
|<span data-ttu-id="e7624-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e7624-117">Attribute</span></span>|<span data-ttu-id="e7624-118">描述</span><span class="sxs-lookup"><span data-stu-id="e7624-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7624-119">NAME</span><span class="sxs-lookup"><span data-stu-id="e7624-119">name</span></span>|<span data-ttu-id="e7624-120">指定引數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e7624-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7624-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e7624-121">Child Elements</span></span>  
 <span data-ttu-id="e7624-122">無。</span><span class="sxs-lookup"><span data-stu-id="e7624-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7624-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e7624-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e7624-124">項目</span><span class="sxs-lookup"><span data-stu-id="e7624-124">Element</span></span>|<span data-ttu-id="e7624-125">描述</span><span class="sxs-lookup"><span data-stu-id="e7624-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7624-126">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e7624-126">\<arguments></span></span>](arguments.md)|<span data-ttu-id="e7624-127">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="e7624-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7624-128">備註</span><span class="sxs-lookup"><span data-stu-id="e7624-128">Remarks</span></span>  
 <span data-ttu-id="e7624-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e7624-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e7624-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="e7624-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e7624-131">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素，從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="e7624-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e7624-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="e7624-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e7624-133">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="e7624-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7624-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7624-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e7624-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e7624-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7624-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e7624-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
