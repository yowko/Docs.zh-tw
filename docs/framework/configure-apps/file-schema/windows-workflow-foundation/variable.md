---
title: '&lt;variable&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 185e7e7196f6679ec3d1fae8a2a256b934022ca9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647877"
---
# <a name="ltvariablegt"></a><span data-ttu-id="308c2-102">&lt;variable&gt;</span><span class="sxs-lookup"><span data-stu-id="308c2-102">&lt;variable&gt;</span></span>
<span data-ttu-id="308c2-103">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="308c2-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="308c2-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="308c2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="308c2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="308c2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="308c2-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="308c2-106">\<tracking></span></span>  
<span data-ttu-id="308c2-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="308c2-107">\<profiles></span></span>  
<span data-ttu-id="308c2-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="308c2-108">\<trackingProfile></span></span>  
<span data-ttu-id="308c2-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="308c2-109">\<workflow></span></span>  
<span data-ttu-id="308c2-110">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="308c2-110">\<activityStateQueries></span></span>  
<span data-ttu-id="308c2-111">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="308c2-111">\<activityStateQuery></span></span>  
<span data-ttu-id="308c2-112">\<variables></span><span class="sxs-lookup"><span data-stu-id="308c2-112">\<variables></span></span>  
<span data-ttu-id="308c2-113">\<variable></span><span class="sxs-lookup"><span data-stu-id="308c2-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="308c2-114">語法</span><span class="sxs-lookup"><span data-stu-id="308c2-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="308c2-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="308c2-115">Attributes and Elements</span></span>  
 <span data-ttu-id="308c2-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="308c2-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="308c2-117">屬性</span><span class="sxs-lookup"><span data-stu-id="308c2-117">Attributes</span></span>  
  
|<span data-ttu-id="308c2-118">屬性</span><span class="sxs-lookup"><span data-stu-id="308c2-118">Attribute</span></span>|<span data-ttu-id="308c2-119">描述</span><span class="sxs-lookup"><span data-stu-id="308c2-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="308c2-120">name</span><span class="sxs-lookup"><span data-stu-id="308c2-120">name</span></span>|<span data-ttu-id="308c2-121">指定變數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="308c2-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="308c2-122">子元素</span><span class="sxs-lookup"><span data-stu-id="308c2-122">Child Elements</span></span>  
 <span data-ttu-id="308c2-123">無。</span><span class="sxs-lookup"><span data-stu-id="308c2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="308c2-124">父項目</span><span class="sxs-lookup"><span data-stu-id="308c2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="308c2-125">項目</span><span class="sxs-lookup"><span data-stu-id="308c2-125">Element</span></span>|<span data-ttu-id="308c2-126">描述</span><span class="sxs-lookup"><span data-stu-id="308c2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="308c2-127">\<variable></span><span class="sxs-lookup"><span data-stu-id="308c2-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="308c2-128">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="308c2-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="308c2-129">備註</span><span class="sxs-lookup"><span data-stu-id="308c2-129">Remarks</span></span>  
 <span data-ttu-id="308c2-130">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="308c2-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="308c2-131">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="308c2-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="308c2-132">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="308c2-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="308c2-133">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="308c2-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="308c2-134">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="308c2-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="308c2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="308c2-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="308c2-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="308c2-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="308c2-137">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="308c2-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
