---
title: '&lt;states&gt; 的 &lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: e4eaf1cbe788018b46759efb1e9755d65b19cc60
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148287"
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="6534c-102">&lt;states&gt; 的 &lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="6534c-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="6534c-103">組態項目，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="6534c-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="6534c-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="6534c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6534c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6534c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6534c-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="6534c-106">\<tracking></span></span>  
<span data-ttu-id="6534c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6534c-107">\<trackingProfile></span></span>  
<span data-ttu-id="6534c-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="6534c-108">\<workflow></span></span>  
<span data-ttu-id="6534c-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="6534c-109">\<activityStateQueries></span></span>  
<span data-ttu-id="6534c-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="6534c-110">\<activityStateQuery></span></span>  
<span data-ttu-id="6534c-111">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="6534c-111">\<states></span></span>  
<span data-ttu-id="6534c-112">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="6534c-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6534c-113">語法</span><span class="sxs-lookup"><span data-stu-id="6534c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6534c-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6534c-114">Attributes and Elements</span></span>  
 <span data-ttu-id="6534c-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6534c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6534c-116">屬性</span><span class="sxs-lookup"><span data-stu-id="6534c-116">Attributes</span></span>  
  
|<span data-ttu-id="6534c-117">屬性</span><span class="sxs-lookup"><span data-stu-id="6534c-117">Attribute</span></span>|<span data-ttu-id="6534c-118">描述</span><span class="sxs-lookup"><span data-stu-id="6534c-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6534c-119">name</span><span class="sxs-lookup"><span data-stu-id="6534c-119">name</span></span>|<span data-ttu-id="6534c-120">可指定追蹤記錄應發出之已訂閱活動狀態的字串。</span><span class="sxs-lookup"><span data-stu-id="6534c-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6534c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6534c-121">Child Elements</span></span>  
 <span data-ttu-id="6534c-122">無。</span><span class="sxs-lookup"><span data-stu-id="6534c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6534c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6534c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6534c-124">項目</span><span class="sxs-lookup"><span data-stu-id="6534c-124">Element</span></span>|<span data-ttu-id="6534c-125">描述</span><span class="sxs-lookup"><span data-stu-id="6534c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6534c-126">\<狀態 ></span><span class="sxs-lookup"><span data-stu-id="6534c-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="6534c-127">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="6534c-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6534c-128">備註</span><span class="sxs-lookup"><span data-stu-id="6534c-128">Remarks</span></span>  
 <span data-ttu-id="6534c-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="6534c-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="6534c-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="6534c-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="6534c-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="6534c-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="6534c-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="6534c-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="6534c-133">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="6534c-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6534c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6534c-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="6534c-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="6534c-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6534c-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="6534c-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
