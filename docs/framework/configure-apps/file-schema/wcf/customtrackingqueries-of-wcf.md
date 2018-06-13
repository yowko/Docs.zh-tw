---
title: WCF 的 &lt;customTrackingQueries&gt;
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 11ad4281d2925a48508c6a3e8258b0b1cd49a326
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749682"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="ab6a4-102">WCF 的 &lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="ab6a4-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="ab6a4-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="ab6a4-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ab6a4-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ab6a4-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ab6a4-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ab6a4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="ab6a4-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ab6a4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ab6a4-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="ab6a4-107">\<tracking></span></span>  
<span data-ttu-id="ab6a4-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ab6a4-108">\<trackingProfile></span></span>  
<span data-ttu-id="ab6a4-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ab6a4-109">\<workflow></span></span>  
<span data-ttu-id="ab6a4-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ab6a4-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab6a4-111">語法</span><span class="sxs-lookup"><span data-stu-id="ab6a4-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab6a4-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab6a4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ab6a4-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ab6a4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab6a4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ab6a4-114">Attributes</span></span>  
 <span data-ttu-id="ab6a4-115">無。</span><span class="sxs-lookup"><span data-stu-id="ab6a4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab6a4-116">子項目</span><span class="sxs-lookup"><span data-stu-id="ab6a4-116">Child Elements</span></span>  
  
|<span data-ttu-id="ab6a4-117">項目</span><span class="sxs-lookup"><span data-stu-id="ab6a4-117">Element</span></span>|<span data-ttu-id="ab6a4-118">描述</span><span class="sxs-lookup"><span data-stu-id="ab6a4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab6a4-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="ab6a4-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="ab6a4-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="ab6a4-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab6a4-121">父項目</span><span class="sxs-lookup"><span data-stu-id="ab6a4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ab6a4-122">項目</span><span class="sxs-lookup"><span data-stu-id="ab6a4-122">Element</span></span>|<span data-ttu-id="ab6a4-123">描述</span><span class="sxs-lookup"><span data-stu-id="ab6a4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab6a4-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="ab6a4-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ab6a4-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="ab6a4-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab6a4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab6a4-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="ab6a4-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="ab6a4-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ab6a4-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ab6a4-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
