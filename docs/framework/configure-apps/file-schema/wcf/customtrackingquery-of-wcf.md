---
title: <customTrackingQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855428"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="3b9d2-102">\<customTrackingQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="3b9d2-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="3b9d2-103">表示用來追蹤您在程式碼活動中定義之事件的查詢。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="3b9d2-104">追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="3b9d2-105">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3b9d2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="3b9d2-106">語法</span><span class="sxs-lookup"><span data-stu-id="3b9d2-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b9d2-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="3b9d2-107">Attributes and elements</span></span>  

<span data-ttu-id="3b9d2-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b9d2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3b9d2-109">Attributes</span></span>  
  
|<span data-ttu-id="3b9d2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3b9d2-110">Attribute</span></span>|<span data-ttu-id="3b9d2-111">描述</span><span class="sxs-lookup"><span data-stu-id="3b9d2-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="3b9d2-112">字串，可指定產生追蹤記錄的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="3b9d2-113">字串，可指定發出自訂追蹤記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b9d2-114">子元素</span><span class="sxs-lookup"><span data-stu-id="3b9d2-114">Child elements</span></span>

<span data-ttu-id="3b9d2-115">無。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3b9d2-116">父元素</span><span class="sxs-lookup"><span data-stu-id="3b9d2-116">Parent elements</span></span>

|<span data-ttu-id="3b9d2-117">元素</span><span class="sxs-lookup"><span data-stu-id="3b9d2-117">Element</span></span>|<span data-ttu-id="3b9d2-118">描述</span><span class="sxs-lookup"><span data-stu-id="3b9d2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="3b9d2-119">代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="3b9d2-119">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="3b9d2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b9d2-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3b9d2-121">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="3b9d2-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3b9d2-122">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="3b9d2-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
