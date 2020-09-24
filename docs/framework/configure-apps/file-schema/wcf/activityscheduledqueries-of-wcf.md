---
title: <activityScheduledQueries> WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 86f196437b2230d6541570aa8994d99e7b340f66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151190"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="7978e-102">\<activityScheduledQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="7978e-102">\<activityScheduledQueries> of WCF</span></span>

<span data-ttu-id="7978e-103">代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="7978e-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7978e-104">追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。</span><span class="sxs-lookup"><span data-stu-id="7978e-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="7978e-105">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7978e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="7978e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7978e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7978e-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="7978e-107">Attributes and elements</span></span>  

<span data-ttu-id="7978e-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7978e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7978e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7978e-109">Attributes</span></span>  

<span data-ttu-id="7978e-110">無。</span><span class="sxs-lookup"><span data-stu-id="7978e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7978e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7978e-111">Child elements</span></span>  
  
|<span data-ttu-id="7978e-112">項目</span><span class="sxs-lookup"><span data-stu-id="7978e-112">Element</span></span>|<span data-ttu-id="7978e-113">描述</span><span class="sxs-lookup"><span data-stu-id="7978e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="7978e-114">查詢，可用來追蹤已排程且由父活動執行的活動。</span><span class="sxs-lookup"><span data-stu-id="7978e-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7978e-115">父元素</span><span class="sxs-lookup"><span data-stu-id="7978e-115">Parent elements</span></span>  
  
|<span data-ttu-id="7978e-116">項目</span><span class="sxs-lookup"><span data-stu-id="7978e-116">Element</span></span>|<span data-ttu-id="7978e-117">描述</span><span class="sxs-lookup"><span data-stu-id="7978e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="7978e-118">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="7978e-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7978e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7978e-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="7978e-120">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="7978e-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7978e-121">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="7978e-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
