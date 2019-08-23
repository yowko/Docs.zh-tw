---
title: <faultPropagationQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: aeb964fc8c96c8cb9aeb316bb95f9565fc4a7f18
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918948"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="e211d-102">\<WCF 的 faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e211d-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="e211d-103">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="e211d-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e211d-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="e211d-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e211d-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="e211d-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e211d-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="e211d-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="e211d-107">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e211d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e211d-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e211d-108">\<system.serviceModel></span></span>  
<span data-ttu-id="e211d-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="e211d-109">\<tracking></span></span>  
<span data-ttu-id="e211d-110">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="e211d-110">\<profiles></span></span>  
<span data-ttu-id="e211d-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e211d-111">\<trackingProfile></span></span>  
<span data-ttu-id="e211d-112">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="e211d-112">\<workflow></span></span>  
<span data-ttu-id="e211d-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e211d-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e211d-114">語法</span><span class="sxs-lookup"><span data-stu-id="e211d-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e211d-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e211d-115">Attributes and elements</span></span>

<span data-ttu-id="e211d-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e211d-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e211d-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e211d-117">Attributes</span></span>

<span data-ttu-id="e211d-118">無。</span><span class="sxs-lookup"><span data-stu-id="e211d-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="e211d-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e211d-119">Child elements</span></span>

|<span data-ttu-id="e211d-120">項目</span><span class="sxs-lookup"><span data-stu-id="e211d-120">Element</span></span>|<span data-ttu-id="e211d-121">描述</span><span class="sxs-lookup"><span data-stu-id="e211d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e211d-122">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e211d-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="e211d-123">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="e211d-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e211d-124">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="e211d-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e211d-125">父元素</span><span class="sxs-lookup"><span data-stu-id="e211d-125">Parent elements</span></span>  
  
|<span data-ttu-id="e211d-126">元素</span><span class="sxs-lookup"><span data-stu-id="e211d-126">Element</span></span>|<span data-ttu-id="e211d-127">說明</span><span class="sxs-lookup"><span data-stu-id="e211d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e211d-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e211d-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e211d-129">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="e211d-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e211d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e211d-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e211d-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e211d-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e211d-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e211d-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
