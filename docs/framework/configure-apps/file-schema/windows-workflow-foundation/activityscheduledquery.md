---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 207931f68303883c29161cc28a5fc1974d01b6b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148733"
---
# \<activityScheduledQuery>

<span data-ttu-id="e5cd7-101">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e5cd7-102">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e5cd7-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e5cd7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="e5cd7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5cd7-104">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5cd7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5cd7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e5cd7-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5cd7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e5cd7-107">Attributes</span></span>  
  
|<span data-ttu-id="e5cd7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e5cd7-108">Attribute</span></span>|<span data-ttu-id="e5cd7-109">描述</span><span class="sxs-lookup"><span data-stu-id="e5cd7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5cd7-110">activityName</span><span class="sxs-lookup"><span data-stu-id="e5cd7-110">activityName</span></span>|<span data-ttu-id="e5cd7-111">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e5cd7-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e5cd7-112">childActivityName</span></span>|<span data-ttu-id="e5cd7-113">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5cd7-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e5cd7-114">Child Elements</span></span>  

 <span data-ttu-id="e5cd7-115">無。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5cd7-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e5cd7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e5cd7-117">項目</span><span class="sxs-lookup"><span data-stu-id="e5cd7-117">Element</span></span>|<span data-ttu-id="e5cd7-118">描述</span><span class="sxs-lookup"><span data-stu-id="e5cd7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="e5cd7-119">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="e5cd7-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5cd7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cd7-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e5cd7-121">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="e5cd7-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e5cd7-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e5cd7-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
