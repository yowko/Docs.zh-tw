---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 3a666b7c7affda06fbf03515b045eddf2a1f6af5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175885"
---
# \<customTrackingQueries>

<span data-ttu-id="9b82f-101">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="9b82f-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="9b82f-102">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="9b82f-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="9b82f-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9b82f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="9b82f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b82f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b82f-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9b82f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9b82f-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9b82f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b82f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9b82f-107">Attributes</span></span>  

 <span data-ttu-id="9b82f-108">無。</span><span class="sxs-lookup"><span data-stu-id="9b82f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b82f-109">子元素</span><span class="sxs-lookup"><span data-stu-id="9b82f-109">Child Elements</span></span>  
  
|<span data-ttu-id="9b82f-110">項目</span><span class="sxs-lookup"><span data-stu-id="9b82f-110">Element</span></span>|<span data-ttu-id="9b82f-111">描述</span><span class="sxs-lookup"><span data-stu-id="9b82f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="9b82f-112">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="9b82f-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b82f-113">父項目</span><span class="sxs-lookup"><span data-stu-id="9b82f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="9b82f-114">項目</span><span class="sxs-lookup"><span data-stu-id="9b82f-114">Element</span></span>|<span data-ttu-id="9b82f-115">描述</span><span class="sxs-lookup"><span data-stu-id="9b82f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="9b82f-116">設定元素，其中包含 **activityDefinitionId** 屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="9b82f-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b82f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b82f-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9b82f-118">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="9b82f-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9b82f-119">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="9b82f-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
