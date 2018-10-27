---
title: WCF 的 &lt;faultPropagationQueries&gt;
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 1db99a8d80fad5c0eca93777d87047b43371d048
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044407"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="bd0e4-102">WCF 的 &lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="bd0e4-102">&lt;faultPropagationQueries&gt; of WCF</span></span>

<span data-ttu-id="bd0e4-103">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="bd0e4-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="bd0e4-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="bd0e4-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="bd0e4-107">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="bd0e4-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bd0e4-108">\<system.serviceModel></span></span>  
<span data-ttu-id="bd0e4-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="bd0e4-109">\<tracking></span></span>  
<span data-ttu-id="bd0e4-110">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="bd0e4-110">\<profiles></span></span>  
<span data-ttu-id="bd0e4-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bd0e4-111">\<trackingProfile></span></span>  
<span data-ttu-id="bd0e4-112">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="bd0e4-112">\<workflow></span></span>  
<span data-ttu-id="bd0e4-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="bd0e4-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0e4-114">語法</span><span class="sxs-lookup"><span data-stu-id="bd0e4-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="bd0e4-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="bd0e4-115">Attributes and elements</span></span>

<span data-ttu-id="bd0e4-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="bd0e4-117">屬性</span><span class="sxs-lookup"><span data-stu-id="bd0e4-117">Attributes</span></span>

<span data-ttu-id="bd0e4-118">無。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="bd0e4-119">子元素</span><span class="sxs-lookup"><span data-stu-id="bd0e4-119">Child elements</span></span>

|<span data-ttu-id="bd0e4-120">項目</span><span class="sxs-lookup"><span data-stu-id="bd0e4-120">Element</span></span>|<span data-ttu-id="bd0e4-121">描述</span><span class="sxs-lookup"><span data-stu-id="bd0e4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd0e4-122">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="bd0e4-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="bd0e4-123">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="bd0e4-124">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd0e4-125">父元素</span><span class="sxs-lookup"><span data-stu-id="bd0e4-125">Parent elements</span></span>  
  
|<span data-ttu-id="bd0e4-126">元素</span><span class="sxs-lookup"><span data-stu-id="bd0e4-126">Element</span></span>|<span data-ttu-id="bd0e4-127">描述</span><span class="sxs-lookup"><span data-stu-id="bd0e4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd0e4-128">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="bd0e4-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="bd0e4-129">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="bd0e4-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd0e4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd0e4-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bd0e4-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="bd0e4-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bd0e4-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="bd0e4-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
