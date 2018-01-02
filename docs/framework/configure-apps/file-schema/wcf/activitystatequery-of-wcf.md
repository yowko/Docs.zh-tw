---
title: "WCF 的 &lt;activityStateQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de042732e7957fa6ea8c22d03ff6892ee1e912f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="56e70-102">WCF 的 &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="56e70-102">&lt;activityStateQuery&gt; of WCF</span></span>
<span data-ttu-id="56e70-103">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="56e70-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="56e70-104">比方說，您可能想要追蹤的每一次 「 傳送電子郵件 」 活動完成的工作流程執行個體中。</span><span class="sxs-lookup"><span data-stu-id="56e70-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="56e70-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="56e70-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="56e70-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="56e70-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="56e70-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="56e70-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="56e70-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="56e70-108">\<system.serviceModel></span></span>  
<span data-ttu-id="56e70-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="56e70-109">\<tracking></span></span>  
<span data-ttu-id="56e70-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="56e70-110">\<trackingProfile></span></span>  
<span data-ttu-id="56e70-111">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="56e70-111">\<workflow></span></span>  
<span data-ttu-id="56e70-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="56e70-112">\<activityStateQueries></span></span>  
<span data-ttu-id="56e70-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="56e70-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e70-114">語法</span><span class="sxs-lookup"><span data-stu-id="56e70-114">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56e70-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56e70-115">Attributes and Elements</span></span>  
 <span data-ttu-id="56e70-116">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56e70-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56e70-117">屬性</span><span class="sxs-lookup"><span data-stu-id="56e70-117">Attributes</span></span>  
  
|<span data-ttu-id="56e70-118">屬性</span><span class="sxs-lookup"><span data-stu-id="56e70-118">Attribute</span></span>|<span data-ttu-id="56e70-119">描述</span><span class="sxs-lookup"><span data-stu-id="56e70-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56e70-120">activityName</span><span class="sxs-lookup"><span data-stu-id="56e70-120">activityName</span></span>|<span data-ttu-id="56e70-121">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="56e70-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56e70-122">子元素</span><span class="sxs-lookup"><span data-stu-id="56e70-122">Child Elements</span></span>  
  
|<span data-ttu-id="56e70-123">項目</span><span class="sxs-lookup"><span data-stu-id="56e70-123">Element</span></span>|<span data-ttu-id="56e70-124">描述</span><span class="sxs-lookup"><span data-stu-id="56e70-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56e70-125">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="56e70-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="56e70-126">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="56e70-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="56e70-127">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="56e70-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="56e70-128">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="56e70-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="56e70-129">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="56e70-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="56e70-130">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="56e70-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56e70-131">父項目</span><span class="sxs-lookup"><span data-stu-id="56e70-131">Parent Elements</span></span>  
  
|<span data-ttu-id="56e70-132">項目</span><span class="sxs-lookup"><span data-stu-id="56e70-132">Element</span></span>|<span data-ttu-id="56e70-133">描述</span><span class="sxs-lookup"><span data-stu-id="56e70-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56e70-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="56e70-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="56e70-135">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="56e70-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="56e70-136">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="56e70-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56e70-137">備註</span><span class="sxs-lookup"><span data-stu-id="56e70-137">Remarks</span></span>  
 <span data-ttu-id="56e70-138">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="56e70-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="56e70-139">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="56e70-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="56e70-140">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="56e70-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="56e70-141">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="56e70-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56e70-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="56e70-142">See Also</span></span>  
 <span data-ttu-id="56e70-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span><span class="sxs-lookup"><span data-stu-id="56e70-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span></span>    
 <span data-ttu-id="56e70-144"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="56e70-144"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>     
 [<span data-ttu-id="56e70-145">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="56e70-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="56e70-146">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="56e70-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
