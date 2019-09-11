---
title: <activityStateQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 233bd3a2fa161222977902cc1053f964e8171173
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850480"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="f57fb-102">\<WCF 的 activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="f57fb-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="f57fb-103">代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f57fb-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="f57fb-104">例如，您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="f57fb-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="f57fb-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="f57fb-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="f57fb-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="f57fb-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="f57fb-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="f57fb-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="f57fb-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f57fb-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f57fb-109">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f57fb-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f57fb-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f57fb-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="f57fb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="f57fb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="f57fb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f57fb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="f57fb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f57fb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="f57fb-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Q s >** ](activitystatequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f57fb-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)</span></span>\
<span data-ttu-id="f57fb-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="f57fb-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57fb-116">語法</span><span class="sxs-lookup"><span data-stu-id="f57fb-116">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f57fb-117">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f57fb-117">Attributes and elements</span></span>  

<span data-ttu-id="f57fb-118">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f57fb-118">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f57fb-119">屬性</span><span class="sxs-lookup"><span data-stu-id="f57fb-119">Attributes</span></span>  
  
|<span data-ttu-id="f57fb-120">屬性</span><span class="sxs-lookup"><span data-stu-id="f57fb-120">Attribute</span></span>|<span data-ttu-id="f57fb-121">描述</span><span class="sxs-lookup"><span data-stu-id="f57fb-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f57fb-122">activityName</span><span class="sxs-lookup"><span data-stu-id="f57fb-122">activityName</span></span>|<span data-ttu-id="f57fb-123">字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f57fb-123">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f57fb-124">子元素</span><span class="sxs-lookup"><span data-stu-id="f57fb-124">Child elements</span></span>  
  
|<span data-ttu-id="f57fb-125">項目</span><span class="sxs-lookup"><span data-stu-id="f57fb-125">Element</span></span>|<span data-ttu-id="f57fb-126">描述</span><span class="sxs-lookup"><span data-stu-id="f57fb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f57fb-127">\<引數 ></span><span class="sxs-lookup"><span data-stu-id="f57fb-127">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="f57fb-128">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="f57fb-128">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="f57fb-129">\<states></span><span class="sxs-lookup"><span data-stu-id="f57fb-129">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="f57fb-130">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="f57fb-130">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="f57fb-131">\<states></span><span class="sxs-lookup"><span data-stu-id="f57fb-131">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="f57fb-132">與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="f57fb-132">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f57fb-133">父元素</span><span class="sxs-lookup"><span data-stu-id="f57fb-133">Parent elements</span></span>  
  
|<span data-ttu-id="f57fb-134">元素</span><span class="sxs-lookup"><span data-stu-id="f57fb-134">Element</span></span>|<span data-ttu-id="f57fb-135">描述</span><span class="sxs-lookup"><span data-stu-id="f57fb-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f57fb-136">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="f57fb-136">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="f57fb-137">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="f57fb-137">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f57fb-138">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="f57fb-138">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f57fb-139">備註</span><span class="sxs-lookup"><span data-stu-id="f57fb-139">Remarks</span></span>

<span data-ttu-id="f57fb-140">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="f57fb-140">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="f57fb-141">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="f57fb-141">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="f57fb-142">您可以使用[ \<引數 >](../windows-workflow-foundation/arguments.md)、 [ \<狀態 >](../windows-workflow-foundation/states.md)和[ \<狀態 >](../windows-workflow-foundation/states.md)元素，從工作流程中的任何活動中解壓縮任何變數或引數。下列範例顯示活動狀態查詢，它會在發出活動的`Closed`追蹤記錄時，解壓縮變數和引數。</span><span class="sxs-lookup"><span data-stu-id="f57fb-142">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="f57fb-143">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用[ \<activityStateQuery >](../windows-workflow-foundation/activitystatequery.md)在追蹤設定檔內訂閱。</span><span class="sxs-lookup"><span data-stu-id="f57fb-143">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="f57fb-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f57fb-144">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="f57fb-145">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="f57fb-145">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f57fb-146">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="f57fb-146">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
