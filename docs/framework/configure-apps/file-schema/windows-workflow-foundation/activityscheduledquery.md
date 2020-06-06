---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152407"
---
# \<activityScheduledQuery>
<span data-ttu-id="7c0dd-101">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7c0dd-102">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="7c0dd-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7c0dd-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="7c0dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c0dd-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c0dd-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c0dd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7c0dd-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c0dd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7c0dd-107">Attributes</span></span>  
  
|<span data-ttu-id="7c0dd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7c0dd-108">Attribute</span></span>|<span data-ttu-id="7c0dd-109">描述</span><span class="sxs-lookup"><span data-stu-id="7c0dd-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c0dd-110">activityName</span><span class="sxs-lookup"><span data-stu-id="7c0dd-110">activityName</span></span>|<span data-ttu-id="7c0dd-111">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="7c0dd-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="7c0dd-112">childActivityName</span></span>|<span data-ttu-id="7c0dd-113">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c0dd-114">子元素</span><span class="sxs-lookup"><span data-stu-id="7c0dd-114">Child Elements</span></span>  
 <span data-ttu-id="7c0dd-115">無。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c0dd-116">父項目</span><span class="sxs-lookup"><span data-stu-id="7c0dd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7c0dd-117">元素</span><span class="sxs-lookup"><span data-stu-id="7c0dd-117">Element</span></span>|<span data-ttu-id="7c0dd-118">描述</span><span class="sxs-lookup"><span data-stu-id="7c0dd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="7c0dd-119">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="7c0dd-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c0dd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c0dd-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7c0dd-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="7c0dd-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7c0dd-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="7c0dd-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
