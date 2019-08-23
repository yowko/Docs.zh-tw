---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 560df771b44fc8ba8d192657677bf0496283b539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945420"
---
# <a name="activitystatequery"></a><span data-ttu-id="9bb9f-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="9bb9f-101">\<activityStateQuery></span></span>
<span data-ttu-id="9bb9f-102">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="9bb9f-103">例如, 您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="9bb9f-104">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="9bb9f-105">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="9bb9f-106">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9bb9f-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9bb9f-107">\<system.serviceModel></span></span>  
<span data-ttu-id="9bb9f-108">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="9bb9f-108">\<tracking></span></span>  
<span data-ttu-id="9bb9f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9bb9f-109">\<trackingProfile></span></span>  
<span data-ttu-id="9bb9f-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="9bb9f-110">\<workflow></span></span>  
<span data-ttu-id="9bb9f-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="9bb9f-111">\<activityStateQueries></span></span>  
<span data-ttu-id="9bb9f-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="9bb9f-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb9f-113">語法</span><span class="sxs-lookup"><span data-stu-id="9bb9f-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bb9f-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9bb9f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9bb9f-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bb9f-116">屬性</span><span class="sxs-lookup"><span data-stu-id="9bb9f-116">Attributes</span></span>  
  
|<span data-ttu-id="9bb9f-117">屬性</span><span class="sxs-lookup"><span data-stu-id="9bb9f-117">Attribute</span></span>|<span data-ttu-id="9bb9f-118">描述</span><span class="sxs-lookup"><span data-stu-id="9bb9f-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bb9f-119">activityName</span><span class="sxs-lookup"><span data-stu-id="9bb9f-119">activityName</span></span>|<span data-ttu-id="9bb9f-120">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bb9f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9bb9f-121">Child Elements</span></span>  
  
|<span data-ttu-id="9bb9f-122">項目</span><span class="sxs-lookup"><span data-stu-id="9bb9f-122">Element</span></span>|<span data-ttu-id="9bb9f-123">描述</span><span class="sxs-lookup"><span data-stu-id="9bb9f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bb9f-124">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="9bb9f-124">\<arguments></span></span>](arguments.md)|<span data-ttu-id="9bb9f-125">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="9bb9f-126">\<states></span><span class="sxs-lookup"><span data-stu-id="9bb9f-126">\<states></span></span>](states.md)|<span data-ttu-id="9bb9f-127">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="9bb9f-128">\<states></span><span class="sxs-lookup"><span data-stu-id="9bb9f-128">\<states></span></span>](states.md)|<span data-ttu-id="9bb9f-129">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bb9f-130">父項目</span><span class="sxs-lookup"><span data-stu-id="9bb9f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="9bb9f-131">項目</span><span class="sxs-lookup"><span data-stu-id="9bb9f-131">Element</span></span>|<span data-ttu-id="9bb9f-132">描述</span><span class="sxs-lookup"><span data-stu-id="9bb9f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bb9f-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="9bb9f-133">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="9bb9f-134">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9bb9f-135">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bb9f-136">備註</span><span class="sxs-lookup"><span data-stu-id="9bb9f-136">Remarks</span></span>  
 <span data-ttu-id="9bb9f-137">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9bb9f-138">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9bb9f-139">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素, 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-139">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="9bb9f-140">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9bb9f-141">只能使用 ActivityStateRecord 來解壓縮變數和引數, 因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="9bb9f-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9bb9f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bb9f-142">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9bb9f-143">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9bb9f-143">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9bb9f-144">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9bb9f-144">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
