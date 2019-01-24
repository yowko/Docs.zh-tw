---
title: WCF 的 &lt;activityStateQueries&gt;
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 6b21ad3f5487a924309b8bee6b9ac972f23bdc66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701933"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="704df-102">WCF 的 &lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="704df-102">&lt;activityStateQueries&gt; of WCF</span></span>

<span data-ttu-id="704df-103">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="704df-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="704df-104">例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。</span><span class="sxs-lookup"><span data-stu-id="704df-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="704df-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="704df-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="704df-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="704df-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="704df-107">如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="704df-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="704df-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="704df-108">\<system.serviceModel></span></span>  
<span data-ttu-id="704df-109">\<tracking></span><span class="sxs-lookup"><span data-stu-id="704df-109">\<tracking></span></span>  
<span data-ttu-id="704df-110">\<設定檔 ></span><span class="sxs-lookup"><span data-stu-id="704df-110">\<profiles></span></span>  
<span data-ttu-id="704df-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="704df-111">\<trackingProfile></span></span>  
<span data-ttu-id="704df-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="704df-112">\<workflow></span></span>  
<span data-ttu-id="704df-113">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="704df-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="704df-114">語法</span><span class="sxs-lookup"><span data-stu-id="704df-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="704df-115">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="704df-115">Attributes and elements</span></span>

<span data-ttu-id="704df-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="704df-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="704df-117">屬性</span><span class="sxs-lookup"><span data-stu-id="704df-117">Attributes</span></span>  

<span data-ttu-id="704df-118">無。</span><span class="sxs-lookup"><span data-stu-id="704df-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="704df-119">子元素</span><span class="sxs-lookup"><span data-stu-id="704df-119">Child elements</span></span>

|<span data-ttu-id="704df-120">項目</span><span class="sxs-lookup"><span data-stu-id="704df-120">Element</span></span>|<span data-ttu-id="704df-121">描述</span><span class="sxs-lookup"><span data-stu-id="704df-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="704df-122">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="704df-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="704df-123">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="704df-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="704df-124">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="704df-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="704df-125">父元素</span><span class="sxs-lookup"><span data-stu-id="704df-125">Parent elements</span></span>

|<span data-ttu-id="704df-126">元素</span><span class="sxs-lookup"><span data-stu-id="704df-126">Element</span></span>|<span data-ttu-id="704df-127">描述</span><span class="sxs-lookup"><span data-stu-id="704df-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="704df-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="704df-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="704df-129">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="704df-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="704df-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704df-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="704df-131">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="704df-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="704df-132">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="704df-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
