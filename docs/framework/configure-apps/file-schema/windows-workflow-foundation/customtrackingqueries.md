---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152257"
---
# \<customTrackingQueries>
<span data-ttu-id="dc4f2-101">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="dc4f2-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="dc4f2-102">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="dc4f2-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="dc4f2-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dc4f2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="dc4f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc4f2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc4f2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc4f2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dc4f2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dc4f2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc4f2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="dc4f2-107">Attributes</span></span>  
 <span data-ttu-id="dc4f2-108">無。</span><span class="sxs-lookup"><span data-stu-id="dc4f2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc4f2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="dc4f2-109">Child Elements</span></span>  
  
|<span data-ttu-id="dc4f2-110">元素</span><span class="sxs-lookup"><span data-stu-id="dc4f2-110">Element</span></span>|<span data-ttu-id="dc4f2-111">描述</span><span class="sxs-lookup"><span data-stu-id="dc4f2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="dc4f2-112">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="dc4f2-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc4f2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="dc4f2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="dc4f2-114">元素</span><span class="sxs-lookup"><span data-stu-id="dc4f2-114">Element</span></span>|<span data-ttu-id="dc4f2-115">描述</span><span class="sxs-lookup"><span data-stu-id="dc4f2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="dc4f2-116">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="dc4f2-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc4f2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4f2-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dc4f2-118">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="dc4f2-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dc4f2-119">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="dc4f2-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
