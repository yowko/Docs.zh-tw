---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152127"
---
# \<faultPropagationQueries>
<span data-ttu-id="6222b-101">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="6222b-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6222b-102">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="6222b-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="6222b-103">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="6222b-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="6222b-104">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="6222b-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="6222b-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="6222b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="6222b-106">語法</span><span class="sxs-lookup"><span data-stu-id="6222b-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6222b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6222b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6222b-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6222b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6222b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6222b-109">Attributes</span></span>  
 <span data-ttu-id="6222b-110">無。</span><span class="sxs-lookup"><span data-stu-id="6222b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6222b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6222b-111">Child Elements</span></span>  
  
|<span data-ttu-id="6222b-112">元素</span><span class="sxs-lookup"><span data-stu-id="6222b-112">Element</span></span>|<span data-ttu-id="6222b-113">描述</span><span class="sxs-lookup"><span data-stu-id="6222b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="6222b-114">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="6222b-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6222b-115">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="6222b-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6222b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="6222b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6222b-117">元素</span><span class="sxs-lookup"><span data-stu-id="6222b-117">Element</span></span>|<span data-ttu-id="6222b-118">描述</span><span class="sxs-lookup"><span data-stu-id="6222b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="6222b-119">Configuration 元素，其中包含**activityDefinitionId**屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="6222b-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6222b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6222b-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6222b-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="6222b-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6222b-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="6222b-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
