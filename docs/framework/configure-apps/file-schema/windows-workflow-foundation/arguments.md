---
title: '&lt;arguments&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 34695cd2fd62a0a10398fd73f014c093c3c5f61b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681660"
---
# <a name="ltargumentsgt"></a><span data-ttu-id="32551-102">&lt;arguments&gt;</span><span class="sxs-lookup"><span data-stu-id="32551-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="32551-103">表示與某個活動狀態查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="32551-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="32551-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="32551-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="32551-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32551-105">\<system.serviceModel></span></span>  
<span data-ttu-id="32551-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="32551-106">\<tracking></span></span>  
<span data-ttu-id="32551-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="32551-107">\<trackingProfile></span></span>  
<span data-ttu-id="32551-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="32551-108">\<workflow></span></span>  
<span data-ttu-id="32551-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="32551-109">\<activityStateQueries></span></span>  
<span data-ttu-id="32551-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="32551-110">\<activityStateQuery></span></span>  
<span data-ttu-id="32551-111">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="32551-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32551-112">語法</span><span class="sxs-lookup"><span data-stu-id="32551-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32551-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32551-113">Attributes and Elements</span></span>  
 <span data-ttu-id="32551-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="32551-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32551-115">屬性</span><span class="sxs-lookup"><span data-stu-id="32551-115">Attributes</span></span>  
 <span data-ttu-id="32551-116">無。</span><span class="sxs-lookup"><span data-stu-id="32551-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32551-117">子元素</span><span class="sxs-lookup"><span data-stu-id="32551-117">Child Elements</span></span>  
  
|<span data-ttu-id="32551-118">項目</span><span class="sxs-lookup"><span data-stu-id="32551-118">Element</span></span>|<span data-ttu-id="32551-119">描述</span><span class="sxs-lookup"><span data-stu-id="32551-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32551-120">\<argument></span><span class="sxs-lookup"><span data-stu-id="32551-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="32551-121">與活動狀態查詢相關聯的引數。</span><span class="sxs-lookup"><span data-stu-id="32551-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32551-122">父項目</span><span class="sxs-lookup"><span data-stu-id="32551-122">Parent Elements</span></span>  
  
|<span data-ttu-id="32551-123">項目</span><span class="sxs-lookup"><span data-stu-id="32551-123">Element</span></span>|<span data-ttu-id="32551-124">描述</span><span class="sxs-lookup"><span data-stu-id="32551-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32551-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="32551-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="32551-126">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="32551-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="32551-127">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="32551-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32551-128">備註</span><span class="sxs-lookup"><span data-stu-id="32551-128">Remarks</span></span>  
 <span data-ttu-id="32551-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="32551-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="32551-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="32551-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="32551-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="32551-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="32551-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="32551-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="32551-133">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="32551-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32551-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32551-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="32551-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="32551-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="32551-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="32551-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
