---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398859"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="2e8c6-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="2e8c6-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="2e8c6-102">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="2e8c6-103">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="2e8c6-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2e8c6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2e8c6-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2e8c6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2e8c6-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2e8c6-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2e8c6-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="2e8c6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="2e8c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="2e8c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="2e8c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2e8c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="2e8c6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="2e8c6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="2e8c6-111">語法</span><span class="sxs-lookup"><span data-stu-id="2e8c6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e8c6-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2e8c6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2e8c6-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e8c6-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2e8c6-114">Attributes</span></span>  
 <span data-ttu-id="2e8c6-115">無。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e8c6-116">子元素</span><span class="sxs-lookup"><span data-stu-id="2e8c6-116">Child Elements</span></span>  
  
|<span data-ttu-id="2e8c6-117">項目</span><span class="sxs-lookup"><span data-stu-id="2e8c6-117">Element</span></span>|<span data-ttu-id="2e8c6-118">描述</span><span class="sxs-lookup"><span data-stu-id="2e8c6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e8c6-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="2e8c6-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="2e8c6-120">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="2e8c6-121">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e8c6-122">父項目</span><span class="sxs-lookup"><span data-stu-id="2e8c6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2e8c6-123">項目</span><span class="sxs-lookup"><span data-stu-id="2e8c6-123">Element</span></span>|<span data-ttu-id="2e8c6-124">說明</span><span class="sxs-lookup"><span data-stu-id="2e8c6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e8c6-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="2e8c6-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="2e8c6-126">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="2e8c6-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e8c6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e8c6-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2e8c6-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2e8c6-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2e8c6-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2e8c6-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
