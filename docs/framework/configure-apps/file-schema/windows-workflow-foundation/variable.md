---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397771"
---
# <a name="variable"></a><span data-ttu-id="7657e-101">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="7657e-101">\<variable></span></span>
<span data-ttu-id="7657e-102">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="7657e-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="7657e-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="7657e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7657e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7657e-105">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7657e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7657e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7657e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7657e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Q s >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="7657e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="7657e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<變數 >** ](variables.md)</span><span class="sxs-lookup"><span data-stu-id="7657e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)</span></span>\
<span data-ttu-id="7657e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<變數 >**</span><span class="sxs-lookup"><span data-stu-id="7657e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7657e-113">語法</span><span class="sxs-lookup"><span data-stu-id="7657e-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7657e-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7657e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="7657e-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7657e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7657e-116">屬性</span><span class="sxs-lookup"><span data-stu-id="7657e-116">Attributes</span></span>  
  
|<span data-ttu-id="7657e-117">屬性</span><span class="sxs-lookup"><span data-stu-id="7657e-117">Attribute</span></span>|<span data-ttu-id="7657e-118">描述</span><span class="sxs-lookup"><span data-stu-id="7657e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7657e-119">NAME</span><span class="sxs-lookup"><span data-stu-id="7657e-119">name</span></span>|<span data-ttu-id="7657e-120">指定變數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="7657e-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7657e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7657e-121">Child Elements</span></span>  
 <span data-ttu-id="7657e-122">無。</span><span class="sxs-lookup"><span data-stu-id="7657e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7657e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7657e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7657e-124">項目</span><span class="sxs-lookup"><span data-stu-id="7657e-124">Element</span></span>|<span data-ttu-id="7657e-125">描述</span><span class="sxs-lookup"><span data-stu-id="7657e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7657e-126">\<variable></span><span class="sxs-lookup"><span data-stu-id="7657e-126">\<variable></span></span>](variable.md)|<span data-ttu-id="7657e-127">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="7657e-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7657e-128">備註</span><span class="sxs-lookup"><span data-stu-id="7657e-128">Remarks</span></span>  
 <span data-ttu-id="7657e-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="7657e-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="7657e-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="7657e-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="7657e-131">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素，從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="7657e-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="7657e-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="7657e-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7657e-133">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="7657e-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7657e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7657e-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7657e-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="7657e-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7657e-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="7657e-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
