---
title: <bookmarkResumptionQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834010"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="137f4-102">\<WCF 的 bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="137f4-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="137f4-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="137f4-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="137f4-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="137f4-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="137f4-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="137f4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="137f4-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="137f4-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="137f4-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="137f4-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="137f4-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="137f4-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="137f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="137f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="137f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="137f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="137f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="137f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="137f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="137f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="137f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="137f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137f4-114">語法</span><span class="sxs-lookup"><span data-stu-id="137f4-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="137f4-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="137f4-115">Attributes and elements</span></span>

<span data-ttu-id="137f4-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="137f4-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="137f4-117">屬性</span><span class="sxs-lookup"><span data-stu-id="137f4-117">Attributes</span></span>  
  
|<span data-ttu-id="137f4-118">屬性</span><span class="sxs-lookup"><span data-stu-id="137f4-118">Attribute</span></span>|<span data-ttu-id="137f4-119">描述</span><span class="sxs-lookup"><span data-stu-id="137f4-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="137f4-120">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="137f4-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="137f4-121">子元素</span><span class="sxs-lookup"><span data-stu-id="137f4-121">Child elements</span></span>

<span data-ttu-id="137f4-122">無。</span><span class="sxs-lookup"><span data-stu-id="137f4-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="137f4-123">父元素</span><span class="sxs-lookup"><span data-stu-id="137f4-123">Parent elements</span></span>  
  
|<span data-ttu-id="137f4-124">元素</span><span class="sxs-lookup"><span data-stu-id="137f4-124">Element</span></span>|<span data-ttu-id="137f4-125">描述</span><span class="sxs-lookup"><span data-stu-id="137f4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="137f4-126">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="137f4-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="137f4-127">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="137f4-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="137f4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="137f4-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="137f4-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="137f4-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="137f4-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="137f4-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
