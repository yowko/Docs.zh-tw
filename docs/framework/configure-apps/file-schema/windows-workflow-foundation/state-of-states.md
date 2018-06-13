---
title: '&lt;states&gt; 的 &lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 8893f6acfc7ec4d6989be2c647b0584093a534a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756848"
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="e9924-102">&lt;states&gt; 的 &lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="e9924-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="e9924-103">組態項目，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="e9924-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="e9924-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e9924-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e9924-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9924-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e9924-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="e9924-106">\<tracking></span></span>  
<span data-ttu-id="e9924-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e9924-107">\<trackingProfile></span></span>  
<span data-ttu-id="e9924-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="e9924-108">\<workflow></span></span>  
<span data-ttu-id="e9924-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="e9924-109">\<activityStateQueries></span></span>  
<span data-ttu-id="e9924-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e9924-110">\<activityStateQuery></span></span>  
<span data-ttu-id="e9924-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="e9924-111">\<states></span></span>  
<span data-ttu-id="e9924-112">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="e9924-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9924-113">語法</span><span class="sxs-lookup"><span data-stu-id="e9924-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9924-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9924-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e9924-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e9924-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9924-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e9924-116">Attributes</span></span>  
  
|<span data-ttu-id="e9924-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e9924-117">Attribute</span></span>|<span data-ttu-id="e9924-118">描述</span><span class="sxs-lookup"><span data-stu-id="e9924-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9924-119">name</span><span class="sxs-lookup"><span data-stu-id="e9924-119">name</span></span>|<span data-ttu-id="e9924-120">可指定追蹤記錄應發出之已訂閱活動狀態的字串。</span><span class="sxs-lookup"><span data-stu-id="e9924-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9924-121">子項目</span><span class="sxs-lookup"><span data-stu-id="e9924-121">Child Elements</span></span>  
 <span data-ttu-id="e9924-122">無。</span><span class="sxs-lookup"><span data-stu-id="e9924-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9924-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e9924-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9924-124">項目</span><span class="sxs-lookup"><span data-stu-id="e9924-124">Element</span></span>|<span data-ttu-id="e9924-125">描述</span><span class="sxs-lookup"><span data-stu-id="e9924-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9924-126">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="e9924-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="e9924-127">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="e9924-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9924-128">備註</span><span class="sxs-lookup"><span data-stu-id="e9924-128">Remarks</span></span>  
 <span data-ttu-id="e9924-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e9924-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e9924-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="e9924-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e9924-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e9924-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e9924-132">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="e9924-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9924-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9924-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="e9924-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e9924-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e9924-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e9924-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
