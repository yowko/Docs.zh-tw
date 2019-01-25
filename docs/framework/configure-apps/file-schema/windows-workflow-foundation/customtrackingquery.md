---
title: '&lt;customTrackingQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9ee5a4a25d379eafb936098597df1ec61ff09f0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725853"
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="40dae-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="40dae-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="40dae-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="40dae-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="40dae-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="40dae-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="40dae-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="40dae-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="40dae-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="40dae-106">\<system.serviceModel></span></span>  
<span data-ttu-id="40dae-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="40dae-107">\<tracking></span></span>  
<span data-ttu-id="40dae-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="40dae-108">\<trackingProfile></span></span>  
<span data-ttu-id="40dae-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="40dae-109">\<workflow></span></span>  
<span data-ttu-id="40dae-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="40dae-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="40dae-111">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="40dae-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40dae-112">語法</span><span class="sxs-lookup"><span data-stu-id="40dae-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40dae-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="40dae-113">Attributes and Elements</span></span>  
 <span data-ttu-id="40dae-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="40dae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40dae-115">屬性</span><span class="sxs-lookup"><span data-stu-id="40dae-115">Attributes</span></span>  
  
|<span data-ttu-id="40dae-116">屬性</span><span class="sxs-lookup"><span data-stu-id="40dae-116">Attribute</span></span>|<span data-ttu-id="40dae-117">描述</span><span class="sxs-lookup"><span data-stu-id="40dae-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40dae-118">activityName</span><span class="sxs-lookup"><span data-stu-id="40dae-118">activityName</span></span>|<span data-ttu-id="40dae-119">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="40dae-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="40dae-120">name</span><span class="sxs-lookup"><span data-stu-id="40dae-120">name</span></span>|<span data-ttu-id="40dae-121">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="40dae-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40dae-122">子元素</span><span class="sxs-lookup"><span data-stu-id="40dae-122">Child Elements</span></span>  
 <span data-ttu-id="40dae-123">無。</span><span class="sxs-lookup"><span data-stu-id="40dae-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40dae-124">父項目</span><span class="sxs-lookup"><span data-stu-id="40dae-124">Parent Elements</span></span>  
  
|<span data-ttu-id="40dae-125">項目</span><span class="sxs-lookup"><span data-stu-id="40dae-125">Element</span></span>|<span data-ttu-id="40dae-126">描述</span><span class="sxs-lookup"><span data-stu-id="40dae-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40dae-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="40dae-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="40dae-128">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="40dae-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40dae-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40dae-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="40dae-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="40dae-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="40dae-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="40dae-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
