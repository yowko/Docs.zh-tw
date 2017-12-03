---
title: '&lt;customTrackingQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 908c340167d50d4d16e0eeff7cc2e01290b55e7a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="53626-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="53626-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="53626-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="53626-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="53626-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="53626-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="53626-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="53626-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="53626-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="53626-106">\<system.serviceModel></span></span>  
<span data-ttu-id="53626-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="53626-107">\<tracking></span></span>  
<span data-ttu-id="53626-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="53626-108">\<trackingProfile></span></span>  
<span data-ttu-id="53626-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="53626-109">\<workflow></span></span>  
<span data-ttu-id="53626-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="53626-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="53626-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="53626-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53626-112">語法</span><span class="sxs-lookup"><span data-stu-id="53626-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53626-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53626-113">Attributes and Elements</span></span>  
 <span data-ttu-id="53626-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="53626-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53626-115">屬性</span><span class="sxs-lookup"><span data-stu-id="53626-115">Attributes</span></span>  
  
|<span data-ttu-id="53626-116">屬性</span><span class="sxs-lookup"><span data-stu-id="53626-116">Attribute</span></span>|<span data-ttu-id="53626-117">描述</span><span class="sxs-lookup"><span data-stu-id="53626-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53626-118">activityName</span><span class="sxs-lookup"><span data-stu-id="53626-118">activityName</span></span>|<span data-ttu-id="53626-119">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="53626-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="53626-120">name</span><span class="sxs-lookup"><span data-stu-id="53626-120">name</span></span>|<span data-ttu-id="53626-121">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="53626-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53626-122">子元素</span><span class="sxs-lookup"><span data-stu-id="53626-122">Child Elements</span></span>  
 <span data-ttu-id="53626-123">無。</span><span class="sxs-lookup"><span data-stu-id="53626-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53626-124">父項目</span><span class="sxs-lookup"><span data-stu-id="53626-124">Parent Elements</span></span>  
  
|<span data-ttu-id="53626-125">項目</span><span class="sxs-lookup"><span data-stu-id="53626-125">Element</span></span>|<span data-ttu-id="53626-126">說明</span><span class="sxs-lookup"><span data-stu-id="53626-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53626-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="53626-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="53626-128">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="53626-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53626-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53626-129">See Also</span></span>  
 <span data-ttu-id="53626-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="53626-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="53626-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="53626-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="53626-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="53626-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="53626-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="53626-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
