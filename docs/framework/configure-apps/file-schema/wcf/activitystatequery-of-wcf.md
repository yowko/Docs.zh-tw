---
title: <activityStateQuery> WCF 的
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 97fce512415ad6ae165b29c7e8eff3394d5e675a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372044"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="67ef6-102">\<activityStateQuery > 的 WCF</span><span class="sxs-lookup"><span data-stu-id="67ef6-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="67ef6-103">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="67ef6-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="67ef6-104">例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。</span><span class="sxs-lookup"><span data-stu-id="67ef6-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="67ef6-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="67ef6-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="67ef6-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="67ef6-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="67ef6-107">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="67ef6-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="67ef6-108">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="67ef6-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="67ef6-109">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="67ef6-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="67ef6-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="67ef6-110">\<workflow></span></span>  
<span data-ttu-id="67ef6-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="67ef6-111">\<activityStateQueries></span></span>  
<span data-ttu-id="67ef6-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="67ef6-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ef6-113">語法</span><span class="sxs-lookup"><span data-stu-id="67ef6-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67ef6-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="67ef6-114">Attributes and elements</span></span>  

<span data-ttu-id="67ef6-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67ef6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67ef6-116">屬性</span><span class="sxs-lookup"><span data-stu-id="67ef6-116">Attributes</span></span>  
  
|<span data-ttu-id="67ef6-117">屬性</span><span class="sxs-lookup"><span data-stu-id="67ef6-117">Attribute</span></span>|<span data-ttu-id="67ef6-118">描述</span><span class="sxs-lookup"><span data-stu-id="67ef6-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67ef6-119">activityName</span><span class="sxs-lookup"><span data-stu-id="67ef6-119">activityName</span></span>|<span data-ttu-id="67ef6-120">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="67ef6-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67ef6-121">子元素</span><span class="sxs-lookup"><span data-stu-id="67ef6-121">Child elements</span></span>  
  
|<span data-ttu-id="67ef6-122">項目</span><span class="sxs-lookup"><span data-stu-id="67ef6-122">Element</span></span>|<span data-ttu-id="67ef6-123">描述</span><span class="sxs-lookup"><span data-stu-id="67ef6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67ef6-124">\<arguments></span><span class="sxs-lookup"><span data-stu-id="67ef6-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="67ef6-125">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="67ef6-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="67ef6-126">\<states></span><span class="sxs-lookup"><span data-stu-id="67ef6-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="67ef6-127">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="67ef6-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="67ef6-128">\<states></span><span class="sxs-lookup"><span data-stu-id="67ef6-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="67ef6-129">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="67ef6-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67ef6-130">父元素</span><span class="sxs-lookup"><span data-stu-id="67ef6-130">Parent elements</span></span>  
  
|<span data-ttu-id="67ef6-131">元素</span><span class="sxs-lookup"><span data-stu-id="67ef6-131">Element</span></span>|<span data-ttu-id="67ef6-132">描述</span><span class="sxs-lookup"><span data-stu-id="67ef6-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67ef6-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="67ef6-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="67ef6-134">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="67ef6-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="67ef6-135">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="67ef6-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ef6-136">備註</span><span class="sxs-lookup"><span data-stu-id="67ef6-136">Remarks</span></span>

<span data-ttu-id="67ef6-137">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="67ef6-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="67ef6-138">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="67ef6-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="67ef6-139">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。下列範例示範活動狀態查詢，擷取變數和引數時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="67ef6-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="67ef6-140">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="67ef6-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="67ef6-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67ef6-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="67ef6-142">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="67ef6-142">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="67ef6-143">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="67ef6-143">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
