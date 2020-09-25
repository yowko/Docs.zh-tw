---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a50e9965a595fce64c383313091334e883dcfbfa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189483"
---
# \<cancelRequestedQuery>

<span data-ttu-id="96303-101">代表查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="96303-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="96303-102">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="96303-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="96303-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="96303-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="96303-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="96303-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96303-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96303-105">Attributes and Elements</span></span>  

 <span data-ttu-id="96303-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="96303-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96303-107">屬性</span><span class="sxs-lookup"><span data-stu-id="96303-107">Attributes</span></span>  
  
|<span data-ttu-id="96303-108">屬性</span><span class="sxs-lookup"><span data-stu-id="96303-108">Attribute</span></span>|<span data-ttu-id="96303-109">描述</span><span class="sxs-lookup"><span data-stu-id="96303-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96303-110">activityName</span><span class="sxs-lookup"><span data-stu-id="96303-110">activityName</span></span>|<span data-ttu-id="96303-111">字串，可指定要求取消的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="96303-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="96303-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="96303-112">childActivityName</span></span>|<span data-ttu-id="96303-113">字串，可指定要求取消的子活動名稱。</span><span class="sxs-lookup"><span data-stu-id="96303-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96303-114">子元素</span><span class="sxs-lookup"><span data-stu-id="96303-114">Child Elements</span></span>  

 <span data-ttu-id="96303-115">無。</span><span class="sxs-lookup"><span data-stu-id="96303-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96303-116">父項目</span><span class="sxs-lookup"><span data-stu-id="96303-116">Parent Elements</span></span>  
  
|<span data-ttu-id="96303-117">項目</span><span class="sxs-lookup"><span data-stu-id="96303-117">Element</span></span>|<span data-ttu-id="96303-118">描述</span><span class="sxs-lookup"><span data-stu-id="96303-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="96303-119">代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="96303-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="96303-120">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="96303-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96303-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96303-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="96303-122">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="96303-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="96303-123">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="96303-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
