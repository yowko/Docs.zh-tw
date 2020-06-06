---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398855"
---
# \<bookmarkResumptionQuery>
<span data-ttu-id="0b956-101">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="0b956-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="0b956-102">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="0b956-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="0b956-103">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0b956-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="0b956-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b956-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b956-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0b956-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0b956-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0b956-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b956-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0b956-107">Attributes</span></span>  
  
|<span data-ttu-id="0b956-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0b956-108">Attribute</span></span>|<span data-ttu-id="0b956-109">描述</span><span class="sxs-lookup"><span data-stu-id="0b956-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b956-110">NAME</span><span class="sxs-lookup"><span data-stu-id="0b956-110">name</span></span>|<span data-ttu-id="0b956-111">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b956-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b956-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0b956-112">Child Elements</span></span>  
 <span data-ttu-id="0b956-113">無。</span><span class="sxs-lookup"><span data-stu-id="0b956-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b956-114">父項目</span><span class="sxs-lookup"><span data-stu-id="0b956-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0b956-115">元素</span><span class="sxs-lookup"><span data-stu-id="0b956-115">Element</span></span>|<span data-ttu-id="0b956-116">描述</span><span class="sxs-lookup"><span data-stu-id="0b956-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="0b956-117">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="0b956-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b956-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b956-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0b956-119">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="0b956-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0b956-120">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0b956-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
