---
title: <faultPropagationQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855326"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="a1214-102">\<faultPropagationQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="a1214-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="a1214-103">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="a1214-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a1214-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a1214-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a1214-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a1214-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a1214-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="a1214-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="a1214-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a1214-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="a1214-108">語法</span><span class="sxs-lookup"><span data-stu-id="a1214-108">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a1214-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a1214-109">Attributes and elements</span></span>

<span data-ttu-id="a1214-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a1214-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1214-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a1214-111">Attributes</span></span>

|<span data-ttu-id="a1214-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a1214-112">Attribute</span></span>|<span data-ttu-id="a1214-113">描述</span><span class="sxs-lookup"><span data-stu-id="a1214-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="a1214-114">字串，指定傳播錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1214-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="a1214-115">預設值為 \* ，表示會針對所有活動傳回錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="a1214-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="a1214-116">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="a1214-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a1214-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a1214-117">Child elements</span></span>

<span data-ttu-id="a1214-118">無。</span><span class="sxs-lookup"><span data-stu-id="a1214-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1214-119">父元素</span><span class="sxs-lookup"><span data-stu-id="a1214-119">Parent elements</span></span>

|<span data-ttu-id="a1214-120">元素</span><span class="sxs-lookup"><span data-stu-id="a1214-120">Element</span></span>|<span data-ttu-id="a1214-121">描述</span><span class="sxs-lookup"><span data-stu-id="a1214-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="a1214-122">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="a1214-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a1214-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a1214-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a1214-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1214-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a1214-125">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a1214-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a1214-126">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a1214-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
