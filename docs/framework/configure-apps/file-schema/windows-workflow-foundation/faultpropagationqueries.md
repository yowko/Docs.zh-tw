---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: bc0cc5fd027da45994269b149b72496fa03becef
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398738"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="778ac-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="778ac-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="778ac-102">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="778ac-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="778ac-103">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="778ac-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="778ac-104">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="778ac-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="778ac-105">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="778ac-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="778ac-106">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="778ac-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="778ac-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="778ac-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="778ac-108">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="778ac-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="778ac-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="778ac-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="778ac-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="778ac-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="778ac-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="778ac-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="778ac-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="778ac-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="778ac-113">語法</span><span class="sxs-lookup"><span data-stu-id="778ac-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="778ac-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="778ac-114">Attributes and Elements</span></span>  
 <span data-ttu-id="778ac-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="778ac-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="778ac-116">屬性</span><span class="sxs-lookup"><span data-stu-id="778ac-116">Attributes</span></span>  
 <span data-ttu-id="778ac-117">無。</span><span class="sxs-lookup"><span data-stu-id="778ac-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="778ac-118">子元素</span><span class="sxs-lookup"><span data-stu-id="778ac-118">Child Elements</span></span>  
  
|<span data-ttu-id="778ac-119">項目</span><span class="sxs-lookup"><span data-stu-id="778ac-119">Element</span></span>|<span data-ttu-id="778ac-120">描述</span><span class="sxs-lookup"><span data-stu-id="778ac-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="778ac-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="778ac-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="778ac-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="778ac-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="778ac-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="778ac-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="778ac-124">父項目</span><span class="sxs-lookup"><span data-stu-id="778ac-124">Parent Elements</span></span>  
  
|<span data-ttu-id="778ac-125">項目</span><span class="sxs-lookup"><span data-stu-id="778ac-125">Element</span></span>|<span data-ttu-id="778ac-126">描述</span><span class="sxs-lookup"><span data-stu-id="778ac-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="778ac-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="778ac-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="778ac-128">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="778ac-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="778ac-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="778ac-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="778ac-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="778ac-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="778ac-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="778ac-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
