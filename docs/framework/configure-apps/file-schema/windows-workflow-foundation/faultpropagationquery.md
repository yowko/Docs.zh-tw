---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f77a613f4eb0456a0085096aa478d37c78122217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946307"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="e76f4-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e76f4-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="e76f4-102">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="e76f4-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e76f4-103">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="e76f4-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e76f4-104">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="e76f4-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e76f4-105">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="e76f4-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="e76f4-106">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e76f4-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="e76f4-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e76f4-107">\<system.serviceModel></span></span>\
<span data-ttu-id="e76f4-108">\<追蹤 > </span><span class="sxs-lookup"><span data-stu-id="e76f4-108">\<tracking></span></span>\
<span data-ttu-id="e76f4-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e76f4-109">\<trackingProfile></span></span>\
<span data-ttu-id="e76f4-110">\<工作流程 > </span><span class="sxs-lookup"><span data-stu-id="e76f4-110">\<workflow></span></span>\
<span data-ttu-id="e76f4-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e76f4-111">\<faultPropagationQueries></span></span>\
<span data-ttu-id="e76f4-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e76f4-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="e76f4-113">語法</span><span class="sxs-lookup"><span data-stu-id="e76f4-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e76f4-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e76f4-114">Attributes and Elements</span></span>

<span data-ttu-id="e76f4-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e76f4-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e76f4-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e76f4-116">Attributes</span></span>

|<span data-ttu-id="e76f4-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e76f4-117">Attribute</span></span>|<span data-ttu-id="e76f4-118">描述</span><span class="sxs-lookup"><span data-stu-id="e76f4-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e76f4-119">activityName</span><span class="sxs-lookup"><span data-stu-id="e76f4-119">activityName</span></span>|<span data-ttu-id="e76f4-120">字串, 指定傳播錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="e76f4-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="e76f4-121">預設為 \*，表示會針對所有活動傳回錯誤傳用記錄。</span><span class="sxs-lookup"><span data-stu-id="e76f4-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="e76f4-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="e76f4-122">faultHandlerActivityName</span></span>|<span data-ttu-id="e76f4-123">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="e76f4-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e76f4-124">子元素</span><span class="sxs-lookup"><span data-stu-id="e76f4-124">Child Elements</span></span>

<span data-ttu-id="e76f4-125">無。</span><span class="sxs-lookup"><span data-stu-id="e76f4-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e76f4-126">父項目</span><span class="sxs-lookup"><span data-stu-id="e76f4-126">Parent Elements</span></span>

|<span data-ttu-id="e76f4-127">項目</span><span class="sxs-lookup"><span data-stu-id="e76f4-127">Element</span></span>|<span data-ttu-id="e76f4-128">描述</span><span class="sxs-lookup"><span data-stu-id="e76f4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e76f4-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e76f4-129">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="e76f4-130">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="e76f4-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e76f4-131">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="e76f4-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e76f4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e76f4-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e76f4-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e76f4-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e76f4-134">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e76f4-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
