---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84c9635b37c592b4d82635deb58880d81d2fb5cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="91545-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="91545-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="91545-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="91545-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="91545-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="91545-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="91545-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="91545-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="91545-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="91545-106">\<system.serviceModel></span></span>  
<span data-ttu-id="91545-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="91545-107">\<tracking></span></span>  
<span data-ttu-id="91545-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="91545-108">\<trackingProfile></span></span>  
<span data-ttu-id="91545-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="91545-109">\<workflow></span></span>  
<span data-ttu-id="91545-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="91545-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91545-111">語法</span><span class="sxs-lookup"><span data-stu-id="91545-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91545-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="91545-112">Attributes and Elements</span></span>  
 <span data-ttu-id="91545-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="91545-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91545-114">屬性</span><span class="sxs-lookup"><span data-stu-id="91545-114">Attributes</span></span>  
 <span data-ttu-id="91545-115">無。</span><span class="sxs-lookup"><span data-stu-id="91545-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91545-116">子元素</span><span class="sxs-lookup"><span data-stu-id="91545-116">Child Elements</span></span>  
  
|<span data-ttu-id="91545-117">項目</span><span class="sxs-lookup"><span data-stu-id="91545-117">Element</span></span>|<span data-ttu-id="91545-118">描述</span><span class="sxs-lookup"><span data-stu-id="91545-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91545-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="91545-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="91545-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="91545-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91545-121">父項目</span><span class="sxs-lookup"><span data-stu-id="91545-121">Parent Elements</span></span>  
  
|<span data-ttu-id="91545-122">項目</span><span class="sxs-lookup"><span data-stu-id="91545-122">Element</span></span>|<span data-ttu-id="91545-123">描述</span><span class="sxs-lookup"><span data-stu-id="91545-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91545-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="91545-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="91545-125">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="91545-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91545-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="91545-126">See Also</span></span>  
 <span data-ttu-id="91545-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="91545-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="91545-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="91545-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="91545-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="91545-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="91545-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="91545-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
