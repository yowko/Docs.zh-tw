---
title: "WCF 的 &lt;customTrackingQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a155f435fb61c19a50f1b047c7dd28b603716
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="c3a61-102">WCF 的 &lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c3a61-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="c3a61-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="c3a61-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c3a61-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="c3a61-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="c3a61-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c3a61-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="c3a61-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c3a61-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c3a61-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="c3a61-107">\<tracking></span></span>  
<span data-ttu-id="c3a61-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c3a61-108">\<trackingProfile></span></span>  
<span data-ttu-id="c3a61-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c3a61-109">\<workflow></span></span>  
<span data-ttu-id="c3a61-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="c3a61-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a61-111">語法</span><span class="sxs-lookup"><span data-stu-id="c3a61-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3a61-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c3a61-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c3a61-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c3a61-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3a61-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c3a61-114">Attributes</span></span>  
 <span data-ttu-id="c3a61-115">無。</span><span class="sxs-lookup"><span data-stu-id="c3a61-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3a61-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c3a61-116">Child Elements</span></span>  
  
|<span data-ttu-id="c3a61-117">項目</span><span class="sxs-lookup"><span data-stu-id="c3a61-117">Element</span></span>|<span data-ttu-id="c3a61-118">描述</span><span class="sxs-lookup"><span data-stu-id="c3a61-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3a61-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="c3a61-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="c3a61-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="c3a61-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3a61-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c3a61-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c3a61-122">項目</span><span class="sxs-lookup"><span data-stu-id="c3a61-122">Element</span></span>|<span data-ttu-id="c3a61-123">描述</span><span class="sxs-lookup"><span data-stu-id="c3a61-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3a61-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="c3a61-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c3a61-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="c3a61-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3a61-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3a61-126">See Also</span></span>  
 <span data-ttu-id="c3a61-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c3a61-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c3a61-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c3a61-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="c3a61-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="c3a61-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c3a61-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="c3a61-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
