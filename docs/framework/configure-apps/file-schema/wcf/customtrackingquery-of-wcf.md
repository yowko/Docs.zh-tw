---
title: WCF 的 &lt;customTrackingQuery&gt;
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 234703e677f838dcdccdf857ba38b8729d25a488
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146377"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="bc2e2-102">WCF 的 &lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="bc2e2-102">&lt;customTrackingQuery&gt; of WCF</span></span>

<span data-ttu-id="bc2e2-103">表示用來追蹤您在程式碼活動中定義的事件的查詢。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="bc2e2-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="bc2e2-105">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bc2e2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bc2e2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bc2e2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bc2e2-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="bc2e2-107">\<tracking></span></span>  
<span data-ttu-id="bc2e2-108">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="bc2e2-108">\<profiles></span></span>  
<span data-ttu-id="bc2e2-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bc2e2-109">\<trackingProfile></span></span>  
<span data-ttu-id="bc2e2-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="bc2e2-110">\<workflow></span></span>  
<span data-ttu-id="bc2e2-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="bc2e2-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="bc2e2-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="bc2e2-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2e2-113">語法</span><span class="sxs-lookup"><span data-stu-id="bc2e2-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc2e2-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="bc2e2-114">Attributes and elements</span></span>  

<span data-ttu-id="bc2e2-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc2e2-116">屬性</span><span class="sxs-lookup"><span data-stu-id="bc2e2-116">Attributes</span></span>  
  
|<span data-ttu-id="bc2e2-117">屬性</span><span class="sxs-lookup"><span data-stu-id="bc2e2-117">Attribute</span></span>|<span data-ttu-id="bc2e2-118">描述</span><span class="sxs-lookup"><span data-stu-id="bc2e2-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="bc2e2-119">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="bc2e2-120">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc2e2-121">子元素</span><span class="sxs-lookup"><span data-stu-id="bc2e2-121">Child elements</span></span>

<span data-ttu-id="bc2e2-122">無。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bc2e2-123">父元素</span><span class="sxs-lookup"><span data-stu-id="bc2e2-123">Parent elements</span></span>

|<span data-ttu-id="bc2e2-124">元素</span><span class="sxs-lookup"><span data-stu-id="bc2e2-124">Element</span></span>|<span data-ttu-id="bc2e2-125">描述</span><span class="sxs-lookup"><span data-stu-id="bc2e2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc2e2-126">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="bc2e2-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="bc2e2-127">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="bc2e2-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="bc2e2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc2e2-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bc2e2-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="bc2e2-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bc2e2-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="bc2e2-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
