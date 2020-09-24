---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 59a76ea772dc8d06c390e3bca9d531df5f11e5f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148720"
---
# \<customTrackingQuery>

<span data-ttu-id="ec119-101">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="ec119-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ec119-102">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ec119-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ec119-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ec119-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="ec119-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec119-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec119-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ec119-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ec119-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ec119-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec119-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ec119-107">Attributes</span></span>  
  
|<span data-ttu-id="ec119-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ec119-108">Attribute</span></span>|<span data-ttu-id="ec119-109">描述</span><span class="sxs-lookup"><span data-stu-id="ec119-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec119-110">activityName</span><span class="sxs-lookup"><span data-stu-id="ec119-110">activityName</span></span>|<span data-ttu-id="ec119-111">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ec119-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="ec119-112">NAME</span><span class="sxs-lookup"><span data-stu-id="ec119-112">name</span></span>|<span data-ttu-id="ec119-113">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec119-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec119-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ec119-114">Child Elements</span></span>  

 <span data-ttu-id="ec119-115">無。</span><span class="sxs-lookup"><span data-stu-id="ec119-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec119-116">父項目</span><span class="sxs-lookup"><span data-stu-id="ec119-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ec119-117">項目</span><span class="sxs-lookup"><span data-stu-id="ec119-117">Element</span></span>|<span data-ttu-id="ec119-118">描述</span><span class="sxs-lookup"><span data-stu-id="ec119-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="ec119-119">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="ec119-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec119-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec119-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ec119-121">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="ec119-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ec119-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ec119-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
