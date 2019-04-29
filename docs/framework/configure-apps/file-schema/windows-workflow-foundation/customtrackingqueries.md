---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790217"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="2c8f4-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="2c8f4-101">\<customTrackingQueries></span></span>
<span data-ttu-id="2c8f4-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="2c8f4-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="2c8f4-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="2c8f4-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="2c8f4-104">如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2c8f4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2c8f4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c8f4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2c8f4-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="2c8f4-106">\<tracking></span></span>  
<span data-ttu-id="2c8f4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2c8f4-107">\<trackingProfile></span></span>  
<span data-ttu-id="2c8f4-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="2c8f4-108">\<workflow></span></span>  
<span data-ttu-id="2c8f4-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="2c8f4-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c8f4-110">語法</span><span class="sxs-lookup"><span data-stu-id="2c8f4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c8f4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c8f4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2c8f4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2c8f4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c8f4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2c8f4-113">Attributes</span></span>  
 <span data-ttu-id="2c8f4-114">無。</span><span class="sxs-lookup"><span data-stu-id="2c8f4-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c8f4-115">子元素</span><span class="sxs-lookup"><span data-stu-id="2c8f4-115">Child Elements</span></span>  
  
|<span data-ttu-id="2c8f4-116">項目</span><span class="sxs-lookup"><span data-stu-id="2c8f4-116">Element</span></span>|<span data-ttu-id="2c8f4-117">描述</span><span class="sxs-lookup"><span data-stu-id="2c8f4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c8f4-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="2c8f4-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="2c8f4-119">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="2c8f4-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c8f4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2c8f4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2c8f4-121">項目</span><span class="sxs-lookup"><span data-stu-id="2c8f4-121">Element</span></span>|<span data-ttu-id="2c8f4-122">描述</span><span class="sxs-lookup"><span data-stu-id="2c8f4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c8f4-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="2c8f4-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="2c8f4-124">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="2c8f4-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c8f4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c8f4-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2c8f4-126">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2c8f4-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2c8f4-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2c8f4-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
