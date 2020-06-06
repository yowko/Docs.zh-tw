---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 5d3c35589330ab5bed5f89c0dafac006b9e3af55
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398943"
---
# \<activityStateQuery>
<span data-ttu-id="96e9b-101">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="96e9b-101">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="96e9b-102">例如，您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="96e9b-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="96e9b-103">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="96e9b-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="96e9b-104">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="96e9b-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="96e9b-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="96e9b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="96e9b-106">語法</span><span class="sxs-lookup"><span data-stu-id="96e9b-106">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96e9b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96e9b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="96e9b-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="96e9b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96e9b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="96e9b-109">Attributes</span></span>  
  
|<span data-ttu-id="96e9b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="96e9b-110">Attribute</span></span>|<span data-ttu-id="96e9b-111">描述</span><span class="sxs-lookup"><span data-stu-id="96e9b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96e9b-112">activityName</span><span class="sxs-lookup"><span data-stu-id="96e9b-112">activityName</span></span>|<span data-ttu-id="96e9b-113">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="96e9b-113">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96e9b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="96e9b-114">Child Elements</span></span>  
  
|<span data-ttu-id="96e9b-115">元素</span><span class="sxs-lookup"><span data-stu-id="96e9b-115">Element</span></span>|<span data-ttu-id="96e9b-116">描述</span><span class="sxs-lookup"><span data-stu-id="96e9b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="96e9b-117">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="96e9b-117">A collection of arguments associated with this activity query.</span></span>|  
|[\<states>](states.md)|<span data-ttu-id="96e9b-118">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="96e9b-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[\<states>](states.md)|<span data-ttu-id="96e9b-119">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="96e9b-119">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96e9b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="96e9b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="96e9b-121">元素</span><span class="sxs-lookup"><span data-stu-id="96e9b-121">Element</span></span>|<span data-ttu-id="96e9b-122">描述</span><span class="sxs-lookup"><span data-stu-id="96e9b-122">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="96e9b-123">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="96e9b-123">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="96e9b-124">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="96e9b-124">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96e9b-125">備註</span><span class="sxs-lookup"><span data-stu-id="96e9b-125">Remarks</span></span>  
 <span data-ttu-id="96e9b-126">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="96e9b-126">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="96e9b-127">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="96e9b-127">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="96e9b-128">您可以使用 [\<arguments>](arguments.md) 、和專案， [\<states>](states.md) [\<states>](states.md) 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="96e9b-128">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="96e9b-129">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="96e9b-129">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="96e9b-130">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用在追蹤設定檔內訂閱 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="96e9b-130">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96e9b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96e9b-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="96e9b-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="96e9b-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="96e9b-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="96e9b-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
