---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 4663ccedcafb6b151de75568afd3743c83c75224
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189821"
---
# \<activityStateQueries>

<span data-ttu-id="a6b39-101">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a6b39-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a6b39-102">例如，您可能想要追蹤每次在工作流程實例中完成「傳送電子郵件」活動。</span><span class="sxs-lookup"><span data-stu-id="a6b39-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a6b39-103">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a6b39-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a6b39-104">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="a6b39-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="a6b39-105">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a6b39-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="a6b39-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6b39-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6b39-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6b39-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a6b39-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a6b39-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6b39-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a6b39-109">Attributes</span></span>  

 <span data-ttu-id="a6b39-110">無。</span><span class="sxs-lookup"><span data-stu-id="a6b39-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6b39-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a6b39-111">Child Elements</span></span>  
  
|<span data-ttu-id="a6b39-112">項目</span><span class="sxs-lookup"><span data-stu-id="a6b39-112">Element</span></span>|<span data-ttu-id="a6b39-113">描述</span><span class="sxs-lookup"><span data-stu-id="a6b39-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="a6b39-114">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="a6b39-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a6b39-115">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a6b39-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6b39-116">父項目</span><span class="sxs-lookup"><span data-stu-id="a6b39-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a6b39-117">項目</span><span class="sxs-lookup"><span data-stu-id="a6b39-117">Element</span></span>|<span data-ttu-id="a6b39-118">描述</span><span class="sxs-lookup"><span data-stu-id="a6b39-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="a6b39-119">設定元素，其中包含 **activityDefinitionId** 屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="a6b39-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6b39-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6b39-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a6b39-121">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="a6b39-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a6b39-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a6b39-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
