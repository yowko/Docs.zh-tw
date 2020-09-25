---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 72a2d6f8439e720bb7bf236bd942552224e85501
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189723"
---
# \<argument>

<span data-ttu-id="e7832-101">表示與活動狀態查詢相關聯之引數的組態項目。</span><span class="sxs-lookup"><span data-stu-id="e7832-101">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="e7832-102">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e7832-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="e7832-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7832-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7832-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7832-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e7832-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e7832-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7832-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e7832-106">Attributes</span></span>  
  
|<span data-ttu-id="e7832-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e7832-107">Attribute</span></span>|<span data-ttu-id="e7832-108">描述</span><span class="sxs-lookup"><span data-stu-id="e7832-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7832-109">NAME</span><span class="sxs-lookup"><span data-stu-id="e7832-109">name</span></span>|<span data-ttu-id="e7832-110">指定引數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e7832-110">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7832-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e7832-111">Child Elements</span></span>  

 <span data-ttu-id="e7832-112">無。</span><span class="sxs-lookup"><span data-stu-id="e7832-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7832-113">父項目</span><span class="sxs-lookup"><span data-stu-id="e7832-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e7832-114">項目</span><span class="sxs-lookup"><span data-stu-id="e7832-114">Element</span></span>|<span data-ttu-id="e7832-115">描述</span><span class="sxs-lookup"><span data-stu-id="e7832-115">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="e7832-116">與此活動查詢相關聯之引數的集合。</span><span class="sxs-lookup"><span data-stu-id="e7832-116">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7832-117">備註</span><span class="sxs-lookup"><span data-stu-id="e7832-117">Remarks</span></span>  

 <span data-ttu-id="e7832-118">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e7832-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e7832-119">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="e7832-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e7832-120">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和元素， [\<states>](states.md) 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="e7832-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e7832-121">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="e7832-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e7832-122">您只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用來訂閱追蹤設定檔中的 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="e7832-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7832-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7832-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e7832-124">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="e7832-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7832-125">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e7832-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
