---
title: <states> 的 <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: fa3736fc13f6f40f52d15b8257b7a79f4179d738
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189595"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="d8587-102">\<狀態 > 的\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d8587-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="d8587-103">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="d8587-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="d8587-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="d8587-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d8587-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d8587-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d8587-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d8587-106">\<tracking></span></span>  
<span data-ttu-id="d8587-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d8587-107">\<trackingProfile></span></span>  
<span data-ttu-id="d8587-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d8587-108">\<workflow></span></span>  
<span data-ttu-id="d8587-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="d8587-109">\<activityStateQueries></span></span>  
<span data-ttu-id="d8587-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d8587-110">\<activityStateQuery></span></span>  
<span data-ttu-id="d8587-111">\<states></span><span class="sxs-lookup"><span data-stu-id="d8587-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8587-112">語法</span><span class="sxs-lookup"><span data-stu-id="d8587-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8587-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8587-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d8587-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8587-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8587-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d8587-115">Attributes</span></span>  
 <span data-ttu-id="d8587-116">無。</span><span class="sxs-lookup"><span data-stu-id="d8587-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8587-117">子元素</span><span class="sxs-lookup"><span data-stu-id="d8587-117">Child Elements</span></span>  
  
|<span data-ttu-id="d8587-118">項目</span><span class="sxs-lookup"><span data-stu-id="d8587-118">Element</span></span>|<span data-ttu-id="d8587-119">描述</span><span class="sxs-lookup"><span data-stu-id="d8587-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8587-120">\<state></span><span class="sxs-lookup"><span data-stu-id="d8587-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="d8587-121">組態項目，其中包含追蹤記錄應發出之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="d8587-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8587-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d8587-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d8587-123">項目</span><span class="sxs-lookup"><span data-stu-id="d8587-123">Element</span></span>|<span data-ttu-id="d8587-124">描述</span><span class="sxs-lookup"><span data-stu-id="d8587-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8587-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d8587-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="d8587-126">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="d8587-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d8587-127">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="d8587-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8587-128">備註</span><span class="sxs-lookup"><span data-stu-id="d8587-128">Remarks</span></span>  
 <span data-ttu-id="d8587-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="d8587-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d8587-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="d8587-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d8587-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="d8587-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d8587-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="d8587-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d8587-133">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="d8587-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8587-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8587-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d8587-135">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="d8587-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d8587-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d8587-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
