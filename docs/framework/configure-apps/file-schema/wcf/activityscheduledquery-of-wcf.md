---
title: <activityScheduledQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850473"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="2f401-102">\<activityScheduledQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="2f401-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="2f401-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="2f401-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2f401-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="2f401-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="2f401-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2f401-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="2f401-106">語法</span><span class="sxs-lookup"><span data-stu-id="2f401-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f401-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2f401-107">Attributes and elements</span></span>  

<span data-ttu-id="2f401-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2f401-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f401-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2f401-109">Attributes</span></span>  
  
|<span data-ttu-id="2f401-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2f401-110">Attribute</span></span>|<span data-ttu-id="2f401-111">描述</span><span class="sxs-lookup"><span data-stu-id="2f401-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="2f401-112">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2f401-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="2f401-113">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2f401-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f401-114">子元素</span><span class="sxs-lookup"><span data-stu-id="2f401-114">Child elements</span></span>

<span data-ttu-id="2f401-115">無。</span><span class="sxs-lookup"><span data-stu-id="2f401-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2f401-116">父元素</span><span class="sxs-lookup"><span data-stu-id="2f401-116">Parent elements</span></span>  
  
|<span data-ttu-id="2f401-117">元素</span><span class="sxs-lookup"><span data-stu-id="2f401-117">Element</span></span>|<span data-ttu-id="2f401-118">描述</span><span class="sxs-lookup"><span data-stu-id="2f401-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="2f401-119">查詢的集合，用來追蹤由父活動排程執行的活動。</span><span class="sxs-lookup"><span data-stu-id="2f401-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f401-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f401-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="2f401-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2f401-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2f401-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2f401-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
