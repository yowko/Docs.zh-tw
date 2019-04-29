---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: c85f3c57739c48566c97c8b1debfb7f2c3912bdf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613517"
---
# <a name="variable"></a><span data-ttu-id="c3450-101">\<variable></span><span class="sxs-lookup"><span data-stu-id="c3450-101">\<variable></span></span>
<span data-ttu-id="c3450-102">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="c3450-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="c3450-103">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="c3450-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c3450-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c3450-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c3450-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c3450-105">\<tracking></span></span>  
<span data-ttu-id="c3450-106">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="c3450-106">\<profiles></span></span>  
<span data-ttu-id="c3450-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c3450-107">\<trackingProfile></span></span>  
<span data-ttu-id="c3450-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c3450-108">\<workflow></span></span>  
<span data-ttu-id="c3450-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="c3450-109">\<activityStateQueries></span></span>  
<span data-ttu-id="c3450-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="c3450-110">\<activityStateQuery></span></span>  
<span data-ttu-id="c3450-111">\<variables></span><span class="sxs-lookup"><span data-stu-id="c3450-111">\<variables></span></span>  
<span data-ttu-id="c3450-112">\<variable></span><span class="sxs-lookup"><span data-stu-id="c3450-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3450-113">語法</span><span class="sxs-lookup"><span data-stu-id="c3450-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3450-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c3450-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c3450-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c3450-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3450-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c3450-116">Attributes</span></span>  
  
|<span data-ttu-id="c3450-117">屬性</span><span class="sxs-lookup"><span data-stu-id="c3450-117">Attribute</span></span>|<span data-ttu-id="c3450-118">描述</span><span class="sxs-lookup"><span data-stu-id="c3450-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3450-119">名稱</span><span class="sxs-lookup"><span data-stu-id="c3450-119">name</span></span>|<span data-ttu-id="c3450-120">指定變數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="c3450-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3450-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c3450-121">Child Elements</span></span>  
 <span data-ttu-id="c3450-122">無。</span><span class="sxs-lookup"><span data-stu-id="c3450-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3450-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c3450-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c3450-124">項目</span><span class="sxs-lookup"><span data-stu-id="c3450-124">Element</span></span>|<span data-ttu-id="c3450-125">描述</span><span class="sxs-lookup"><span data-stu-id="c3450-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3450-126">\<variable></span><span class="sxs-lookup"><span data-stu-id="c3450-126">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="c3450-127">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="c3450-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3450-128">備註</span><span class="sxs-lookup"><span data-stu-id="c3450-128">Remarks</span></span>  
 <span data-ttu-id="c3450-129">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="c3450-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="c3450-130">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="c3450-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="c3450-131">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)並[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)項目擷取任何變數或引數從工作流程中的任何活動。</span><span class="sxs-lookup"><span data-stu-id="c3450-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="c3450-132">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="c3450-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="c3450-133">變數和引數只能使用 ActivityStateRecord 擷取，並因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="c3450-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3450-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3450-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c3450-135">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c3450-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c3450-136">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c3450-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
