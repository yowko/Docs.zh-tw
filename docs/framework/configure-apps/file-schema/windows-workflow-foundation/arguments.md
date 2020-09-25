---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: cb1f96cb6ba2643e28552c354bdd5caf4d43285c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189639"
---
# \<arguments>

<span data-ttu-id="a66a2-101">表示與某個活動狀態查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="a66a2-101">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="a66a2-102">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a66a2-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="a66a2-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="a66a2-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a66a2-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a66a2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a66a2-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a66a2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a66a2-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a66a2-106">Attributes</span></span>  

 <span data-ttu-id="a66a2-107">無。</span><span class="sxs-lookup"><span data-stu-id="a66a2-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a66a2-108">子元素</span><span class="sxs-lookup"><span data-stu-id="a66a2-108">Child Elements</span></span>  
  
|<span data-ttu-id="a66a2-109">項目</span><span class="sxs-lookup"><span data-stu-id="a66a2-109">Element</span></span>|<span data-ttu-id="a66a2-110">描述</span><span class="sxs-lookup"><span data-stu-id="a66a2-110">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="a66a2-111">與活動狀態查詢相關聯的引數。</span><span class="sxs-lookup"><span data-stu-id="a66a2-111">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a66a2-112">父項目</span><span class="sxs-lookup"><span data-stu-id="a66a2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a66a2-113">項目</span><span class="sxs-lookup"><span data-stu-id="a66a2-113">Element</span></span>|<span data-ttu-id="a66a2-114">描述</span><span class="sxs-lookup"><span data-stu-id="a66a2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="a66a2-115">代表組態項目，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="a66a2-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a66a2-116">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="a66a2-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a66a2-117">備註</span><span class="sxs-lookup"><span data-stu-id="a66a2-117">Remarks</span></span>  

 <span data-ttu-id="a66a2-118">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="a66a2-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a66a2-119">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="a66a2-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a66a2-120">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和元素， [\<states>](states.md) 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="a66a2-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="a66a2-121">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="a66a2-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a66a2-122">您只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用來訂閱追蹤設定檔中的 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="a66a2-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a66a2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a66a2-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a66a2-124">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="a66a2-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a66a2-125">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a66a2-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
