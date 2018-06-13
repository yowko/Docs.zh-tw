---
title: WCF 的 &lt;faultPropagationQuery&gt;
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: fe3dd90a5c6b26537ab461b4bf4993df5be625a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747355"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="02aa3-102">WCF 的 &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="02aa3-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="02aa3-103">表示用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="02aa3-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="02aa3-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="02aa3-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="02aa3-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="02aa3-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="02aa3-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="02aa3-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="02aa3-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="02aa3-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="02aa3-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02aa3-108">\<system.serviceModel></span></span>  
<span data-ttu-id="02aa3-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="02aa3-109">\<tracking></span></span>  
<span data-ttu-id="02aa3-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="02aa3-110">\<trackingProfile></span></span>  
<span data-ttu-id="02aa3-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="02aa3-111">\<workflow></span></span>  
<span data-ttu-id="02aa3-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="02aa3-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="02aa3-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="02aa3-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02aa3-114">語法</span><span class="sxs-lookup"><span data-stu-id="02aa3-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02aa3-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02aa3-115">Attributes and Elements</span></span>  
 <span data-ttu-id="02aa3-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="02aa3-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02aa3-117">屬性</span><span class="sxs-lookup"><span data-stu-id="02aa3-117">Attributes</span></span>  
  
|<span data-ttu-id="02aa3-118">屬性</span><span class="sxs-lookup"><span data-stu-id="02aa3-118">Attribute</span></span>|<span data-ttu-id="02aa3-119">描述</span><span class="sxs-lookup"><span data-stu-id="02aa3-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02aa3-120">activityName</span><span class="sxs-lookup"><span data-stu-id="02aa3-120">activityName</span></span>|<span data-ttu-id="02aa3-121">字串，可指定傳用錯誤之錯誤處理常式活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="02aa3-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="02aa3-122">預設為 \*，表示會針對所有活動傳回錯誤傳用記錄。</span><span class="sxs-lookup"><span data-stu-id="02aa3-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="02aa3-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="02aa3-123">faultHandlerActivityName</span></span>|<span data-ttu-id="02aa3-124">字串，可指定本身是錯誤來源的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="02aa3-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02aa3-125">子項目</span><span class="sxs-lookup"><span data-stu-id="02aa3-125">Child Elements</span></span>  
 <span data-ttu-id="02aa3-126">無。</span><span class="sxs-lookup"><span data-stu-id="02aa3-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02aa3-127">父項目</span><span class="sxs-lookup"><span data-stu-id="02aa3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="02aa3-128">項目</span><span class="sxs-lookup"><span data-stu-id="02aa3-128">Element</span></span>|<span data-ttu-id="02aa3-129">描述</span><span class="sxs-lookup"><span data-stu-id="02aa3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02aa3-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="02aa3-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="02aa3-131">代表組態項目的清單，可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="02aa3-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="02aa3-132">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="02aa3-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02aa3-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02aa3-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="02aa3-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="02aa3-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="02aa3-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="02aa3-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
