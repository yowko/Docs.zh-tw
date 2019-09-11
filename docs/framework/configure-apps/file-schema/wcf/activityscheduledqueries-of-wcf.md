---
title: <activityScheduledQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850490"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="a5328-102">\<WCF 的 activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="a5328-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="a5328-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a5328-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a5328-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="a5328-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="a5328-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a5328-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a5328-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5328-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5328-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a5328-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a5328-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5328-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a5328-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="a5328-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a5328-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5328-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="a5328-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5328-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="a5328-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="a5328-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5328-113">語法</span><span class="sxs-lookup"><span data-stu-id="a5328-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5328-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a5328-114">Attributes and elements</span></span>  

<span data-ttu-id="a5328-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a5328-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5328-116">屬性</span><span class="sxs-lookup"><span data-stu-id="a5328-116">Attributes</span></span>  

<span data-ttu-id="a5328-117">無。</span><span class="sxs-lookup"><span data-stu-id="a5328-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5328-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a5328-118">Child elements</span></span>  
  
|<span data-ttu-id="a5328-119">項目</span><span class="sxs-lookup"><span data-stu-id="a5328-119">Element</span></span>|<span data-ttu-id="a5328-120">描述</span><span class="sxs-lookup"><span data-stu-id="a5328-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5328-121">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="a5328-121">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="a5328-122">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a5328-122">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5328-123">父元素</span><span class="sxs-lookup"><span data-stu-id="a5328-123">Parent elements</span></span>  
  
|<span data-ttu-id="a5328-124">元素</span><span class="sxs-lookup"><span data-stu-id="a5328-124">Element</span></span>|<span data-ttu-id="a5328-125">描述</span><span class="sxs-lookup"><span data-stu-id="a5328-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5328-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a5328-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a5328-127">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="a5328-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5328-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5328-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="a5328-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a5328-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5328-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a5328-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
