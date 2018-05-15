---
title: '&lt;引數&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: bfcb98085e0b2292d46acfd0a57096219afff606
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltargumentgt"></a><span data-ttu-id="66663-102">&lt;引數&gt;</span><span class="sxs-lookup"><span data-stu-id="66663-102">&lt;argument&gt;</span></span>
<span data-ttu-id="66663-103">表示與活動狀態查詢相關聯之引數的組態項目。</span><span class="sxs-lookup"><span data-stu-id="66663-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="66663-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="66663-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="66663-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="66663-105">\<system.serviceModel></span></span>  
<span data-ttu-id="66663-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="66663-106">\<tracking></span></span>  
<span data-ttu-id="66663-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="66663-107">\<trackingProfile></span></span>  
<span data-ttu-id="66663-108">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="66663-108">\<workflow></span></span>  
<span data-ttu-id="66663-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="66663-109">\<activityStateQueries></span></span>  
<span data-ttu-id="66663-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="66663-110">\<activityStateQuery></span></span>  
<span data-ttu-id="66663-111">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="66663-111">\<arguments></span></span>  
<span data-ttu-id="66663-112">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="66663-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66663-113">語法</span><span class="sxs-lookup"><span data-stu-id="66663-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66663-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66663-114">Attributes and Elements</span></span>  
 <span data-ttu-id="66663-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66663-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66663-116">屬性</span><span class="sxs-lookup"><span data-stu-id="66663-116">Attributes</span></span>  
  
|<span data-ttu-id="66663-117">屬性</span><span class="sxs-lookup"><span data-stu-id="66663-117">Attribute</span></span>|<span data-ttu-id="66663-118">描述</span><span class="sxs-lookup"><span data-stu-id="66663-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66663-119">name</span><span class="sxs-lookup"><span data-stu-id="66663-119">name</span></span>|<span data-ttu-id="66663-120">指定引數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="66663-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66663-121">子項目</span><span class="sxs-lookup"><span data-stu-id="66663-121">Child Elements</span></span>  
 <span data-ttu-id="66663-122">無。</span><span class="sxs-lookup"><span data-stu-id="66663-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66663-123">父項目</span><span class="sxs-lookup"><span data-stu-id="66663-123">Parent Elements</span></span>  
  
|<span data-ttu-id="66663-124">項目</span><span class="sxs-lookup"><span data-stu-id="66663-124">Element</span></span>|<span data-ttu-id="66663-125">描述</span><span class="sxs-lookup"><span data-stu-id="66663-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66663-126">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="66663-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="66663-127">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="66663-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66663-128">備註</span><span class="sxs-lookup"><span data-stu-id="66663-128">Remarks</span></span>  
 <span data-ttu-id="66663-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="66663-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="66663-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="66663-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="66663-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="66663-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="66663-132">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="66663-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66663-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66663-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="66663-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="66663-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="66663-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="66663-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
