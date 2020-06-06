---
title: <customTrackingQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855441"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="94cf6-102">\<customTrackingQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="94cf6-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="94cf6-103">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="94cf6-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="94cf6-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="94cf6-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="94cf6-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="94cf6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="94cf6-106">語法</span><span class="sxs-lookup"><span data-stu-id="94cf6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94cf6-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="94cf6-107">Attributes and elements</span></span>

<span data-ttu-id="94cf6-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94cf6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94cf6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="94cf6-109">Attributes</span></span>

<span data-ttu-id="94cf6-110">無。</span><span class="sxs-lookup"><span data-stu-id="94cf6-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="94cf6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="94cf6-111">Child elements</span></span>
  
|<span data-ttu-id="94cf6-112">元素</span><span class="sxs-lookup"><span data-stu-id="94cf6-112">Element</span></span>|<span data-ttu-id="94cf6-113">描述</span><span class="sxs-lookup"><span data-stu-id="94cf6-113">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="94cf6-114">查詢，可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="94cf6-114">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94cf6-115">父元素</span><span class="sxs-lookup"><span data-stu-id="94cf6-115">Parent elements</span></span>  
  
|<span data-ttu-id="94cf6-116">元素</span><span class="sxs-lookup"><span data-stu-id="94cf6-116">Element</span></span>|<span data-ttu-id="94cf6-117">描述</span><span class="sxs-lookup"><span data-stu-id="94cf6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="94cf6-118">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="94cf6-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94cf6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94cf6-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="94cf6-120">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="94cf6-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="94cf6-121">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="94cf6-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
