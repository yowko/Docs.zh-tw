---
title: <activityScheduledQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850473"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="36085-102">\<WCF 的 activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="36085-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="36085-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="36085-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="36085-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="36085-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="36085-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="36085-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="36085-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="36085-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="36085-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="36085-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="36085-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="36085-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="36085-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="36085-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="36085-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="36085-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="36085-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="36085-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="36085-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="36085-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)</span></span>\
<span data-ttu-id="36085-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="36085-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36085-114">語法</span><span class="sxs-lookup"><span data-stu-id="36085-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36085-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="36085-115">Attributes and elements</span></span>  

<span data-ttu-id="36085-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="36085-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36085-117">屬性</span><span class="sxs-lookup"><span data-stu-id="36085-117">Attributes</span></span>  
  
|<span data-ttu-id="36085-118">屬性</span><span class="sxs-lookup"><span data-stu-id="36085-118">Attribute</span></span>|<span data-ttu-id="36085-119">描述</span><span class="sxs-lookup"><span data-stu-id="36085-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="36085-120">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="36085-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="36085-121">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="36085-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36085-122">子元素</span><span class="sxs-lookup"><span data-stu-id="36085-122">Child elements</span></span>

<span data-ttu-id="36085-123">無。</span><span class="sxs-lookup"><span data-stu-id="36085-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="36085-124">父元素</span><span class="sxs-lookup"><span data-stu-id="36085-124">Parent elements</span></span>  
  
|<span data-ttu-id="36085-125">元素</span><span class="sxs-lookup"><span data-stu-id="36085-125">Element</span></span>|<span data-ttu-id="36085-126">說明</span><span class="sxs-lookup"><span data-stu-id="36085-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36085-127">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="36085-127">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="36085-128">查詢的集合，用來追蹤由父活動排程執行的活動。</span><span class="sxs-lookup"><span data-stu-id="36085-128">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36085-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36085-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="36085-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="36085-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="36085-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="36085-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
