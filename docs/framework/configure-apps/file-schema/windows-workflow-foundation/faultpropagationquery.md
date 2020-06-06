---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398722"
---
# \<faultPropagationQuery>

<span data-ttu-id="b2168-101">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="b2168-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b2168-102">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="b2168-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b2168-103">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="b2168-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b2168-104">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="b2168-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="b2168-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="b2168-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="b2168-106">語法</span><span class="sxs-lookup"><span data-stu-id="b2168-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b2168-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b2168-107">Attributes and Elements</span></span>

<span data-ttu-id="b2168-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b2168-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2168-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b2168-109">Attributes</span></span>

|<span data-ttu-id="b2168-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b2168-110">Attribute</span></span>|<span data-ttu-id="b2168-111">描述</span><span class="sxs-lookup"><span data-stu-id="b2168-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b2168-112">activityName</span><span class="sxs-lookup"><span data-stu-id="b2168-112">activityName</span></span>|<span data-ttu-id="b2168-113">字串，指定傳播錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2168-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="b2168-114">預設為 \*，表示會針對所有活動傳回錯誤傳用記錄。</span><span class="sxs-lookup"><span data-stu-id="b2168-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="b2168-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="b2168-115">faultHandlerActivityName</span></span>|<span data-ttu-id="b2168-116">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="b2168-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b2168-117">子元素</span><span class="sxs-lookup"><span data-stu-id="b2168-117">Child Elements</span></span>

<span data-ttu-id="b2168-118">無。</span><span class="sxs-lookup"><span data-stu-id="b2168-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2168-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b2168-119">Parent Elements</span></span>

|<span data-ttu-id="b2168-120">元素</span><span class="sxs-lookup"><span data-stu-id="b2168-120">Element</span></span>|<span data-ttu-id="b2168-121">描述</span><span class="sxs-lookup"><span data-stu-id="b2168-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="b2168-122">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="b2168-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b2168-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="b2168-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b2168-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2168-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b2168-125">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b2168-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b2168-126">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b2168-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
