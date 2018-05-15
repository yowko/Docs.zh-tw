---
title: WCF 的 &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 24970d0fa810db13423fa4c0fc37a4531feeb550
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="32138-102">WCF 的 &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="32138-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="32138-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="32138-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="32138-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="32138-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="32138-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="32138-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="32138-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32138-106">\<system.serviceModel></span></span>  
<span data-ttu-id="32138-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="32138-107">\<tracking></span></span>  
<span data-ttu-id="32138-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="32138-108">\<trackingProfile></span></span>  
<span data-ttu-id="32138-109">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="32138-109">\<workflow></span></span>  
<span data-ttu-id="32138-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="32138-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32138-111">語法</span><span class="sxs-lookup"><span data-stu-id="32138-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32138-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32138-112">Attributes and Elements</span></span>  
 <span data-ttu-id="32138-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="32138-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32138-114">屬性</span><span class="sxs-lookup"><span data-stu-id="32138-114">Attributes</span></span>  
 <span data-ttu-id="32138-115">無。</span><span class="sxs-lookup"><span data-stu-id="32138-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32138-116">子項目</span><span class="sxs-lookup"><span data-stu-id="32138-116">Child Elements</span></span>  
  
|<span data-ttu-id="32138-117">項目</span><span class="sxs-lookup"><span data-stu-id="32138-117">Element</span></span>|<span data-ttu-id="32138-118">描述</span><span class="sxs-lookup"><span data-stu-id="32138-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32138-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="32138-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="32138-120">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="32138-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32138-121">父項目</span><span class="sxs-lookup"><span data-stu-id="32138-121">Parent Elements</span></span>  
  
|<span data-ttu-id="32138-122">項目</span><span class="sxs-lookup"><span data-stu-id="32138-122">Element</span></span>|<span data-ttu-id="32138-123">描述</span><span class="sxs-lookup"><span data-stu-id="32138-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32138-124">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="32138-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="32138-125">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="32138-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32138-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32138-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="32138-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="32138-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="32138-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="32138-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
