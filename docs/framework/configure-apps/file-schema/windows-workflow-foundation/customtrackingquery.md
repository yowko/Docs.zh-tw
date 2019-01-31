---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 4e525bc4c77649a6c6d70ddb2408b6ecce4a0f09
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263757"
---
# <a name="customtrackingquery"></a><span data-ttu-id="eca37-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="eca37-101">\<customTrackingQuery></span></span>
<span data-ttu-id="eca37-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="eca37-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="eca37-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="eca37-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="eca37-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="eca37-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="eca37-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eca37-105">\<system.serviceModel></span></span>  
<span data-ttu-id="eca37-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="eca37-106">\<tracking></span></span>  
<span data-ttu-id="eca37-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eca37-107">\<trackingProfile></span></span>  
<span data-ttu-id="eca37-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="eca37-108">\<workflow></span></span>  
<span data-ttu-id="eca37-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="eca37-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="eca37-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="eca37-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca37-111">語法</span><span class="sxs-lookup"><span data-stu-id="eca37-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eca37-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eca37-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eca37-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="eca37-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eca37-114">屬性</span><span class="sxs-lookup"><span data-stu-id="eca37-114">Attributes</span></span>  
  
|<span data-ttu-id="eca37-115">屬性</span><span class="sxs-lookup"><span data-stu-id="eca37-115">Attribute</span></span>|<span data-ttu-id="eca37-116">描述</span><span class="sxs-lookup"><span data-stu-id="eca37-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eca37-117">activityName</span><span class="sxs-lookup"><span data-stu-id="eca37-117">activityName</span></span>|<span data-ttu-id="eca37-118">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="eca37-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="eca37-119">name</span><span class="sxs-lookup"><span data-stu-id="eca37-119">name</span></span>|<span data-ttu-id="eca37-120">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="eca37-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eca37-121">子元素</span><span class="sxs-lookup"><span data-stu-id="eca37-121">Child Elements</span></span>  
 <span data-ttu-id="eca37-122">無。</span><span class="sxs-lookup"><span data-stu-id="eca37-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eca37-123">父項目</span><span class="sxs-lookup"><span data-stu-id="eca37-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eca37-124">項目</span><span class="sxs-lookup"><span data-stu-id="eca37-124">Element</span></span>|<span data-ttu-id="eca37-125">描述</span><span class="sxs-lookup"><span data-stu-id="eca37-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eca37-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="eca37-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="eca37-127">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="eca37-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eca37-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eca37-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="eca37-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="eca37-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="eca37-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="eca37-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
