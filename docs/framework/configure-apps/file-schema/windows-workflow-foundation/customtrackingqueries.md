---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152257"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="43dbd-101">\<自訂跟蹤查詢></span><span class="sxs-lookup"><span data-stu-id="43dbd-101">\<customTrackingQueries></span></span>
<span data-ttu-id="43dbd-102">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="43dbd-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="43dbd-103">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="43dbd-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="43dbd-104">有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="43dbd-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="43dbd-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43dbd-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43dbd-106">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="43dbd-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="43dbd-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="43dbd-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="43dbd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="43dbd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="43dbd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="43dbd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="43dbd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<自訂跟蹤查詢>**</span><span class="sxs-lookup"><span data-stu-id="43dbd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43dbd-111">語法</span><span class="sxs-lookup"><span data-stu-id="43dbd-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43dbd-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43dbd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="43dbd-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="43dbd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43dbd-114">屬性</span><span class="sxs-lookup"><span data-stu-id="43dbd-114">Attributes</span></span>  
 <span data-ttu-id="43dbd-115">無。</span><span class="sxs-lookup"><span data-stu-id="43dbd-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43dbd-116">子元素</span><span class="sxs-lookup"><span data-stu-id="43dbd-116">Child Elements</span></span>  
  
|<span data-ttu-id="43dbd-117">元素</span><span class="sxs-lookup"><span data-stu-id="43dbd-117">Element</span></span>|<span data-ttu-id="43dbd-118">描述</span><span class="sxs-lookup"><span data-stu-id="43dbd-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43dbd-119">\<自訂跟蹤查詢></span><span class="sxs-lookup"><span data-stu-id="43dbd-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="43dbd-120">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="43dbd-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43dbd-121">父項目</span><span class="sxs-lookup"><span data-stu-id="43dbd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="43dbd-122">元素</span><span class="sxs-lookup"><span data-stu-id="43dbd-122">Element</span></span>|<span data-ttu-id="43dbd-123">描述</span><span class="sxs-lookup"><span data-stu-id="43dbd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43dbd-124">\<工作流></span><span class="sxs-lookup"><span data-stu-id="43dbd-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="43dbd-125">包含**活動定義 Id**屬性標識的特定工作流的所有查詢的配置元素。</span><span class="sxs-lookup"><span data-stu-id="43dbd-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43dbd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43dbd-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="43dbd-127">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="43dbd-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="43dbd-128">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="43dbd-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
