---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5de459717fdc0dbf946f12dceda18dce79ca4b06
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398808"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="0ddfc-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="0ddfc-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="0ddfc-102">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0ddfc-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="0ddfc-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0ddfc-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ddfc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ddfc-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0ddfc-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0ddfc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="0ddfc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="0ddfc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="0ddfc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="0ddfc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0ddfc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="0ddfc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="0ddfc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="0ddfc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="0ddfc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ddfc-112">語法</span><span class="sxs-lookup"><span data-stu-id="0ddfc-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ddfc-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0ddfc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0ddfc-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ddfc-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0ddfc-115">Attributes</span></span>  
  
|<span data-ttu-id="0ddfc-116">屬性</span><span class="sxs-lookup"><span data-stu-id="0ddfc-116">Attribute</span></span>|<span data-ttu-id="0ddfc-117">說明</span><span class="sxs-lookup"><span data-stu-id="0ddfc-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ddfc-118">activityName</span><span class="sxs-lookup"><span data-stu-id="0ddfc-118">activityName</span></span>|<span data-ttu-id="0ddfc-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="0ddfc-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="0ddfc-120">childActivityName</span></span>|<span data-ttu-id="0ddfc-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ddfc-122">子元素</span><span class="sxs-lookup"><span data-stu-id="0ddfc-122">Child Elements</span></span>  
 <span data-ttu-id="0ddfc-123">無。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ddfc-124">父項目</span><span class="sxs-lookup"><span data-stu-id="0ddfc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0ddfc-125">項目</span><span class="sxs-lookup"><span data-stu-id="0ddfc-125">Element</span></span>|<span data-ttu-id="0ddfc-126">描述</span><span class="sxs-lookup"><span data-stu-id="0ddfc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ddfc-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="0ddfc-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="0ddfc-128">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0ddfc-129">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="0ddfc-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ddfc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ddfc-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0ddfc-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="0ddfc-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0ddfc-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0ddfc-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
