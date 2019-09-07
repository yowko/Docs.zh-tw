---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 695fccf88ac0d8a672e710ccc632ea58dd2fc693
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398773"
---
# <a name="customtrackingquery"></a><span data-ttu-id="e424d-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="e424d-101">\<customTrackingQuery></span></span>
<span data-ttu-id="e424d-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="e424d-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="e424d-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e424d-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="e424d-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e424d-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e424d-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e424d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e424d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e424d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e424d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="e424d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="e424d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="e424d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e424d-112">語法</span><span class="sxs-lookup"><span data-stu-id="e424d-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e424d-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e424d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e424d-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e424d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e424d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e424d-115">Attributes</span></span>  
  
|<span data-ttu-id="e424d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e424d-116">Attribute</span></span>|<span data-ttu-id="e424d-117">說明</span><span class="sxs-lookup"><span data-stu-id="e424d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e424d-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e424d-118">activityName</span></span>|<span data-ttu-id="e424d-119">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="e424d-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="e424d-120">NAME</span><span class="sxs-lookup"><span data-stu-id="e424d-120">name</span></span>|<span data-ttu-id="e424d-121">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="e424d-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e424d-122">子元素</span><span class="sxs-lookup"><span data-stu-id="e424d-122">Child Elements</span></span>  
 <span data-ttu-id="e424d-123">無。</span><span class="sxs-lookup"><span data-stu-id="e424d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e424d-124">父項目</span><span class="sxs-lookup"><span data-stu-id="e424d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e424d-125">項目</span><span class="sxs-lookup"><span data-stu-id="e424d-125">Element</span></span>|<span data-ttu-id="e424d-126">說明</span><span class="sxs-lookup"><span data-stu-id="e424d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e424d-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="e424d-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="e424d-128">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="e424d-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e424d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e424d-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e424d-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e424d-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e424d-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e424d-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
