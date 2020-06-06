---
title: <activityScheduledQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850490"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="bbaed-102">\<activityScheduledQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="bbaed-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="bbaed-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="bbaed-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="bbaed-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="bbaed-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="bbaed-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bbaed-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="bbaed-106">語法</span><span class="sxs-lookup"><span data-stu-id="bbaed-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbaed-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="bbaed-107">Attributes and elements</span></span>  

<span data-ttu-id="bbaed-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bbaed-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbaed-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bbaed-109">Attributes</span></span>  

<span data-ttu-id="bbaed-110">無。</span><span class="sxs-lookup"><span data-stu-id="bbaed-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bbaed-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bbaed-111">Child elements</span></span>  
  
|<span data-ttu-id="bbaed-112">元素</span><span class="sxs-lookup"><span data-stu-id="bbaed-112">Element</span></span>|<span data-ttu-id="bbaed-113">描述</span><span class="sxs-lookup"><span data-stu-id="bbaed-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="bbaed-114">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="bbaed-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbaed-115">父元素</span><span class="sxs-lookup"><span data-stu-id="bbaed-115">Parent elements</span></span>  
  
|<span data-ttu-id="bbaed-116">元素</span><span class="sxs-lookup"><span data-stu-id="bbaed-116">Element</span></span>|<span data-ttu-id="bbaed-117">描述</span><span class="sxs-lookup"><span data-stu-id="bbaed-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="bbaed-118">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="bbaed-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbaed-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbaed-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="bbaed-120">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="bbaed-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bbaed-121">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="bbaed-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
