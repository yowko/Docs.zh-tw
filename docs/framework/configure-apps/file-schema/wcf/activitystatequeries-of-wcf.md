---
title: <activityStateQueries>WCF 的
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850580"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="784f1-102">\<activityStateQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="784f1-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="784f1-103">代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="784f1-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="784f1-104">例如，您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。</span><span class="sxs-lookup"><span data-stu-id="784f1-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="784f1-105">追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。</span><span class="sxs-lookup"><span data-stu-id="784f1-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="784f1-106">可供訂閱的狀態可於 ActivityStates 中指定。</span><span class="sxs-lookup"><span data-stu-id="784f1-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="784f1-107">如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="784f1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="784f1-108">語法</span><span class="sxs-lookup"><span data-stu-id="784f1-108">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="784f1-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="784f1-109">Attributes and elements</span></span>

<span data-ttu-id="784f1-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="784f1-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="784f1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="784f1-111">Attributes</span></span>  

<span data-ttu-id="784f1-112">無。</span><span class="sxs-lookup"><span data-stu-id="784f1-112">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="784f1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="784f1-113">Child elements</span></span>

|<span data-ttu-id="784f1-114">元素</span><span class="sxs-lookup"><span data-stu-id="784f1-114">Element</span></span>|<span data-ttu-id="784f1-115">描述</span><span class="sxs-lookup"><span data-stu-id="784f1-115">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="784f1-116">用來追蹤活動中發生之錯誤處理的查詢。</span><span class="sxs-lookup"><span data-stu-id="784f1-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="784f1-117">每當 FaultHandler 處理錯誤時，都會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="784f1-117">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="784f1-118">父元素</span><span class="sxs-lookup"><span data-stu-id="784f1-118">Parent elements</span></span>

|<span data-ttu-id="784f1-119">元素</span><span class="sxs-lookup"><span data-stu-id="784f1-119">Element</span></span>|<span data-ttu-id="784f1-120">描述</span><span class="sxs-lookup"><span data-stu-id="784f1-120">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="784f1-121">包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。</span><span class="sxs-lookup"><span data-stu-id="784f1-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="784f1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="784f1-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="784f1-123">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="784f1-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="784f1-124">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="784f1-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
