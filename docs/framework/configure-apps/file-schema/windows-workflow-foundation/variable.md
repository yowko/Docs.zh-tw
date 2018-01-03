---
title: "&lt;變數&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 971e3e366c2383828dde8e8f152660fb39c886ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltvariablegt"></a><span data-ttu-id="733a7-102">&lt;變數&gt;</span><span class="sxs-lookup"><span data-stu-id="733a7-102">&lt;variable&gt;</span></span>
<span data-ttu-id="733a7-103">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="733a7-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="733a7-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="733a7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="733a7-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="733a7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="733a7-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="733a7-106">\<tracking></span></span>  
<span data-ttu-id="733a7-107">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="733a7-107">\<profiles></span></span>  
<span data-ttu-id="733a7-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="733a7-108">\<trackingProfile></span></span>  
<span data-ttu-id="733a7-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="733a7-109">\<workflow></span></span>  
<span data-ttu-id="733a7-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="733a7-110">\<activityStateQueries></span></span>  
<span data-ttu-id="733a7-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="733a7-111">\<activityStateQuery></span></span>  
<span data-ttu-id="733a7-112">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="733a7-112">\<variables></span></span>  
<span data-ttu-id="733a7-113">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="733a7-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733a7-114">語法</span><span class="sxs-lookup"><span data-stu-id="733a7-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="733a7-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="733a7-115">Attributes and Elements</span></span>  
 <span data-ttu-id="733a7-116">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="733a7-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="733a7-117">屬性</span><span class="sxs-lookup"><span data-stu-id="733a7-117">Attributes</span></span>  
  
|<span data-ttu-id="733a7-118">屬性</span><span class="sxs-lookup"><span data-stu-id="733a7-118">Attribute</span></span>|<span data-ttu-id="733a7-119">描述</span><span class="sxs-lookup"><span data-stu-id="733a7-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="733a7-120">name</span><span class="sxs-lookup"><span data-stu-id="733a7-120">name</span></span>|<span data-ttu-id="733a7-121">指定變數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="733a7-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="733a7-122">子元素</span><span class="sxs-lookup"><span data-stu-id="733a7-122">Child Elements</span></span>  
 <span data-ttu-id="733a7-123">無。</span><span class="sxs-lookup"><span data-stu-id="733a7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="733a7-124">父項目</span><span class="sxs-lookup"><span data-stu-id="733a7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="733a7-125">項目</span><span class="sxs-lookup"><span data-stu-id="733a7-125">Element</span></span>|<span data-ttu-id="733a7-126">描述</span><span class="sxs-lookup"><span data-stu-id="733a7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="733a7-127">\<變數 ></span><span class="sxs-lookup"><span data-stu-id="733a7-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="733a7-128">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="733a7-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="733a7-129">備註</span><span class="sxs-lookup"><span data-stu-id="733a7-129">Remarks</span></span>  
 <span data-ttu-id="733a7-130">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="733a7-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="733a7-131">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="733a7-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="733a7-132">您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="733a7-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="733a7-133">變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="733a7-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="733a7-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="733a7-134">See Also</span></span>  
 <span data-ttu-id="733a7-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="733a7-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="733a7-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="733a7-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="733a7-137">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="733a7-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="733a7-138">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="733a7-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
