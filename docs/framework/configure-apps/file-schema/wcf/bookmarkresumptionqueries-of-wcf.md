---
title: <bookmarkResumptionQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850134"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="91d1a-102">\<bookmarkResumptionQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="91d1a-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="91d1a-103">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="91d1a-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="91d1a-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="91d1a-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="91d1a-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="91d1a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="91d1a-106">語法</span><span class="sxs-lookup"><span data-stu-id="91d1a-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91d1a-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="91d1a-107">Attributes and elements</span></span>  
  
<span data-ttu-id="91d1a-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="91d1a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91d1a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="91d1a-109">Attributes</span></span>  
  
<span data-ttu-id="91d1a-110">無。</span><span class="sxs-lookup"><span data-stu-id="91d1a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91d1a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="91d1a-111">Child elements</span></span>  
  
|<span data-ttu-id="91d1a-112">元素</span><span class="sxs-lookup"><span data-stu-id="91d1a-112">Element</span></span>|<span data-ttu-id="91d1a-113">描述</span><span class="sxs-lookup"><span data-stu-id="91d1a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="91d1a-114">查詢，可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="91d1a-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="91d1a-115">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="91d1a-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91d1a-116">父元素</span><span class="sxs-lookup"><span data-stu-id="91d1a-116">Parent elements</span></span>  
  
|<span data-ttu-id="91d1a-117">元素</span><span class="sxs-lookup"><span data-stu-id="91d1a-117">Element</span></span>|<span data-ttu-id="91d1a-118">描述</span><span class="sxs-lookup"><span data-stu-id="91d1a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="91d1a-119">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="91d1a-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91d1a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d1a-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="91d1a-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="91d1a-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="91d1a-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="91d1a-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
