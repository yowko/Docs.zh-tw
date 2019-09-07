---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398722"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="55b79-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="55b79-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="55b79-102">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="55b79-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="55b79-103">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="55b79-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="55b79-104">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="55b79-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="55b79-105">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="55b79-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="55b79-106">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="55b79-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="55b79-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55b79-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55b79-108">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="55b79-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="55b79-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="55b79-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="55b79-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="55b79-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="55b79-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="55b79-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="55b79-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries.md)</span><span class="sxs-lookup"><span data-stu-id="55b79-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)</span></span>\
<span data-ttu-id="55b79-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="55b79-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>

## <a name="syntax"></a><span data-ttu-id="55b79-114">語法</span><span class="sxs-lookup"><span data-stu-id="55b79-114">Syntax</span></span>

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55b79-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="55b79-115">Attributes and Elements</span></span>

<span data-ttu-id="55b79-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="55b79-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="55b79-117">屬性</span><span class="sxs-lookup"><span data-stu-id="55b79-117">Attributes</span></span>

|<span data-ttu-id="55b79-118">屬性</span><span class="sxs-lookup"><span data-stu-id="55b79-118">Attribute</span></span>|<span data-ttu-id="55b79-119">描述</span><span class="sxs-lookup"><span data-stu-id="55b79-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="55b79-120">activityName</span><span class="sxs-lookup"><span data-stu-id="55b79-120">activityName</span></span>|<span data-ttu-id="55b79-121">字串，指定傳播錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="55b79-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="55b79-122">預設為 \*，表示會針對所有活動傳回錯誤傳用記錄。</span><span class="sxs-lookup"><span data-stu-id="55b79-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="55b79-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="55b79-123">faultHandlerActivityName</span></span>|<span data-ttu-id="55b79-124">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="55b79-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="55b79-125">子元素</span><span class="sxs-lookup"><span data-stu-id="55b79-125">Child Elements</span></span>

<span data-ttu-id="55b79-126">無。</span><span class="sxs-lookup"><span data-stu-id="55b79-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55b79-127">父項目</span><span class="sxs-lookup"><span data-stu-id="55b79-127">Parent Elements</span></span>

|<span data-ttu-id="55b79-128">項目</span><span class="sxs-lookup"><span data-stu-id="55b79-128">Element</span></span>|<span data-ttu-id="55b79-129">描述</span><span class="sxs-lookup"><span data-stu-id="55b79-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55b79-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="55b79-130">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="55b79-131">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="55b79-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="55b79-132">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="55b79-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="55b79-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b79-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="55b79-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="55b79-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="55b79-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="55b79-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
