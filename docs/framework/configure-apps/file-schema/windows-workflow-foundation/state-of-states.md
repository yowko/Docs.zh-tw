---
title: <state> 的 <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947487"
---
# <a name="state-of-states"></a><span data-ttu-id="9d346-102">\<狀態 > \<></span><span class="sxs-lookup"><span data-stu-id="9d346-102">\<state> of \<states></span></span>
<span data-ttu-id="9d346-103">組態項目，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="9d346-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="9d346-104">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9d346-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9d346-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9d346-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9d346-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="9d346-106">\<tracking></span></span>  
<span data-ttu-id="9d346-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9d346-107">\<trackingProfile></span></span>  
<span data-ttu-id="9d346-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="9d346-108">\<workflow></span></span>  
<span data-ttu-id="9d346-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="9d346-109">\<activityStateQueries></span></span>  
<span data-ttu-id="9d346-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="9d346-110">\<activityStateQuery></span></span>  
<span data-ttu-id="9d346-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="9d346-111">\<states></span></span>  
<span data-ttu-id="9d346-112">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="9d346-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d346-113">語法</span><span class="sxs-lookup"><span data-stu-id="9d346-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d346-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9d346-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9d346-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9d346-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d346-116">屬性</span><span class="sxs-lookup"><span data-stu-id="9d346-116">Attributes</span></span>  
  
|<span data-ttu-id="9d346-117">屬性</span><span class="sxs-lookup"><span data-stu-id="9d346-117">Attribute</span></span>|<span data-ttu-id="9d346-118">描述</span><span class="sxs-lookup"><span data-stu-id="9d346-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d346-119">NAME</span><span class="sxs-lookup"><span data-stu-id="9d346-119">name</span></span>|<span data-ttu-id="9d346-120">可指定追蹤記錄應發出之已訂閱活動狀態的字串。</span><span class="sxs-lookup"><span data-stu-id="9d346-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d346-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9d346-121">Child Elements</span></span>  
 <span data-ttu-id="9d346-122">無。</span><span class="sxs-lookup"><span data-stu-id="9d346-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d346-123">父項目</span><span class="sxs-lookup"><span data-stu-id="9d346-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9d346-124">項目</span><span class="sxs-lookup"><span data-stu-id="9d346-124">Element</span></span>|<span data-ttu-id="9d346-125">描述</span><span class="sxs-lookup"><span data-stu-id="9d346-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d346-126">\<states></span><span class="sxs-lookup"><span data-stu-id="9d346-126">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="9d346-127">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="9d346-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d346-128">備註</span><span class="sxs-lookup"><span data-stu-id="9d346-128">Remarks</span></span>  
 <span data-ttu-id="9d346-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="9d346-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9d346-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="9d346-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9d346-131">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素, 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="9d346-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="9d346-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="9d346-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9d346-133">只能使用 ActivityStateRecord 來解壓縮變數和引數, 因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="9d346-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d346-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d346-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9d346-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9d346-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9d346-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9d346-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
