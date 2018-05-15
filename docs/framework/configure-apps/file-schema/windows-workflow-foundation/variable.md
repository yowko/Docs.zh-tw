---
title: '&lt;變數&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 7d41d80bfe83cfafca01509d50709e21730bcb97
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltvariablegt"></a><span data-ttu-id="aeeb6-102">&lt;變數&gt;</span><span class="sxs-lookup"><span data-stu-id="aeeb6-102">&lt;variable&gt;</span></span>
<span data-ttu-id="aeeb6-103">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="aeeb6-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="aeeb6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aeeb6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="aeeb6-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-106">\<tracking></span></span>  
<span data-ttu-id="aeeb6-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-107">\<profiles></span></span>  
<span data-ttu-id="aeeb6-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="aeeb6-108">\<trackingProfile></span></span>  
<span data-ttu-id="aeeb6-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-109">\<workflow></span></span>  
<span data-ttu-id="aeeb6-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-110">\<activityStateQueries></span></span>  
<span data-ttu-id="aeeb6-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-111">\<activityStateQuery></span></span>  
<span data-ttu-id="aeeb6-112">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-112">\<variables></span></span>  
<span data-ttu-id="aeeb6-113">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeeb6-114">語法</span><span class="sxs-lookup"><span data-stu-id="aeeb6-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeeb6-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aeeb6-115">Attributes and Elements</span></span>  
 <span data-ttu-id="aeeb6-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeeb6-117">屬性</span><span class="sxs-lookup"><span data-stu-id="aeeb6-117">Attributes</span></span>  
  
|<span data-ttu-id="aeeb6-118">屬性</span><span class="sxs-lookup"><span data-stu-id="aeeb6-118">Attribute</span></span>|<span data-ttu-id="aeeb6-119">描述</span><span class="sxs-lookup"><span data-stu-id="aeeb6-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aeeb6-120">name</span><span class="sxs-lookup"><span data-stu-id="aeeb6-120">name</span></span>|<span data-ttu-id="aeeb6-121">指定變數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aeeb6-122">子項目</span><span class="sxs-lookup"><span data-stu-id="aeeb6-122">Child Elements</span></span>  
 <span data-ttu-id="aeeb6-123">無。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aeeb6-124">父項目</span><span class="sxs-lookup"><span data-stu-id="aeeb6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="aeeb6-125">項目</span><span class="sxs-lookup"><span data-stu-id="aeeb6-125">Element</span></span>|<span data-ttu-id="aeeb6-126">描述</span><span class="sxs-lookup"><span data-stu-id="aeeb6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aeeb6-127">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="aeeb6-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="aeeb6-128">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeeb6-129">備註</span><span class="sxs-lookup"><span data-stu-id="aeeb6-129">Remarks</span></span>  
 <span data-ttu-id="aeeb6-130">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="aeeb6-131">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="aeeb6-132">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="aeeb6-133">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="aeeb6-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aeeb6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aeeb6-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="aeeb6-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="aeeb6-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="aeeb6-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="aeeb6-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
