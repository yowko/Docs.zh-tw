---
title: <customTrackingQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855441"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="65f42-102">\<WCF 的 customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="65f42-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="65f42-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="65f42-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="65f42-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="65f42-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="65f42-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="65f42-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="65f42-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65f42-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="65f42-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="65f42-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="65f42-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="65f42-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="65f42-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** </span><span class="sxs-lookup"><span data-stu-id="65f42-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="65f42-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="65f42-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="65f42-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="65f42-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="65f42-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="65f42-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="65f42-113">語法</span><span class="sxs-lookup"><span data-stu-id="65f42-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65f42-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="65f42-114">Attributes and elements</span></span>

<span data-ttu-id="65f42-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="65f42-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65f42-116">屬性</span><span class="sxs-lookup"><span data-stu-id="65f42-116">Attributes</span></span>

<span data-ttu-id="65f42-117">無。</span><span class="sxs-lookup"><span data-stu-id="65f42-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="65f42-118">子元素</span><span class="sxs-lookup"><span data-stu-id="65f42-118">Child elements</span></span>
  
|<span data-ttu-id="65f42-119">項目</span><span class="sxs-lookup"><span data-stu-id="65f42-119">Element</span></span>|<span data-ttu-id="65f42-120">描述</span><span class="sxs-lookup"><span data-stu-id="65f42-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65f42-121">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="65f42-121">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="65f42-122">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="65f42-122">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65f42-123">父元素</span><span class="sxs-lookup"><span data-stu-id="65f42-123">Parent elements</span></span>  
  
|<span data-ttu-id="65f42-124">元素</span><span class="sxs-lookup"><span data-stu-id="65f42-124">Element</span></span>|<span data-ttu-id="65f42-125">描述</span><span class="sxs-lookup"><span data-stu-id="65f42-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65f42-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="65f42-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="65f42-127">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="65f42-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65f42-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f42-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="65f42-129">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="65f42-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="65f42-130">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="65f42-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
