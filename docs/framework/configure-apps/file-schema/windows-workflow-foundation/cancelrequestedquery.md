---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152283"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="9ccc7-101">\<取消請求查詢></span><span class="sxs-lookup"><span data-stu-id="9ccc7-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="9ccc7-102">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9ccc7-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="9ccc7-104">有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9ccc7-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9ccc7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9ccc7-106">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9ccc7-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="9ccc7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="9ccc7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="9ccc7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="9ccc7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="9ccc7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9ccc7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="9ccc7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<取消請求查詢>**](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="9ccc7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="9ccc7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<取消請求查詢>**</span><span class="sxs-lookup"><span data-stu-id="9ccc7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ccc7-112">語法</span><span class="sxs-lookup"><span data-stu-id="9ccc7-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ccc7-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9ccc7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9ccc7-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ccc7-115">屬性</span><span class="sxs-lookup"><span data-stu-id="9ccc7-115">Attributes</span></span>  
  
|<span data-ttu-id="9ccc7-116">屬性</span><span class="sxs-lookup"><span data-stu-id="9ccc7-116">Attribute</span></span>|<span data-ttu-id="9ccc7-117">描述</span><span class="sxs-lookup"><span data-stu-id="9ccc7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ccc7-118">activityName</span><span class="sxs-lookup"><span data-stu-id="9ccc7-118">activityName</span></span>|<span data-ttu-id="9ccc7-119">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="9ccc7-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="9ccc7-120">childActivityName</span></span>|<span data-ttu-id="9ccc7-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ccc7-122">子元素</span><span class="sxs-lookup"><span data-stu-id="9ccc7-122">Child Elements</span></span>  
 <span data-ttu-id="9ccc7-123">無。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ccc7-124">父項目</span><span class="sxs-lookup"><span data-stu-id="9ccc7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9ccc7-125">元素</span><span class="sxs-lookup"><span data-stu-id="9ccc7-125">Element</span></span>|<span data-ttu-id="9ccc7-126">描述</span><span class="sxs-lookup"><span data-stu-id="9ccc7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ccc7-127">\<故障傳播查詢></span><span class="sxs-lookup"><span data-stu-id="9ccc7-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="9ccc7-128">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9ccc7-129">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="9ccc7-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ccc7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ccc7-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ccc7-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9ccc7-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ccc7-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9ccc7-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
