---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: bb7ae702209df3c0297ec2cfac6b09ee47ad9558
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946134"
---
# <a name="arguments"></a><span data-ttu-id="4e97e-101">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="4e97e-101">\<arguments></span></span>
<span data-ttu-id="4e97e-102">表示與某個活動狀態查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="4e97e-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="4e97e-103">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4e97e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4e97e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4e97e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4e97e-105">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="4e97e-105">\<tracking></span></span>  
<span data-ttu-id="4e97e-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4e97e-106">\<trackingProfile></span></span>  
<span data-ttu-id="4e97e-107">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="4e97e-107">\<workflow></span></span>  
<span data-ttu-id="4e97e-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="4e97e-108">\<activityStateQueries></span></span>  
<span data-ttu-id="4e97e-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4e97e-109">\<activityStateQuery></span></span>  
<span data-ttu-id="4e97e-110">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="4e97e-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e97e-111">語法</span><span class="sxs-lookup"><span data-stu-id="4e97e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e97e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e97e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4e97e-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e97e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e97e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="4e97e-114">Attributes</span></span>  
 <span data-ttu-id="4e97e-115">無。</span><span class="sxs-lookup"><span data-stu-id="4e97e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e97e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="4e97e-116">Child Elements</span></span>  
  
|<span data-ttu-id="4e97e-117">項目</span><span class="sxs-lookup"><span data-stu-id="4e97e-117">Element</span></span>|<span data-ttu-id="4e97e-118">說明</span><span class="sxs-lookup"><span data-stu-id="4e97e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e97e-119">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="4e97e-119">\<argument></span></span>](argument.md)|<span data-ttu-id="4e97e-120">與活動狀態查詢相關聯的引數。</span><span class="sxs-lookup"><span data-stu-id="4e97e-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e97e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="4e97e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4e97e-122">項目</span><span class="sxs-lookup"><span data-stu-id="4e97e-122">Element</span></span>|<span data-ttu-id="4e97e-123">說明</span><span class="sxs-lookup"><span data-stu-id="4e97e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e97e-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4e97e-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="4e97e-125">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="4e97e-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4e97e-126">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="4e97e-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e97e-127">備註</span><span class="sxs-lookup"><span data-stu-id="4e97e-127">Remarks</span></span>  
 <span data-ttu-id="4e97e-128">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="4e97e-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4e97e-129">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="4e97e-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4e97e-130">您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素, 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="4e97e-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4e97e-131">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="4e97e-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4e97e-132">只能使用 ActivityStateRecord 來解壓縮變數和引數, 因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="4e97e-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e97e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e97e-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4e97e-134">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="4e97e-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4e97e-135">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4e97e-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
