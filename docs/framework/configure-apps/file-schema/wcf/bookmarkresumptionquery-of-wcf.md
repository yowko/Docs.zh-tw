---
title: <bookmarkResumptionQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 36d169b78e78692c7b45c75d5d375bddbba1c66f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850112"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="9f811-102">\<WCF 的 bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9f811-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="9f811-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="9f811-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9f811-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="9f811-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="9f811-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="9f811-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f811-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9f811-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="9f811-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="9f811-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="9f811-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="9f811-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="9f811-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f811-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="9f811-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="9f811-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f811-114">語法</span><span class="sxs-lookup"><span data-stu-id="9f811-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f811-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="9f811-115">Attributes and elements</span></span>

<span data-ttu-id="9f811-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9f811-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f811-117">屬性</span><span class="sxs-lookup"><span data-stu-id="9f811-117">Attributes</span></span>  
  
|<span data-ttu-id="9f811-118">屬性</span><span class="sxs-lookup"><span data-stu-id="9f811-118">Attribute</span></span>|<span data-ttu-id="9f811-119">說明</span><span class="sxs-lookup"><span data-stu-id="9f811-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9f811-120">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f811-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f811-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9f811-121">Child elements</span></span>

<span data-ttu-id="9f811-122">無。</span><span class="sxs-lookup"><span data-stu-id="9f811-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="9f811-123">父元素</span><span class="sxs-lookup"><span data-stu-id="9f811-123">Parent elements</span></span>  
  
|<span data-ttu-id="9f811-124">元素</span><span class="sxs-lookup"><span data-stu-id="9f811-124">Element</span></span>|<span data-ttu-id="9f811-125">說明</span><span class="sxs-lookup"><span data-stu-id="9f811-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f811-126">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="9f811-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="9f811-127">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="9f811-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f811-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f811-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9f811-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9f811-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9f811-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9f811-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
