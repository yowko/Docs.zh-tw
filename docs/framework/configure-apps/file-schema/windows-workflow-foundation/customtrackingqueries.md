---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 398b018ce407aee0687c95037753f3affa07aa9b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398787"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="35417-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="35417-101">\<customTrackingQueries></span></span>
<span data-ttu-id="35417-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="35417-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="35417-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="35417-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="35417-104">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="35417-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="35417-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="35417-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="35417-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="35417-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="35417-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="35417-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="35417-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="35417-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="35417-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="35417-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="35417-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="35417-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35417-111">語法</span><span class="sxs-lookup"><span data-stu-id="35417-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35417-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="35417-112">Attributes and Elements</span></span>  
 <span data-ttu-id="35417-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="35417-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35417-114">屬性</span><span class="sxs-lookup"><span data-stu-id="35417-114">Attributes</span></span>  
 <span data-ttu-id="35417-115">無。</span><span class="sxs-lookup"><span data-stu-id="35417-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="35417-116">子元素</span><span class="sxs-lookup"><span data-stu-id="35417-116">Child Elements</span></span>  
  
|<span data-ttu-id="35417-117">項目</span><span class="sxs-lookup"><span data-stu-id="35417-117">Element</span></span>|<span data-ttu-id="35417-118">描述</span><span class="sxs-lookup"><span data-stu-id="35417-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35417-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="35417-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="35417-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="35417-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35417-121">父項目</span><span class="sxs-lookup"><span data-stu-id="35417-121">Parent Elements</span></span>  
  
|<span data-ttu-id="35417-122">項目</span><span class="sxs-lookup"><span data-stu-id="35417-122">Element</span></span>|<span data-ttu-id="35417-123">說明</span><span class="sxs-lookup"><span data-stu-id="35417-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35417-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="35417-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="35417-125">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="35417-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35417-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35417-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="35417-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="35417-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="35417-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="35417-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
