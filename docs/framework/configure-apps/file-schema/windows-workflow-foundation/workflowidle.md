---
title: '&lt;workflowIdle&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5f9b4989de57204d9ec97d69475121c30ae82644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="54e5c-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="54e5c-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="54e5c-103">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="54e5c-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="54e5c-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="54e5c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="54e5c-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="54e5c-105">\<behaviors></span></span>  
<span data-ttu-id="54e5c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="54e5c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="54e5c-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="54e5c-107">\<behavior></span></span>  
<span data-ttu-id="54e5c-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="54e5c-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e5c-109">語法</span><span class="sxs-lookup"><span data-stu-id="54e5c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54e5c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="54e5c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="54e5c-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="54e5c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54e5c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="54e5c-112">Attributes</span></span>  
  
|<span data-ttu-id="54e5c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="54e5c-113">Attribute</span></span>|<span data-ttu-id="54e5c-114">描述</span><span class="sxs-lookup"><span data-stu-id="54e5c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54e5c-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="54e5c-115">timeToPersist</span></span>|<span data-ttu-id="54e5c-116">Timespan 值，指定工作流程進入閒置狀態與保存的時間之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="54e5c-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="54e5c-117">預設值是 TimeSpan.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="54e5c-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="54e5c-118">持續期間會開始在工作流程執行個體閒置時開始消逝。</span><span class="sxs-lookup"><span data-stu-id="54e5c-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="54e5c-119">這個屬性是很有用，如果您想要更積極地保存工作流程執行個體，同時仍保留在記憶體中，盡可能長期的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54e5c-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="54e5c-120">這個屬性才有效，如果其值為小於**timeToUnload**屬性。</span><span class="sxs-lookup"><span data-stu-id="54e5c-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="54e5c-121">如果此屬性的值較大，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="54e5c-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="54e5c-122">如果這個屬性就超過所指定的值之前**timeToUnload**屬性，持續性必須先完成工作流程已卸載。</span><span class="sxs-lookup"><span data-stu-id="54e5c-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="54e5c-123">也就是說，卸載作業可能會延遲到保存工作流程之後。</span><span class="sxs-lookup"><span data-stu-id="54e5c-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="54e5c-124">保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="54e5c-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="54e5c-125">因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="54e5c-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="54e5c-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="54e5c-126">timeToUnload</span></span>|<span data-ttu-id="54e5c-127">Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="54e5c-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="54e5c-128">預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="54e5c-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="54e5c-129">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="54e5c-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="54e5c-130">如果這個屬性設為的零會保存工作流程執行個體，並將其卸載之後立即工作流程變成閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="54e5c-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="54e5c-131">有效地將此屬性設定為 TimeSpan.MaxValue，就會停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="54e5c-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="54e5c-132">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="54e5c-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54e5c-133">子元素</span><span class="sxs-lookup"><span data-stu-id="54e5c-133">Child Elements</span></span>  
 <span data-ttu-id="54e5c-134">無。</span><span class="sxs-lookup"><span data-stu-id="54e5c-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54e5c-135">父項目</span><span class="sxs-lookup"><span data-stu-id="54e5c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="54e5c-136">項目</span><span class="sxs-lookup"><span data-stu-id="54e5c-136">Element</span></span>|<span data-ttu-id="54e5c-137">說明</span><span class="sxs-lookup"><span data-stu-id="54e5c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54e5c-138">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="54e5c-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="54e5c-139">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="54e5c-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54e5c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54e5c-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
