---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152127"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="c74b1-101">\<故障傳播查詢></span><span class="sxs-lookup"><span data-stu-id="c74b1-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="c74b1-102">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="c74b1-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c74b1-103">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="c74b1-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c74b1-104">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="c74b1-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c74b1-105">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="c74b1-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c74b1-106">有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="c74b1-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c74b1-107">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c74b1-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c74b1-108">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c74b1-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c74b1-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="c74b1-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="c74b1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="c74b1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="c74b1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c74b1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="c74b1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<故障傳播查詢>**</span><span class="sxs-lookup"><span data-stu-id="c74b1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c74b1-113">語法</span><span class="sxs-lookup"><span data-stu-id="c74b1-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c74b1-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c74b1-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c74b1-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c74b1-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c74b1-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c74b1-116">Attributes</span></span>  
 <span data-ttu-id="c74b1-117">無。</span><span class="sxs-lookup"><span data-stu-id="c74b1-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c74b1-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c74b1-118">Child Elements</span></span>  
  
|<span data-ttu-id="c74b1-119">元素</span><span class="sxs-lookup"><span data-stu-id="c74b1-119">Element</span></span>|<span data-ttu-id="c74b1-120">描述</span><span class="sxs-lookup"><span data-stu-id="c74b1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c74b1-121">\<故障傳播查詢></span><span class="sxs-lookup"><span data-stu-id="c74b1-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="c74b1-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="c74b1-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c74b1-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="c74b1-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c74b1-124">父項目</span><span class="sxs-lookup"><span data-stu-id="c74b1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c74b1-125">元素</span><span class="sxs-lookup"><span data-stu-id="c74b1-125">Element</span></span>|<span data-ttu-id="c74b1-126">描述</span><span class="sxs-lookup"><span data-stu-id="c74b1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c74b1-127">\<工作流></span><span class="sxs-lookup"><span data-stu-id="c74b1-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="c74b1-128">包含**活動定義 Id**屬性標識的特定工作流的所有查詢的配置元素。</span><span class="sxs-lookup"><span data-stu-id="c74b1-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c74b1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c74b1-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c74b1-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c74b1-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c74b1-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c74b1-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
