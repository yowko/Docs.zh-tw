---
title: WCF 的 &lt;faultPropagationQuery&gt;
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: c3853c470a9243835e071d35008dfff5b885591d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123315"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="c7336-102">WCF 的 &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="c7336-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="c7336-103">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="c7336-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c7336-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="c7336-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c7336-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="c7336-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c7336-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="c7336-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="c7336-107">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="c7336-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c7336-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c7336-108">\<system.serviceModel></span></span>  
<span data-ttu-id="c7336-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="c7336-109">\<tracking></span></span>  
<span data-ttu-id="c7336-110">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="c7336-110">\<profiles></span></span>  
<span data-ttu-id="c7336-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c7336-111">\<trackingProfile></span></span>  
<span data-ttu-id="c7336-112">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c7336-112">\<workflow></span></span>  
<span data-ttu-id="c7336-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c7336-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="c7336-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c7336-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7336-115">語法</span><span class="sxs-lookup"><span data-stu-id="c7336-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7336-116">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c7336-116">Attributes and elements</span></span>

<span data-ttu-id="c7336-117">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c7336-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7336-118">屬性</span><span class="sxs-lookup"><span data-stu-id="c7336-118">Attributes</span></span>  
  
|<span data-ttu-id="c7336-119">屬性</span><span class="sxs-lookup"><span data-stu-id="c7336-119">Attribute</span></span>|<span data-ttu-id="c7336-120">描述</span><span class="sxs-lookup"><span data-stu-id="c7336-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="c7336-121">字串，可指定傳用錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7336-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="c7336-122">預設值是\*，這表示所有活動傳回錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="c7336-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="c7336-123">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c7336-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7336-124">子元素</span><span class="sxs-lookup"><span data-stu-id="c7336-124">Child elements</span></span>

<span data-ttu-id="c7336-125">無。</span><span class="sxs-lookup"><span data-stu-id="c7336-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c7336-126">父元素</span><span class="sxs-lookup"><span data-stu-id="c7336-126">Parent elements</span></span>  
  
|<span data-ttu-id="c7336-127">元素</span><span class="sxs-lookup"><span data-stu-id="c7336-127">Element</span></span>|<span data-ttu-id="c7336-128">描述</span><span class="sxs-lookup"><span data-stu-id="c7336-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7336-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="c7336-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="c7336-130">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="c7336-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c7336-131">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="c7336-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="c7336-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7336-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c7336-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c7336-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c7336-134">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c7336-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
