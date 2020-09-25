---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 047d13bc8477214fa1e3c9ffdbed6785b29da637
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189574"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="1c55c-101">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="1c55c-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1c55c-102">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="1c55c-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="1c55c-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1c55c-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="1c55c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c55c-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c55c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1c55c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1c55c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1c55c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c55c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1c55c-107">Attributes</span></span>  

 <span data-ttu-id="1c55c-108">無。</span><span class="sxs-lookup"><span data-stu-id="1c55c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c55c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="1c55c-109">Child Elements</span></span>  
  
|<span data-ttu-id="1c55c-110">項目</span><span class="sxs-lookup"><span data-stu-id="1c55c-110">Element</span></span>|<span data-ttu-id="1c55c-111">描述</span><span class="sxs-lookup"><span data-stu-id="1c55c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="1c55c-112">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="1c55c-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1c55c-113">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="1c55c-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c55c-114">父項目</span><span class="sxs-lookup"><span data-stu-id="1c55c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1c55c-115">項目</span><span class="sxs-lookup"><span data-stu-id="1c55c-115">Element</span></span>|<span data-ttu-id="1c55c-116">描述</span><span class="sxs-lookup"><span data-stu-id="1c55c-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="1c55c-117">設定元素，其中包含 **activityDefinitionId** 屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="1c55c-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c55c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c55c-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1c55c-119">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="1c55c-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1c55c-120">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="1c55c-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
