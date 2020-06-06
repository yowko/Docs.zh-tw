---
title: <faultPropagationQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855272"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="dab5e-102">\<faultPropagationQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="dab5e-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="dab5e-103">代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。</span><span class="sxs-lookup"><span data-stu-id="dab5e-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dab5e-104">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="dab5e-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="dab5e-105">您應該使用這種查詢來追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="dab5e-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="dab5e-106">追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="dab5e-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="dab5e-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dab5e-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="dab5e-108">語法</span><span class="sxs-lookup"><span data-stu-id="dab5e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dab5e-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="dab5e-109">Attributes and elements</span></span>

<span data-ttu-id="dab5e-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dab5e-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="dab5e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dab5e-111">Attributes</span></span>

<span data-ttu-id="dab5e-112">無。</span><span class="sxs-lookup"><span data-stu-id="dab5e-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="dab5e-113">子元素</span><span class="sxs-lookup"><span data-stu-id="dab5e-113">Child elements</span></span>

|<span data-ttu-id="dab5e-114">元素</span><span class="sxs-lookup"><span data-stu-id="dab5e-114">Element</span></span>|<span data-ttu-id="dab5e-115">描述</span><span class="sxs-lookup"><span data-stu-id="dab5e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="dab5e-116">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="dab5e-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dab5e-117">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="dab5e-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dab5e-118">父元素</span><span class="sxs-lookup"><span data-stu-id="dab5e-118">Parent elements</span></span>  
  
|<span data-ttu-id="dab5e-119">元素</span><span class="sxs-lookup"><span data-stu-id="dab5e-119">Element</span></span>|<span data-ttu-id="dab5e-120">描述</span><span class="sxs-lookup"><span data-stu-id="dab5e-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="dab5e-121">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="dab5e-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dab5e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dab5e-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dab5e-123">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="dab5e-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dab5e-124">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="dab5e-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
