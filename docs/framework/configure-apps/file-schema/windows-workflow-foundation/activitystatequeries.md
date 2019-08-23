---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 6e91078a24a950c6de027d57e3883e38f19447d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945446"
---
# <a name="activitystatequeries"></a><span data-ttu-id="a908d-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="a908d-101">\<activityStateQueries></span></span>
<span data-ttu-id="a908d-102">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a908d-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a908d-103">例如, 您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="a908d-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a908d-104">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a908d-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a908d-105">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="a908d-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="a908d-106">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a908d-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a908d-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a908d-107">\<system.serviceModel></span></span>  
<span data-ttu-id="a908d-108">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="a908d-108">\<tracking></span></span>  
<span data-ttu-id="a908d-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a908d-109">\<trackingProfile></span></span>  
<span data-ttu-id="a908d-110">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="a908d-110">\<workflow></span></span>  
<span data-ttu-id="a908d-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="a908d-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a908d-112">語法</span><span class="sxs-lookup"><span data-stu-id="a908d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a908d-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a908d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a908d-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a908d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a908d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="a908d-115">Attributes</span></span>  
 <span data-ttu-id="a908d-116">無。</span><span class="sxs-lookup"><span data-stu-id="a908d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a908d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a908d-117">Child Elements</span></span>  
  
|<span data-ttu-id="a908d-118">項目</span><span class="sxs-lookup"><span data-stu-id="a908d-118">Element</span></span>|<span data-ttu-id="a908d-119">描述</span><span class="sxs-lookup"><span data-stu-id="a908d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a908d-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="a908d-120">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="a908d-121">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="a908d-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a908d-122">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a908d-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a908d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a908d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a908d-124">項目</span><span class="sxs-lookup"><span data-stu-id="a908d-124">Element</span></span>|<span data-ttu-id="a908d-125">說明</span><span class="sxs-lookup"><span data-stu-id="a908d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a908d-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a908d-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="a908d-127">Configuration 元素, 其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="a908d-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a908d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a908d-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a908d-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a908d-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a908d-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a908d-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
