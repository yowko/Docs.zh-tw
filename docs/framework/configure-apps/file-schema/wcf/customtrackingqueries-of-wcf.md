---
title: <customTrackingQueries> WCF 的
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 8b317cc289853902592e145e34b6e7bf5f84763b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282369"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="40326-102">\<customTrackingQueries > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="40326-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="40326-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="40326-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="40326-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="40326-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="40326-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="40326-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="40326-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="40326-106">\<system.serviceModel></span></span>  
<span data-ttu-id="40326-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="40326-107">\<tracking></span></span>  
<span data-ttu-id="40326-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="40326-108">\<profiles></span></span>  
<span data-ttu-id="40326-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="40326-109">\<trackingProfile></span></span>  
<span data-ttu-id="40326-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="40326-110">\<workflow></span></span>  
<span data-ttu-id="40326-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="40326-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40326-112">語法</span><span class="sxs-lookup"><span data-stu-id="40326-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40326-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="40326-113">Attributes and elements</span></span>

<span data-ttu-id="40326-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="40326-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40326-115">屬性</span><span class="sxs-lookup"><span data-stu-id="40326-115">Attributes</span></span>

<span data-ttu-id="40326-116">無。</span><span class="sxs-lookup"><span data-stu-id="40326-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="40326-117">子元素</span><span class="sxs-lookup"><span data-stu-id="40326-117">Child elements</span></span>
  
|<span data-ttu-id="40326-118">項目</span><span class="sxs-lookup"><span data-stu-id="40326-118">Element</span></span>|<span data-ttu-id="40326-119">描述</span><span class="sxs-lookup"><span data-stu-id="40326-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40326-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="40326-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="40326-121">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="40326-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40326-122">父元素</span><span class="sxs-lookup"><span data-stu-id="40326-122">Parent elements</span></span>  
  
|<span data-ttu-id="40326-123">元素</span><span class="sxs-lookup"><span data-stu-id="40326-123">Element</span></span>|<span data-ttu-id="40326-124">描述</span><span class="sxs-lookup"><span data-stu-id="40326-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40326-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="40326-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="40326-126">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="40326-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40326-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40326-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="40326-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="40326-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="40326-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="40326-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
