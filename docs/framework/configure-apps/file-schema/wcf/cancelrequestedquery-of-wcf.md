---
title: <cancelRequestedQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850059"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="ed0ae-102">\<WCF 的 cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="ed0ae-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="ed0ae-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ed0ae-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="ed0ae-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="ed0ae-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ae-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed0ae-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ae-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ed0ae-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ae-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="ed0ae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="ed0ae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="ed0ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="ed0ae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="ed0ae-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ae-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)</span></span>\
<span data-ttu-id="ed0ae-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="ed0ae-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ed0ae-114">語法</span><span class="sxs-lookup"><span data-stu-id="ed0ae-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed0ae-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="ed0ae-115">Attributes and elements</span></span>

<span data-ttu-id="ed0ae-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed0ae-117">屬性</span><span class="sxs-lookup"><span data-stu-id="ed0ae-117">Attributes</span></span>  
  
|<span data-ttu-id="ed0ae-118">屬性</span><span class="sxs-lookup"><span data-stu-id="ed0ae-118">Attribute</span></span>|<span data-ttu-id="ed0ae-119">說明</span><span class="sxs-lookup"><span data-stu-id="ed0ae-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="ed0ae-120">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="ed0ae-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed0ae-122">子元素</span><span class="sxs-lookup"><span data-stu-id="ed0ae-122">Child elements</span></span>

<span data-ttu-id="ed0ae-123">無。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ed0ae-124">父元素</span><span class="sxs-lookup"><span data-stu-id="ed0ae-124">Parent elements</span></span>
  
|<span data-ttu-id="ed0ae-125">元素</span><span class="sxs-lookup"><span data-stu-id="ed0ae-125">Element</span></span>|<span data-ttu-id="ed0ae-126">描述</span><span class="sxs-lookup"><span data-stu-id="ed0ae-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed0ae-127">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ed0ae-127">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="ed0ae-128">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="ed0ae-128">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed0ae-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed0ae-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ed0ae-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ed0ae-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ed0ae-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ed0ae-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
