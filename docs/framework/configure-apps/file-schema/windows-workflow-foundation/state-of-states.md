---
title: <state> 的 <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 058480c29d6c5b554d5187a1a12a0c2e54587428
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169748"
---
# <a name="state-of-states"></a><span data-ttu-id="4f186-102">\<state> 的 \<states></span><span class="sxs-lookup"><span data-stu-id="4f186-102">\<state> of \<states></span></span>

<span data-ttu-id="4f186-103">組態項目，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="4f186-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="4f186-104">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4f186-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="4f186-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f186-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f186-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4f186-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4f186-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4f186-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f186-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4f186-108">Attributes</span></span>  
  
|<span data-ttu-id="4f186-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4f186-109">Attribute</span></span>|<span data-ttu-id="4f186-110">描述</span><span class="sxs-lookup"><span data-stu-id="4f186-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f186-111">NAME</span><span class="sxs-lookup"><span data-stu-id="4f186-111">name</span></span>|<span data-ttu-id="4f186-112">可指定追蹤記錄應發出之已訂閱活動狀態的字串。</span><span class="sxs-lookup"><span data-stu-id="4f186-112">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f186-113">子元素</span><span class="sxs-lookup"><span data-stu-id="4f186-113">Child Elements</span></span>  

 <span data-ttu-id="4f186-114">無。</span><span class="sxs-lookup"><span data-stu-id="4f186-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f186-115">父項目</span><span class="sxs-lookup"><span data-stu-id="4f186-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4f186-116">項目</span><span class="sxs-lookup"><span data-stu-id="4f186-116">Element</span></span>|<span data-ttu-id="4f186-117">描述</span><span class="sxs-lookup"><span data-stu-id="4f186-117">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="4f186-118">組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="4f186-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f186-119">備註</span><span class="sxs-lookup"><span data-stu-id="4f186-119">Remarks</span></span>  

 <span data-ttu-id="4f186-120">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="4f186-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4f186-121">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="4f186-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4f186-122">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和元素， [\<states>](states.md) 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="4f186-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4f186-123">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="4f186-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4f186-124">您只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用來訂閱追蹤設定檔中的 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="4f186-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f186-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f186-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4f186-126">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="4f186-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4f186-127">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4f186-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
