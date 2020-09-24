---
title: <cancelRequestedQueries> WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 205399330c1aa69b332c2149ee32d9b6098ccdbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151164"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="d1469-102">\<cancelRequestedQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="d1469-102">\<cancelRequestedQueries> of WCF</span></span>

<span data-ttu-id="d1469-103">代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="d1469-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d1469-104">追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。</span><span class="sxs-lookup"><span data-stu-id="d1469-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="d1469-105">如需追蹤設定檔查詢的詳細資訊，請參閱 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d1469-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="d1469-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1469-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1469-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="d1469-107">Attributes and elements</span></span>  

<span data-ttu-id="d1469-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d1469-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1469-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d1469-109">Attributes</span></span>

<span data-ttu-id="d1469-110">無。</span><span class="sxs-lookup"><span data-stu-id="d1469-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="d1469-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d1469-111">Child elements</span></span>
  
|<span data-ttu-id="d1469-112">項目</span><span class="sxs-lookup"><span data-stu-id="d1469-112">Element</span></span>|<span data-ttu-id="d1469-113">描述</span><span class="sxs-lookup"><span data-stu-id="d1469-113">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="d1469-114">查詢，可用來追蹤由父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="d1469-114">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1469-115">父元素</span><span class="sxs-lookup"><span data-stu-id="d1469-115">Parent elements</span></span>  
  
|<span data-ttu-id="d1469-116">項目</span><span class="sxs-lookup"><span data-stu-id="d1469-116">Element</span></span>|<span data-ttu-id="d1469-117">描述</span><span class="sxs-lookup"><span data-stu-id="d1469-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="d1469-118">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="d1469-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1469-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1469-119">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="d1469-120">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="d1469-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d1469-121">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="d1469-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
