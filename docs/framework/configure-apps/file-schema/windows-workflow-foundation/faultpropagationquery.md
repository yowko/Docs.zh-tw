---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 1a6899eaa04ad16192e07f4bc2ad1abe6e4aedd5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257361"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="9b239-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="9b239-101">\<faultPropagationQuery></span></span>
<span data-ttu-id="9b239-102">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="9b239-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9b239-103">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="9b239-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9b239-104">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="9b239-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9b239-105">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="9b239-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="9b239-106">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9b239-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9b239-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9b239-107">\<system.serviceModel></span></span>  
<span data-ttu-id="9b239-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="9b239-108">\<tracking></span></span>  
<span data-ttu-id="9b239-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9b239-109">\<trackingProfile></span></span>  
<span data-ttu-id="9b239-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9b239-110">\<workflow></span></span>  
<span data-ttu-id="9b239-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="9b239-111">\<faultPropagationQueries></span></span>  
<span data-ttu-id="9b239-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="9b239-112">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b239-113">語法</span><span class="sxs-lookup"><span data-stu-id="9b239-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b239-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9b239-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9b239-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9b239-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b239-116">屬性</span><span class="sxs-lookup"><span data-stu-id="9b239-116">Attributes</span></span>  
  
|<span data-ttu-id="9b239-117">屬性</span><span class="sxs-lookup"><span data-stu-id="9b239-117">Attribute</span></span>|<span data-ttu-id="9b239-118">描述</span><span class="sxs-lookup"><span data-stu-id="9b239-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b239-119">activityName</span><span class="sxs-lookup"><span data-stu-id="9b239-119">activityName</span></span>|<span data-ttu-id="9b239-120">字串，可指定傳用錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b239-120">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="9b239-121">預設為 \*，表示會針對所有活動傳回錯誤傳用記錄。</span><span class="sxs-lookup"><span data-stu-id="9b239-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="9b239-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="9b239-122">faultHandlerActivityName</span></span>|<span data-ttu-id="9b239-123">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="9b239-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b239-124">子元素</span><span class="sxs-lookup"><span data-stu-id="9b239-124">Child Elements</span></span>  
 <span data-ttu-id="9b239-125">無。</span><span class="sxs-lookup"><span data-stu-id="9b239-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b239-126">父項目</span><span class="sxs-lookup"><span data-stu-id="9b239-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9b239-127">項目</span><span class="sxs-lookup"><span data-stu-id="9b239-127">Element</span></span>|<span data-ttu-id="9b239-128">描述</span><span class="sxs-lookup"><span data-stu-id="9b239-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b239-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="9b239-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="9b239-130">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="9b239-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9b239-131">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="9b239-131">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b239-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b239-132">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9b239-133">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9b239-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9b239-134">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9b239-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
