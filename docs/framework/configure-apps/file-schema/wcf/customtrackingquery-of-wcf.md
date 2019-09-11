---
title: <customTrackingQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855428"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="d500a-102">\<WCF 的 customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d500a-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="d500a-103">表示用來追蹤您在程式碼活動中定義之事件的查詢。</span><span class="sxs-lookup"><span data-stu-id="d500a-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="d500a-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d500a-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="d500a-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d500a-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d500a-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d500a-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="d500a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="d500a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="d500a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="d500a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="d500a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d500a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)</span></span>\
<span data-ttu-id="d500a-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="d500a-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d500a-114">語法</span><span class="sxs-lookup"><span data-stu-id="d500a-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d500a-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="d500a-115">Attributes and elements</span></span>  

<span data-ttu-id="d500a-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d500a-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d500a-117">屬性</span><span class="sxs-lookup"><span data-stu-id="d500a-117">Attributes</span></span>  
  
|<span data-ttu-id="d500a-118">屬性</span><span class="sxs-lookup"><span data-stu-id="d500a-118">Attribute</span></span>|<span data-ttu-id="d500a-119">描述</span><span class="sxs-lookup"><span data-stu-id="d500a-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="d500a-120">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="d500a-120">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="d500a-121">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d500a-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d500a-122">子元素</span><span class="sxs-lookup"><span data-stu-id="d500a-122">Child elements</span></span>

<span data-ttu-id="d500a-123">無。</span><span class="sxs-lookup"><span data-stu-id="d500a-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d500a-124">父元素</span><span class="sxs-lookup"><span data-stu-id="d500a-124">Parent elements</span></span>

|<span data-ttu-id="d500a-125">元素</span><span class="sxs-lookup"><span data-stu-id="d500a-125">Element</span></span>|<span data-ttu-id="d500a-126">說明</span><span class="sxs-lookup"><span data-stu-id="d500a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d500a-127">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d500a-127">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="d500a-128">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="d500a-128">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="d500a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d500a-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d500a-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d500a-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d500a-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d500a-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
