---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397771"
---
# \<variable>
<span data-ttu-id="912e9-101">代表與此活動查詢相關聯之變數的集合。</span><span class="sxs-lookup"><span data-stu-id="912e9-101">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="912e9-102">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="912e9-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**  
  
## <a name="syntax"></a><span data-ttu-id="912e9-103">語法</span><span class="sxs-lookup"><span data-stu-id="912e9-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="912e9-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="912e9-104">Attributes and Elements</span></span>  
 <span data-ttu-id="912e9-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="912e9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="912e9-106">屬性</span><span class="sxs-lookup"><span data-stu-id="912e9-106">Attributes</span></span>  
  
|<span data-ttu-id="912e9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="912e9-107">Attribute</span></span>|<span data-ttu-id="912e9-108">描述</span><span class="sxs-lookup"><span data-stu-id="912e9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="912e9-109">NAME</span><span class="sxs-lookup"><span data-stu-id="912e9-109">name</span></span>|<span data-ttu-id="912e9-110">指定變數名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="912e9-110">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="912e9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="912e9-111">Child Elements</span></span>  
 <span data-ttu-id="912e9-112">無。</span><span class="sxs-lookup"><span data-stu-id="912e9-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="912e9-113">父項目</span><span class="sxs-lookup"><span data-stu-id="912e9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="912e9-114">元素</span><span class="sxs-lookup"><span data-stu-id="912e9-114">Element</span></span>|<span data-ttu-id="912e9-115">描述</span><span class="sxs-lookup"><span data-stu-id="912e9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="912e9-116">與活動狀態查詢相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="912e9-116">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="912e9-117">備註</span><span class="sxs-lookup"><span data-stu-id="912e9-117">Remarks</span></span>  
 <span data-ttu-id="912e9-118">ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="912e9-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="912e9-119">它可在存取追蹤記錄後期執行時，提供額外的內容。</span><span class="sxs-lookup"><span data-stu-id="912e9-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="912e9-120">您可以使用 [\<arguments>](arguments.md) 、和專案， [\<states>](states.md) [\<states>](states.md) 從工作流程中的任何活動中解壓縮任何變數或引數。</span><span class="sxs-lookup"><span data-stu-id="912e9-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="912e9-121">下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。</span><span class="sxs-lookup"><span data-stu-id="912e9-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="912e9-122">只能使用 ActivityStateRecord 來解壓縮變數和引數，因此會使用在追蹤設定檔內訂閱 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="912e9-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="912e9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="912e9-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="912e9-124">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="912e9-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="912e9-125">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="912e9-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
