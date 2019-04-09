---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 90acda7277fd276f43a619a014fbce103261aa1e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112225"
---
# <a name="activitystatequeries"></a><span data-ttu-id="b4aa1-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b4aa1-101">\<activityStateQueries></span></span>
<span data-ttu-id="b4aa1-102">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b4aa1-103">例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b4aa1-104">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="b4aa1-105">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="b4aa1-106">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b4aa1-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b4aa1-107">\<system.serviceModel></span></span>  
<span data-ttu-id="b4aa1-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b4aa1-108">\<tracking></span></span>  
<span data-ttu-id="b4aa1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b4aa1-109">\<trackingProfile></span></span>  
<span data-ttu-id="b4aa1-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b4aa1-110">\<workflow></span></span>  
<span data-ttu-id="b4aa1-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b4aa1-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4aa1-112">語法</span><span class="sxs-lookup"><span data-stu-id="b4aa1-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4aa1-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b4aa1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b4aa1-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4aa1-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b4aa1-115">Attributes</span></span>  
 <span data-ttu-id="b4aa1-116">無。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4aa1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="b4aa1-117">Child Elements</span></span>  
  
|<span data-ttu-id="b4aa1-118">項目</span><span class="sxs-lookup"><span data-stu-id="b4aa1-118">Element</span></span>|<span data-ttu-id="b4aa1-119">描述</span><span class="sxs-lookup"><span data-stu-id="b4aa1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4aa1-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b4aa1-120">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="b4aa1-121">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b4aa1-122">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4aa1-123">父項目</span><span class="sxs-lookup"><span data-stu-id="b4aa1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b4aa1-124">項目</span><span class="sxs-lookup"><span data-stu-id="b4aa1-124">Element</span></span>|<span data-ttu-id="b4aa1-125">描述</span><span class="sxs-lookup"><span data-stu-id="b4aa1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4aa1-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b4aa1-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b4aa1-127">包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。</span><span class="sxs-lookup"><span data-stu-id="b4aa1-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4aa1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4aa1-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b4aa1-129">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="b4aa1-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b4aa1-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="b4aa1-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
