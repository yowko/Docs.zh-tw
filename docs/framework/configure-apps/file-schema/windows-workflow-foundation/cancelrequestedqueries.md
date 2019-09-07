---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 0d08612ce5d74f4f7f505c538187ddecea610132
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398818"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="ca183-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ca183-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="ca183-102">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="ca183-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ca183-103">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="ca183-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="ca183-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ca183-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ca183-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca183-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca183-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ca183-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ca183-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ca183-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ca183-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ca183-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ca183-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ca183-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ca183-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="ca183-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca183-111">語法</span><span class="sxs-lookup"><span data-stu-id="ca183-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca183-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ca183-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ca183-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ca183-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca183-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ca183-114">Attributes</span></span>  
 <span data-ttu-id="ca183-115">無。</span><span class="sxs-lookup"><span data-stu-id="ca183-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca183-116">子元素</span><span class="sxs-lookup"><span data-stu-id="ca183-116">Child Elements</span></span>  
  
|<span data-ttu-id="ca183-117">項目</span><span class="sxs-lookup"><span data-stu-id="ca183-117">Element</span></span>|<span data-ttu-id="ca183-118">說明</span><span class="sxs-lookup"><span data-stu-id="ca183-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca183-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="ca183-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="ca183-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="ca183-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca183-121">父項目</span><span class="sxs-lookup"><span data-stu-id="ca183-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ca183-122">項目</span><span class="sxs-lookup"><span data-stu-id="ca183-122">Element</span></span>|<span data-ttu-id="ca183-123">說明</span><span class="sxs-lookup"><span data-stu-id="ca183-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca183-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ca183-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="ca183-125">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="ca183-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca183-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca183-126">See also</span></span>

- [<span data-ttu-id="ca183-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ca183-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ca183-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ca183-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
