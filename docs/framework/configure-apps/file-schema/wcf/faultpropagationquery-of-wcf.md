---
title: <faultPropagationQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855326"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="38566-102">\<WCF 的 faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="38566-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="38566-103">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="38566-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="38566-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="38566-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="38566-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="38566-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="38566-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="38566-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="38566-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="38566-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="38566-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38566-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38566-109">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="38566-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="38566-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="38566-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="38566-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="38566-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="38566-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="38566-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="38566-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="38566-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="38566-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="38566-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)</span></span>\
<span data-ttu-id="38566-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="38566-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="38566-116">語法</span><span class="sxs-lookup"><span data-stu-id="38566-116">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38566-117">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="38566-117">Attributes and elements</span></span>

<span data-ttu-id="38566-118">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="38566-118">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="38566-119">屬性</span><span class="sxs-lookup"><span data-stu-id="38566-119">Attributes</span></span>

|<span data-ttu-id="38566-120">屬性</span><span class="sxs-lookup"><span data-stu-id="38566-120">Attribute</span></span>|<span data-ttu-id="38566-121">說明</span><span class="sxs-lookup"><span data-stu-id="38566-121">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="38566-122">字串，指定傳播錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="38566-122">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="38566-123">預設值為\*，表示會針對所有活動傳回錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="38566-123">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="38566-124">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="38566-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="38566-125">子元素</span><span class="sxs-lookup"><span data-stu-id="38566-125">Child elements</span></span>

<span data-ttu-id="38566-126">無。</span><span class="sxs-lookup"><span data-stu-id="38566-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38566-127">父元素</span><span class="sxs-lookup"><span data-stu-id="38566-127">Parent elements</span></span>

|<span data-ttu-id="38566-128">元素</span><span class="sxs-lookup"><span data-stu-id="38566-128">Element</span></span>|<span data-ttu-id="38566-129">說明</span><span class="sxs-lookup"><span data-stu-id="38566-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38566-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="38566-130">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="38566-131">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="38566-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="38566-132">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="38566-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="38566-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38566-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="38566-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="38566-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="38566-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="38566-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
