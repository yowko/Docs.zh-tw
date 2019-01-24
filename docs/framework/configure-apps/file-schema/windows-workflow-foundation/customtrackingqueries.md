---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 757bbe500ec3edccef465b7ff23b2c974e4a5011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598837"
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="a639b-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="a639b-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="a639b-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="a639b-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a639b-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a639b-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="a639b-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a639b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a639b-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a639b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a639b-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="a639b-107">\<tracking></span></span>  
<span data-ttu-id="a639b-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a639b-108">\<trackingProfile></span></span>  
<span data-ttu-id="a639b-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a639b-109">\<workflow></span></span>  
<span data-ttu-id="a639b-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="a639b-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a639b-111">語法</span><span class="sxs-lookup"><span data-stu-id="a639b-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a639b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a639b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a639b-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a639b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a639b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a639b-114">Attributes</span></span>  
 <span data-ttu-id="a639b-115">無。</span><span class="sxs-lookup"><span data-stu-id="a639b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a639b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="a639b-116">Child Elements</span></span>  
  
|<span data-ttu-id="a639b-117">項目</span><span class="sxs-lookup"><span data-stu-id="a639b-117">Element</span></span>|<span data-ttu-id="a639b-118">描述</span><span class="sxs-lookup"><span data-stu-id="a639b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a639b-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="a639b-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="a639b-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="a639b-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a639b-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a639b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a639b-122">項目</span><span class="sxs-lookup"><span data-stu-id="a639b-122">Element</span></span>|<span data-ttu-id="a639b-123">描述</span><span class="sxs-lookup"><span data-stu-id="a639b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a639b-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a639b-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a639b-125">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="a639b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a639b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a639b-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a639b-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a639b-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a639b-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a639b-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
