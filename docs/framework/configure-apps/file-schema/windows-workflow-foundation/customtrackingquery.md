---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 92060260075017359d8a5f0500d52e52c2217d3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076649"
---
# <a name="customtrackingquery"></a><span data-ttu-id="53fe0-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="53fe0-101">\<customTrackingQuery></span></span>
<span data-ttu-id="53fe0-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="53fe0-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="53fe0-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="53fe0-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="53fe0-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="53fe0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="53fe0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="53fe0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="53fe0-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="53fe0-106">\<tracking></span></span>  
<span data-ttu-id="53fe0-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="53fe0-107">\<trackingProfile></span></span>  
<span data-ttu-id="53fe0-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="53fe0-108">\<workflow></span></span>  
<span data-ttu-id="53fe0-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="53fe0-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="53fe0-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="53fe0-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fe0-111">語法</span><span class="sxs-lookup"><span data-stu-id="53fe0-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53fe0-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53fe0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="53fe0-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="53fe0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53fe0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="53fe0-114">Attributes</span></span>  
  
|<span data-ttu-id="53fe0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="53fe0-115">Attribute</span></span>|<span data-ttu-id="53fe0-116">描述</span><span class="sxs-lookup"><span data-stu-id="53fe0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53fe0-117">activityName</span><span class="sxs-lookup"><span data-stu-id="53fe0-117">activityName</span></span>|<span data-ttu-id="53fe0-118">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="53fe0-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="53fe0-119">名稱</span><span class="sxs-lookup"><span data-stu-id="53fe0-119">name</span></span>|<span data-ttu-id="53fe0-120">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="53fe0-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53fe0-121">子元素</span><span class="sxs-lookup"><span data-stu-id="53fe0-121">Child Elements</span></span>  
 <span data-ttu-id="53fe0-122">無。</span><span class="sxs-lookup"><span data-stu-id="53fe0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53fe0-123">父項目</span><span class="sxs-lookup"><span data-stu-id="53fe0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="53fe0-124">項目</span><span class="sxs-lookup"><span data-stu-id="53fe0-124">Element</span></span>|<span data-ttu-id="53fe0-125">描述</span><span class="sxs-lookup"><span data-stu-id="53fe0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53fe0-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="53fe0-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="53fe0-127">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="53fe0-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53fe0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53fe0-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="53fe0-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="53fe0-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="53fe0-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="53fe0-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
