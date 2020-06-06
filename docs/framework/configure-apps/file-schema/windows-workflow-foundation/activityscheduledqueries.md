---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152420"
---
# \<activityScheduledQueries>
<span data-ttu-id="d97b7-101">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d97b7-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d97b7-102">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="d97b7-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d97b7-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d97b7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="d97b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d97b7-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d97b7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d97b7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d97b7-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d97b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d97b7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d97b7-107">Attributes</span></span>  
 <span data-ttu-id="d97b7-108">無。</span><span class="sxs-lookup"><span data-stu-id="d97b7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d97b7-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d97b7-109">Child Elements</span></span>  
  
|<span data-ttu-id="d97b7-110">元素</span><span class="sxs-lookup"><span data-stu-id="d97b7-110">Element</span></span>|<span data-ttu-id="d97b7-111">描述</span><span class="sxs-lookup"><span data-stu-id="d97b7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="d97b7-112">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d97b7-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d97b7-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d97b7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d97b7-114">元素</span><span class="sxs-lookup"><span data-stu-id="d97b7-114">Element</span></span>|<span data-ttu-id="d97b7-115">描述</span><span class="sxs-lookup"><span data-stu-id="d97b7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="d97b7-116">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="d97b7-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d97b7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d97b7-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d97b7-118">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d97b7-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d97b7-119">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d97b7-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
