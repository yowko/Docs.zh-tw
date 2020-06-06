---
title: <bookmarkResumptionQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834010"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="019fc-102">\<bookmarkResumptionQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="019fc-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="019fc-103">代表用來追蹤工作流程執行個體中之書籤繼續的查詢。</span><span class="sxs-lookup"><span data-stu-id="019fc-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="019fc-104">追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="019fc-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="019fc-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="019fc-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="019fc-106">語法</span><span class="sxs-lookup"><span data-stu-id="019fc-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="019fc-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="019fc-107">Attributes and elements</span></span>

<span data-ttu-id="019fc-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="019fc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="019fc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="019fc-109">Attributes</span></span>  
  
|<span data-ttu-id="019fc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="019fc-110">Attribute</span></span>|<span data-ttu-id="019fc-111">描述</span><span class="sxs-lookup"><span data-stu-id="019fc-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="019fc-112">字串，可指定要訂閱的書籤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="019fc-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="019fc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="019fc-113">Child elements</span></span>

<span data-ttu-id="019fc-114">無。</span><span class="sxs-lookup"><span data-stu-id="019fc-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="019fc-115">父元素</span><span class="sxs-lookup"><span data-stu-id="019fc-115">Parent elements</span></span>  
  
|<span data-ttu-id="019fc-116">元素</span><span class="sxs-lookup"><span data-stu-id="019fc-116">Element</span></span>|<span data-ttu-id="019fc-117">描述</span><span class="sxs-lookup"><span data-stu-id="019fc-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="019fc-118">代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="019fc-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="019fc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="019fc-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="019fc-120">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="019fc-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="019fc-121">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="019fc-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
