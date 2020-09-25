---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 4db30f3fed12b585b73339120fa5bc6602150e7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189535"
---
# \<cancelRequestedQueries>

<span data-ttu-id="62025-101">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="62025-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="62025-102">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="62025-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="62025-103">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="62025-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="62025-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="62025-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62025-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62025-105">Attributes and Elements</span></span>  

 <span data-ttu-id="62025-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="62025-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62025-107">屬性</span><span class="sxs-lookup"><span data-stu-id="62025-107">Attributes</span></span>  

 <span data-ttu-id="62025-108">無。</span><span class="sxs-lookup"><span data-stu-id="62025-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62025-109">子元素</span><span class="sxs-lookup"><span data-stu-id="62025-109">Child Elements</span></span>  
  
|<span data-ttu-id="62025-110">項目</span><span class="sxs-lookup"><span data-stu-id="62025-110">Element</span></span>|<span data-ttu-id="62025-111">描述</span><span class="sxs-lookup"><span data-stu-id="62025-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="62025-112">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="62025-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62025-113">父項目</span><span class="sxs-lookup"><span data-stu-id="62025-113">Parent Elements</span></span>  
  
|<span data-ttu-id="62025-114">項目</span><span class="sxs-lookup"><span data-stu-id="62025-114">Element</span></span>|<span data-ttu-id="62025-115">描述</span><span class="sxs-lookup"><span data-stu-id="62025-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="62025-116">設定元素，其中包含 **activityDefinitionId** 屬性所識別之特定工作流程的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="62025-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62025-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62025-117">See also</span></span>

- [<span data-ttu-id="62025-118">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="62025-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="62025-119">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="62025-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
