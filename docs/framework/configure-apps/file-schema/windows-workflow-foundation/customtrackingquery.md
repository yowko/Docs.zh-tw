---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152205"
---
# \<customTrackingQuery>
<span data-ttu-id="2135e-101">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="2135e-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="2135e-102">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="2135e-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="2135e-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2135e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="2135e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2135e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2135e-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2135e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2135e-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2135e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2135e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2135e-107">Attributes</span></span>  
  
|<span data-ttu-id="2135e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2135e-108">Attribute</span></span>|<span data-ttu-id="2135e-109">描述</span><span class="sxs-lookup"><span data-stu-id="2135e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2135e-110">activityName</span><span class="sxs-lookup"><span data-stu-id="2135e-110">activityName</span></span>|<span data-ttu-id="2135e-111">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="2135e-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="2135e-112">NAME</span><span class="sxs-lookup"><span data-stu-id="2135e-112">name</span></span>|<span data-ttu-id="2135e-113">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="2135e-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2135e-114">子元素</span><span class="sxs-lookup"><span data-stu-id="2135e-114">Child Elements</span></span>  
 <span data-ttu-id="2135e-115">無。</span><span class="sxs-lookup"><span data-stu-id="2135e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2135e-116">父項目</span><span class="sxs-lookup"><span data-stu-id="2135e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2135e-117">元素</span><span class="sxs-lookup"><span data-stu-id="2135e-117">Element</span></span>|<span data-ttu-id="2135e-118">描述</span><span class="sxs-lookup"><span data-stu-id="2135e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="2135e-119">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="2135e-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2135e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2135e-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2135e-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="2135e-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2135e-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2135e-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
