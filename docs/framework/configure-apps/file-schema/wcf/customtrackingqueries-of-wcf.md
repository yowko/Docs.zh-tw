---
title: <customTrackingQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: abc0c7dfb426338ec6bca61b0a4b87754bb63588
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925945"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="d782f-102">\<WCF 的 customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d782f-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="d782f-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="d782f-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d782f-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d782f-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d782f-105">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="d782f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="d782f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d782f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d782f-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d782f-107">\<tracking></span></span>  
<span data-ttu-id="d782f-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="d782f-108">\<profiles></span></span>  
<span data-ttu-id="d782f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d782f-109">\<trackingProfile></span></span>  
<span data-ttu-id="d782f-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="d782f-110">\<workflow></span></span>  
<span data-ttu-id="d782f-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d782f-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d782f-112">語法</span><span class="sxs-lookup"><span data-stu-id="d782f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d782f-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="d782f-113">Attributes and elements</span></span>

<span data-ttu-id="d782f-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d782f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d782f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d782f-115">Attributes</span></span>

<span data-ttu-id="d782f-116">無。</span><span class="sxs-lookup"><span data-stu-id="d782f-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="d782f-117">子元素</span><span class="sxs-lookup"><span data-stu-id="d782f-117">Child elements</span></span>
  
|<span data-ttu-id="d782f-118">項目</span><span class="sxs-lookup"><span data-stu-id="d782f-118">Element</span></span>|<span data-ttu-id="d782f-119">說明</span><span class="sxs-lookup"><span data-stu-id="d782f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d782f-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d782f-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="d782f-121">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="d782f-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d782f-122">父元素</span><span class="sxs-lookup"><span data-stu-id="d782f-122">Parent elements</span></span>  
  
|<span data-ttu-id="d782f-123">元素</span><span class="sxs-lookup"><span data-stu-id="d782f-123">Element</span></span>|<span data-ttu-id="d782f-124">說明</span><span class="sxs-lookup"><span data-stu-id="d782f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d782f-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d782f-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="d782f-126">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="d782f-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d782f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d782f-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d782f-128">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d782f-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d782f-129">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d782f-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
