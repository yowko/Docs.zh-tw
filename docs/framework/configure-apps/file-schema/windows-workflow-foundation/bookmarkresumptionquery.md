---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398855"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="ecd40-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="ecd40-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="ecd40-102">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="ecd40-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ecd40-103">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="ecd40-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="ecd40-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ecd40-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ecd40-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ecd40-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ecd40-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ecd40-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ecd40-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries.md)</span><span class="sxs-lookup"><span data-stu-id="ecd40-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)</span></span>\
<span data-ttu-id="ecd40-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="ecd40-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd40-112">語法</span><span class="sxs-lookup"><span data-stu-id="ecd40-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecd40-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ecd40-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ecd40-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ecd40-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecd40-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ecd40-115">Attributes</span></span>  
  
|<span data-ttu-id="ecd40-116">屬性</span><span class="sxs-lookup"><span data-stu-id="ecd40-116">Attribute</span></span>|<span data-ttu-id="ecd40-117">描述</span><span class="sxs-lookup"><span data-stu-id="ecd40-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecd40-118">NAME</span><span class="sxs-lookup"><span data-stu-id="ecd40-118">name</span></span>|<span data-ttu-id="ecd40-119">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ecd40-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecd40-120">子元素</span><span class="sxs-lookup"><span data-stu-id="ecd40-120">Child Elements</span></span>  
 <span data-ttu-id="ecd40-121">無。</span><span class="sxs-lookup"><span data-stu-id="ecd40-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecd40-122">父項目</span><span class="sxs-lookup"><span data-stu-id="ecd40-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ecd40-123">項目</span><span class="sxs-lookup"><span data-stu-id="ecd40-123">Element</span></span>|<span data-ttu-id="ecd40-124">描述</span><span class="sxs-lookup"><span data-stu-id="ecd40-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecd40-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="ecd40-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="ecd40-126">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="ecd40-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecd40-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecd40-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ecd40-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ecd40-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ecd40-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ecd40-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
