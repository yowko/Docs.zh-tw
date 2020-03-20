---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152205"
---
# <a name="customtrackingquery"></a><span data-ttu-id="829dc-101">\<自訂跟蹤查詢></span><span class="sxs-lookup"><span data-stu-id="829dc-101">\<customTrackingQuery></span></span>
<span data-ttu-id="829dc-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="829dc-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="829dc-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="829dc-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="829dc-104">有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="829dc-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="829dc-106">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="829dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="829dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="829dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="829dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<自訂跟蹤查詢>**](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="829dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="829dc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<自訂跟蹤查詢>**</span><span class="sxs-lookup"><span data-stu-id="829dc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829dc-112">語法</span><span class="sxs-lookup"><span data-stu-id="829dc-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="829dc-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="829dc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="829dc-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="829dc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="829dc-115">屬性</span><span class="sxs-lookup"><span data-stu-id="829dc-115">Attributes</span></span>  
  
|<span data-ttu-id="829dc-116">屬性</span><span class="sxs-lookup"><span data-stu-id="829dc-116">Attribute</span></span>|<span data-ttu-id="829dc-117">描述</span><span class="sxs-lookup"><span data-stu-id="829dc-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="829dc-118">activityName</span><span class="sxs-lookup"><span data-stu-id="829dc-118">activityName</span></span>|<span data-ttu-id="829dc-119">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="829dc-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="829dc-120">NAME</span><span class="sxs-lookup"><span data-stu-id="829dc-120">name</span></span>|<span data-ttu-id="829dc-121">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="829dc-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="829dc-122">子元素</span><span class="sxs-lookup"><span data-stu-id="829dc-122">Child Elements</span></span>  
 <span data-ttu-id="829dc-123">無。</span><span class="sxs-lookup"><span data-stu-id="829dc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="829dc-124">父項目</span><span class="sxs-lookup"><span data-stu-id="829dc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="829dc-125">元素</span><span class="sxs-lookup"><span data-stu-id="829dc-125">Element</span></span>|<span data-ttu-id="829dc-126">描述</span><span class="sxs-lookup"><span data-stu-id="829dc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="829dc-127">\<自訂跟蹤查詢></span><span class="sxs-lookup"><span data-stu-id="829dc-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="829dc-128">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="829dc-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="829dc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="829dc-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="829dc-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="829dc-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="829dc-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="829dc-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
