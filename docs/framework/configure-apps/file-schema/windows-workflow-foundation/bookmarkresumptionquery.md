---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: efd1e4e54223ff9f5d60b4087fbe5b6bebf1af2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189585"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="627d9-101">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="627d9-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="627d9-102">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="627d9-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="627d9-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="627d9-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="627d9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="627d9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="627d9-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="627d9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="627d9-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="627d9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="627d9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="627d9-107">Attributes</span></span>  
  
|<span data-ttu-id="627d9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="627d9-108">Attribute</span></span>|<span data-ttu-id="627d9-109">描述</span><span class="sxs-lookup"><span data-stu-id="627d9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="627d9-110">NAME</span><span class="sxs-lookup"><span data-stu-id="627d9-110">name</span></span>|<span data-ttu-id="627d9-111">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="627d9-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="627d9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="627d9-112">Child Elements</span></span>  

 <span data-ttu-id="627d9-113">無。</span><span class="sxs-lookup"><span data-stu-id="627d9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="627d9-114">父項目</span><span class="sxs-lookup"><span data-stu-id="627d9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="627d9-115">項目</span><span class="sxs-lookup"><span data-stu-id="627d9-115">Element</span></span>|<span data-ttu-id="627d9-116">描述</span><span class="sxs-lookup"><span data-stu-id="627d9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="627d9-117">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="627d9-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="627d9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="627d9-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="627d9-119">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="627d9-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="627d9-120">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="627d9-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
