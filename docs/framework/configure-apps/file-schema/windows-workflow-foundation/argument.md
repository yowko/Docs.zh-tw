---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: a920d60d703fe262bee96d75c420c526d54f88ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210642"
---
# <a name="argument"></a><span data-ttu-id="e890e-101">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e890e-101">\<argument></span></span>
<span data-ttu-id="e890e-102">表示與活動狀態查詢相關聯之引數的組態項目。</span><span class="sxs-lookup"><span data-stu-id="e890e-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="e890e-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e890e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e890e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e890e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e890e-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e890e-105">\<tracking></span></span>  
<span data-ttu-id="e890e-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e890e-106">\<trackingProfile></span></span>  
<span data-ttu-id="e890e-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e890e-107">\<workflow></span></span>  
<span data-ttu-id="e890e-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="e890e-108">\<activityStateQueries></span></span>  
<span data-ttu-id="e890e-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="e890e-109">\<activityStateQuery></span></span>  
<span data-ttu-id="e890e-110">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e890e-110">\<arguments></span></span>  
<span data-ttu-id="e890e-111">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="e890e-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e890e-112">語法</span><span class="sxs-lookup"><span data-stu-id="e890e-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e890e-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e890e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e890e-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e890e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e890e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e890e-115">Attributes</span></span>  
  
|<span data-ttu-id="e890e-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e890e-116">Attribute</span></span>|<span data-ttu-id="e890e-117">描述</span><span class="sxs-lookup"><span data-stu-id="e890e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e890e-118">名稱</span><span class="sxs-lookup"><span data-stu-id="e890e-118">name</span></span>|<span data-ttu-id="e890e-119">指定引數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e890e-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e890e-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e890e-120">Child Elements</span></span>  
 <span data-ttu-id="e890e-121">無。</span><span class="sxs-lookup"><span data-stu-id="e890e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e890e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="e890e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e890e-123">項目</span><span class="sxs-lookup"><span data-stu-id="e890e-123">Element</span></span>|<span data-ttu-id="e890e-124">描述</span><span class="sxs-lookup"><span data-stu-id="e890e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e890e-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="e890e-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="e890e-126">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="e890e-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e890e-127">備註</span><span class="sxs-lookup"><span data-stu-id="e890e-127">Remarks</span></span>  
 <span data-ttu-id="e890e-128">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e890e-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e890e-129">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="e890e-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e890e-130">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="e890e-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e890e-131">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="e890e-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e890e-132">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="e890e-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e890e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e890e-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e890e-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e890e-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e890e-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e890e-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
