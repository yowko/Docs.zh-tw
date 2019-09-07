---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398948"
---
# <a name="activitystatequeries"></a><span data-ttu-id="85506-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="85506-101">\<activityStateQueries></span></span>
<span data-ttu-id="85506-102">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="85506-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="85506-103">例如，您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="85506-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="85506-104">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="85506-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="85506-105">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="85506-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="85506-106">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="85506-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="85506-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85506-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85506-108">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="85506-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="85506-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="85506-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="85506-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="85506-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="85506-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="85506-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="85506-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Q s >**</span><span class="sxs-lookup"><span data-stu-id="85506-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85506-113">語法</span><span class="sxs-lookup"><span data-stu-id="85506-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85506-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85506-114">Attributes and Elements</span></span>  
 <span data-ttu-id="85506-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="85506-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85506-116">屬性</span><span class="sxs-lookup"><span data-stu-id="85506-116">Attributes</span></span>  
 <span data-ttu-id="85506-117">無。</span><span class="sxs-lookup"><span data-stu-id="85506-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85506-118">子元素</span><span class="sxs-lookup"><span data-stu-id="85506-118">Child Elements</span></span>  
  
|<span data-ttu-id="85506-119">項目</span><span class="sxs-lookup"><span data-stu-id="85506-119">Element</span></span>|<span data-ttu-id="85506-120">描述</span><span class="sxs-lookup"><span data-stu-id="85506-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85506-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="85506-121">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="85506-122">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="85506-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="85506-123">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="85506-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85506-124">父項目</span><span class="sxs-lookup"><span data-stu-id="85506-124">Parent Elements</span></span>  
  
|<span data-ttu-id="85506-125">項目</span><span class="sxs-lookup"><span data-stu-id="85506-125">Element</span></span>|<span data-ttu-id="85506-126">描述</span><span class="sxs-lookup"><span data-stu-id="85506-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85506-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="85506-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="85506-128">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="85506-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85506-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85506-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="85506-130">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="85506-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="85506-131">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="85506-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
