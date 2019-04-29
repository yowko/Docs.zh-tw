---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 402b938913575adfa9125b981dc2913680f07b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790152"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="0722c-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="0722c-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="0722c-102">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="0722c-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0722c-103">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="0722c-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="0722c-104">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="0722c-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0722c-105">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="0722c-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="0722c-106">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0722c-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0722c-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0722c-107">\<system.serviceModel></span></span>  
<span data-ttu-id="0722c-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="0722c-108">\<tracking></span></span>  
<span data-ttu-id="0722c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0722c-109">\<trackingProfile></span></span>  
<span data-ttu-id="0722c-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0722c-110">\<workflow></span></span>  
<span data-ttu-id="0722c-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="0722c-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0722c-112">語法</span><span class="sxs-lookup"><span data-stu-id="0722c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0722c-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0722c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0722c-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0722c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0722c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0722c-115">Attributes</span></span>  
 <span data-ttu-id="0722c-116">無。</span><span class="sxs-lookup"><span data-stu-id="0722c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0722c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0722c-117">Child Elements</span></span>  
  
|<span data-ttu-id="0722c-118">項目</span><span class="sxs-lookup"><span data-stu-id="0722c-118">Element</span></span>|<span data-ttu-id="0722c-119">描述</span><span class="sxs-lookup"><span data-stu-id="0722c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0722c-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="0722c-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="0722c-121">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="0722c-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0722c-122">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="0722c-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0722c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="0722c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0722c-124">項目</span><span class="sxs-lookup"><span data-stu-id="0722c-124">Element</span></span>|<span data-ttu-id="0722c-125">描述</span><span class="sxs-lookup"><span data-stu-id="0722c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0722c-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0722c-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="0722c-127">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="0722c-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0722c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0722c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0722c-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="0722c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0722c-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0722c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
