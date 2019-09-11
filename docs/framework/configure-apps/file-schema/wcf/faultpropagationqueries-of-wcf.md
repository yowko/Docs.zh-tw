---
title: <faultPropagationQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855272"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="a9439-102">\<WCF 的 faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="a9439-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="a9439-103">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="a9439-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a9439-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a9439-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a9439-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a9439-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a9439-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="a9439-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="a9439-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a9439-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a9439-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a9439-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a9439-109">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a9439-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a9439-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9439-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a9439-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="a9439-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a9439-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9439-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="a9439-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9439-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="a9439-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="a9439-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9439-115">語法</span><span class="sxs-lookup"><span data-stu-id="a9439-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9439-116">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a9439-116">Attributes and elements</span></span>

<span data-ttu-id="a9439-117">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a9439-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="a9439-118">屬性</span><span class="sxs-lookup"><span data-stu-id="a9439-118">Attributes</span></span>

<span data-ttu-id="a9439-119">無。</span><span class="sxs-lookup"><span data-stu-id="a9439-119">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="a9439-120">子元素</span><span class="sxs-lookup"><span data-stu-id="a9439-120">Child elements</span></span>

|<span data-ttu-id="a9439-121">項目</span><span class="sxs-lookup"><span data-stu-id="a9439-121">Element</span></span>|<span data-ttu-id="a9439-122">描述</span><span class="sxs-lookup"><span data-stu-id="a9439-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9439-123">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="a9439-123">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="a9439-124">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="a9439-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a9439-125">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="a9439-125">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9439-126">父元素</span><span class="sxs-lookup"><span data-stu-id="a9439-126">Parent elements</span></span>  
  
|<span data-ttu-id="a9439-127">元素</span><span class="sxs-lookup"><span data-stu-id="a9439-127">Element</span></span>|<span data-ttu-id="a9439-128">說明</span><span class="sxs-lookup"><span data-stu-id="a9439-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9439-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a9439-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a9439-130">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="a9439-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9439-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9439-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a9439-132">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="a9439-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a9439-133">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="a9439-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
