---
title: <bookmarkResumptionQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850134"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="4f4f6-102">\<WCF 的 bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="4f4f6-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="4f4f6-103">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4f4f6-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="4f4f6-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="4f4f6-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4f4f6-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4f4f6-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4f4f6-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4f4f6-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4f4f6-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="4f4f6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="4f4f6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="4f4f6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4f4f6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="4f4f6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4f4f6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="4f4f6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="4f4f6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="4f4f6-113">語法</span><span class="sxs-lookup"><span data-stu-id="4f4f6-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f4f6-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="4f4f6-114">Attributes and elements</span></span>  
  
<span data-ttu-id="4f4f6-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f4f6-116">屬性</span><span class="sxs-lookup"><span data-stu-id="4f4f6-116">Attributes</span></span>  
  
<span data-ttu-id="4f4f6-117">無。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f4f6-118">子元素</span><span class="sxs-lookup"><span data-stu-id="4f4f6-118">Child elements</span></span>  
  
|<span data-ttu-id="4f4f6-119">項目</span><span class="sxs-lookup"><span data-stu-id="4f4f6-119">Element</span></span>|<span data-ttu-id="4f4f6-120">描述</span><span class="sxs-lookup"><span data-stu-id="4f4f6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f4f6-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="4f4f6-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="4f4f6-122">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4f4f6-123">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f4f6-124">父元素</span><span class="sxs-lookup"><span data-stu-id="4f4f6-124">Parent elements</span></span>  
  
|<span data-ttu-id="4f4f6-125">元素</span><span class="sxs-lookup"><span data-stu-id="4f4f6-125">Element</span></span>|<span data-ttu-id="4f4f6-126">描述</span><span class="sxs-lookup"><span data-stu-id="4f4f6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f4f6-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4f4f6-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="4f4f6-128">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="4f4f6-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f4f6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f4f6-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4f4f6-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="4f4f6-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4f4f6-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4f4f6-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
