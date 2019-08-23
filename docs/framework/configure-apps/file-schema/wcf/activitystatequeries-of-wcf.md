---
title: <activityStateQueries>WCF 的
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 415cd4a75ecab725f91bcd298f8a7966ea6079d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920303"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="e9b46-102">\<WCF 的 Q s ></span><span class="sxs-lookup"><span data-stu-id="e9b46-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="e9b46-103">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9b46-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="e9b46-104">例如, 您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="e9b46-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="e9b46-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="e9b46-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="e9b46-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="e9b46-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="e9b46-107">如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e9b46-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="e9b46-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9b46-108">\<system.serviceModel></span></span>  
<span data-ttu-id="e9b46-109">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="e9b46-109">\<tracking></span></span>  
<span data-ttu-id="e9b46-110">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="e9b46-110">\<profiles></span></span>  
<span data-ttu-id="e9b46-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e9b46-111">\<trackingProfile></span></span>  
<span data-ttu-id="e9b46-112">\<工作流程 ></span><span class="sxs-lookup"><span data-stu-id="e9b46-112">\<workflow></span></span>  
<span data-ttu-id="e9b46-113">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="e9b46-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="e9b46-114">語法</span><span class="sxs-lookup"><span data-stu-id="e9b46-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="e9b46-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e9b46-115">Attributes and elements</span></span>

<span data-ttu-id="e9b46-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e9b46-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e9b46-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e9b46-117">Attributes</span></span>  

<span data-ttu-id="e9b46-118">無。</span><span class="sxs-lookup"><span data-stu-id="e9b46-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="e9b46-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e9b46-119">Child elements</span></span>

|<span data-ttu-id="e9b46-120">項目</span><span class="sxs-lookup"><span data-stu-id="e9b46-120">Element</span></span>|<span data-ttu-id="e9b46-121">說明</span><span class="sxs-lookup"><span data-stu-id="e9b46-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9b46-122">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="e9b46-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="e9b46-123">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="e9b46-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e9b46-124">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="e9b46-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e9b46-125">父元素</span><span class="sxs-lookup"><span data-stu-id="e9b46-125">Parent elements</span></span>

|<span data-ttu-id="e9b46-126">元素</span><span class="sxs-lookup"><span data-stu-id="e9b46-126">Element</span></span>|<span data-ttu-id="e9b46-127">描述</span><span class="sxs-lookup"><span data-stu-id="e9b46-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9b46-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e9b46-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e9b46-129">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="e9b46-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e9b46-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9b46-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="e9b46-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="e9b46-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e9b46-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e9b46-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
