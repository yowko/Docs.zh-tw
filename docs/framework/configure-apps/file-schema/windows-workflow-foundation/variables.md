---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 61a786efc67f4e9afa585864e1f62b966b5cdff8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105374"
---
# <a name="variables"></a><span data-ttu-id="14b36-101">\<variables></span><span class="sxs-lookup"><span data-stu-id="14b36-101">\<variables></span></span>
<span data-ttu-id="14b36-102">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="14b36-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="14b36-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="14b36-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="14b36-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="14b36-104">\<system.serviceModel></span></span>  
<span data-ttu-id="14b36-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="14b36-105">\<tracking></span></span>  
<span data-ttu-id="14b36-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="14b36-106">\<trackingProfile></span></span>  
<span data-ttu-id="14b36-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="14b36-107">\<workflow></span></span>  
<span data-ttu-id="14b36-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="14b36-108">\<activityStateQueries></span></span>  
<span data-ttu-id="14b36-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="14b36-109">\<activityStateQuery></span></span>  
<span data-ttu-id="14b36-110">\<variables></span><span class="sxs-lookup"><span data-stu-id="14b36-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b36-111">語法</span><span class="sxs-lookup"><span data-stu-id="14b36-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14b36-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="14b36-112">Attributes and Elements</span></span>  
 <span data-ttu-id="14b36-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="14b36-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14b36-114">屬性</span><span class="sxs-lookup"><span data-stu-id="14b36-114">Attributes</span></span>  
 <span data-ttu-id="14b36-115">無。</span><span class="sxs-lookup"><span data-stu-id="14b36-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14b36-116">子元素</span><span class="sxs-lookup"><span data-stu-id="14b36-116">Child Elements</span></span>  
  
|<span data-ttu-id="14b36-117">項目</span><span class="sxs-lookup"><span data-stu-id="14b36-117">Element</span></span>|<span data-ttu-id="14b36-118">描述</span><span class="sxs-lookup"><span data-stu-id="14b36-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14b36-119">\<variable></span><span class="sxs-lookup"><span data-stu-id="14b36-119">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="14b36-120">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="14b36-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14b36-121">父項目</span><span class="sxs-lookup"><span data-stu-id="14b36-121">Parent Elements</span></span>  
  
|<span data-ttu-id="14b36-122">項目</span><span class="sxs-lookup"><span data-stu-id="14b36-122">Element</span></span>|<span data-ttu-id="14b36-123">描述</span><span class="sxs-lookup"><span data-stu-id="14b36-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14b36-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="14b36-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="14b36-125">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="14b36-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="14b36-126">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="14b36-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14b36-127">備註</span><span class="sxs-lookup"><span data-stu-id="14b36-127">Remarks</span></span>  
 <span data-ttu-id="14b36-128">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="14b36-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="14b36-129">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="14b36-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="14b36-130">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="14b36-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="14b36-131">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="14b36-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="14b36-132">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="14b36-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14b36-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14b36-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="14b36-134">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="14b36-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="14b36-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="14b36-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
