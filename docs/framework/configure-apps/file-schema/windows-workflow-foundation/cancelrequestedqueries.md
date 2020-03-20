---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152303"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="e899e-101">\<取消請求查詢></span><span class="sxs-lookup"><span data-stu-id="e899e-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="e899e-102">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="e899e-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e899e-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="e899e-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="e899e-104">有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e899e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e899e-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e899e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e899e-106">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e899e-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e899e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e899e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e899e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e899e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e899e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e899e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e899e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<取消請求查詢>**</span><span class="sxs-lookup"><span data-stu-id="e899e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e899e-111">語法</span><span class="sxs-lookup"><span data-stu-id="e899e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e899e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e899e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e899e-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e899e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e899e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e899e-114">Attributes</span></span>  
 <span data-ttu-id="e899e-115">無。</span><span class="sxs-lookup"><span data-stu-id="e899e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e899e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e899e-116">Child Elements</span></span>  
  
|<span data-ttu-id="e899e-117">元素</span><span class="sxs-lookup"><span data-stu-id="e899e-117">Element</span></span>|<span data-ttu-id="e899e-118">描述</span><span class="sxs-lookup"><span data-stu-id="e899e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e899e-119">\<取消請求查詢></span><span class="sxs-lookup"><span data-stu-id="e899e-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="e899e-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="e899e-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e899e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="e899e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e899e-122">元素</span><span class="sxs-lookup"><span data-stu-id="e899e-122">Element</span></span>|<span data-ttu-id="e899e-123">描述</span><span class="sxs-lookup"><span data-stu-id="e899e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e899e-124">\<工作流></span><span class="sxs-lookup"><span data-stu-id="e899e-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e899e-125">包含**活動定義 Id**屬性標識的特定工作流的所有查詢的配置元素。</span><span class="sxs-lookup"><span data-stu-id="e899e-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e899e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e899e-126">See also</span></span>

- [<span data-ttu-id="e899e-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e899e-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e899e-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e899e-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
