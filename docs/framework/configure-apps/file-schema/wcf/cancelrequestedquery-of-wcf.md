---
title: <cancelRequestedQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850059"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="99597-102">\<cancelRequestedQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="99597-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="99597-103">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="99597-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="99597-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="99597-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="99597-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="99597-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="99597-106">語法</span><span class="sxs-lookup"><span data-stu-id="99597-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99597-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="99597-107">Attributes and elements</span></span>

<span data-ttu-id="99597-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="99597-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="99597-109">屬性</span><span class="sxs-lookup"><span data-stu-id="99597-109">Attributes</span></span>  
  
|<span data-ttu-id="99597-110">屬性</span><span class="sxs-lookup"><span data-stu-id="99597-110">Attribute</span></span>|<span data-ttu-id="99597-111">描述</span><span class="sxs-lookup"><span data-stu-id="99597-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="99597-112">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="99597-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="99597-113">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="99597-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99597-114">子元素</span><span class="sxs-lookup"><span data-stu-id="99597-114">Child elements</span></span>

<span data-ttu-id="99597-115">無。</span><span class="sxs-lookup"><span data-stu-id="99597-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="99597-116">父元素</span><span class="sxs-lookup"><span data-stu-id="99597-116">Parent elements</span></span>
  
|<span data-ttu-id="99597-117">元素</span><span class="sxs-lookup"><span data-stu-id="99597-117">Element</span></span>|<span data-ttu-id="99597-118">描述</span><span class="sxs-lookup"><span data-stu-id="99597-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="99597-119">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="99597-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99597-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99597-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="99597-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="99597-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="99597-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="99597-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
