---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397542"
---
# <a name="workflowidle"></a><span data-ttu-id="31b3a-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="31b3a-101">\<workflowIdle></span></span>
<span data-ttu-id="31b3a-102">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="31b3a-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="31b3a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="31b3a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="31b3a-104">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="31b3a-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="31b3a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="31b3a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="31b3a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="31b3a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="31b3a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="31b3a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="31b3a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**</span><span class="sxs-lookup"><span data-stu-id="31b3a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b3a-109">語法</span><span class="sxs-lookup"><span data-stu-id="31b3a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31b3a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="31b3a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="31b3a-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="31b3a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31b3a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="31b3a-112">Attributes</span></span>  
  
|<span data-ttu-id="31b3a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="31b3a-113">Attribute</span></span>|<span data-ttu-id="31b3a-114">描述</span><span class="sxs-lookup"><span data-stu-id="31b3a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31b3a-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="31b3a-115">timeToPersist</span></span>|<span data-ttu-id="31b3a-116">Timespan 值，指定工作流程閒置和保存之間的持續時間。</span><span class="sxs-lookup"><span data-stu-id="31b3a-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="31b3a-117">預設值為 Timespan.zero。</span><span class="sxs-lookup"><span data-stu-id="31b3a-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="31b3a-118">持續期間會開始在工作流程執行個體閒置時開始消逝。</span><span class="sxs-lookup"><span data-stu-id="31b3a-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="31b3a-119">如果您想要更積極地保存工作流程實例，但仍將實例保持在記憶體中最長的時間，這個屬性就很有用。</span><span class="sxs-lookup"><span data-stu-id="31b3a-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="31b3a-120">只有在其值小於**timeToUnload**屬性時，這個屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="31b3a-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="31b3a-121">如果此屬性的值較大，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="31b3a-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="31b3a-122">如果此屬性在**timeToUnload**屬性所指定的值之前過期，則持續性必須在卸載工作流程之前完成。</span><span class="sxs-lookup"><span data-stu-id="31b3a-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="31b3a-123">也就是說，卸載作業可能會延遲到保存工作流程之後。</span><span class="sxs-lookup"><span data-stu-id="31b3a-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="31b3a-124">保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="31b3a-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="31b3a-125">因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="31b3a-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="31b3a-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="31b3a-126">timeToUnload</span></span>|<span data-ttu-id="31b3a-127">Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="31b3a-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="31b3a-128">預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="31b3a-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="31b3a-129">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="31b3a-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="31b3a-130">如果此屬性設定為零，則會在工作流程變成閒置之後，立即保存工作流程實例並將其卸載。</span><span class="sxs-lookup"><span data-stu-id="31b3a-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="31b3a-131">將此屬性設定為 TimeSpan，會有效地停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="31b3a-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="31b3a-132">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="31b3a-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31b3a-133">子元素</span><span class="sxs-lookup"><span data-stu-id="31b3a-133">Child Elements</span></span>  
 <span data-ttu-id="31b3a-134">無。</span><span class="sxs-lookup"><span data-stu-id="31b3a-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31b3a-135">父項目</span><span class="sxs-lookup"><span data-stu-id="31b3a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="31b3a-136">項目</span><span class="sxs-lookup"><span data-stu-id="31b3a-136">Element</span></span>|<span data-ttu-id="31b3a-137">描述</span><span class="sxs-lookup"><span data-stu-id="31b3a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31b3a-138">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="31b3a-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="31b3a-139">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="31b3a-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31b3a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31b3a-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
