---
title: <cancelRequestedQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850090"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="26c9d-102">\<WCF 的 cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="26c9d-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="26c9d-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="26c9d-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="26c9d-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="26c9d-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="26c9d-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="26c9d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="26c9d-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="26c9d-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="26c9d-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="26c9d-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="26c9d-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="26c9d-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="26c9d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="26c9d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="26c9d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="26c9d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="26c9d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="26c9d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="26c9d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="26c9d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c9d-113">語法</span><span class="sxs-lookup"><span data-stu-id="26c9d-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26c9d-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="26c9d-114">Attributes and elements</span></span>  

<span data-ttu-id="26c9d-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="26c9d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26c9d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="26c9d-116">Attributes</span></span>

<span data-ttu-id="26c9d-117">無。</span><span class="sxs-lookup"><span data-stu-id="26c9d-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="26c9d-118">子元素</span><span class="sxs-lookup"><span data-stu-id="26c9d-118">Child elements</span></span>
  
|<span data-ttu-id="26c9d-119">項目</span><span class="sxs-lookup"><span data-stu-id="26c9d-119">Element</span></span>|<span data-ttu-id="26c9d-120">描述</span><span class="sxs-lookup"><span data-stu-id="26c9d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26c9d-121">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="26c9d-121">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="26c9d-122">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="26c9d-122">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26c9d-123">父元素</span><span class="sxs-lookup"><span data-stu-id="26c9d-123">Parent elements</span></span>  
  
|<span data-ttu-id="26c9d-124">元素</span><span class="sxs-lookup"><span data-stu-id="26c9d-124">Element</span></span>|<span data-ttu-id="26c9d-125">說明</span><span class="sxs-lookup"><span data-stu-id="26c9d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26c9d-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="26c9d-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="26c9d-127">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="26c9d-127">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26c9d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26c9d-128">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="26c9d-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="26c9d-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="26c9d-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="26c9d-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
