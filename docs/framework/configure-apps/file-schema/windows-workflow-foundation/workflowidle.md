---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: af8a2568eb13bb3007065c4b4a3564aae27de7ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280926"
---
# <a name="workflowidle"></a><span data-ttu-id="fd5b3-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="fd5b3-101">\<workflowIdle></span></span>
<span data-ttu-id="fd5b3-102">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="fd5b3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd5b3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd5b3-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="fd5b3-104">\<behaviors></span></span>  
<span data-ttu-id="fd5b3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fd5b3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="fd5b3-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="fd5b3-106">\<behavior></span></span>  
<span data-ttu-id="fd5b3-107">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="fd5b3-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5b3-108">語法</span><span class="sxs-lookup"><span data-stu-id="fd5b3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd5b3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd5b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fd5b3-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd5b3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="fd5b3-111">Attributes</span></span>  
  
|<span data-ttu-id="fd5b3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fd5b3-112">Attribute</span></span>|<span data-ttu-id="fd5b3-113">描述</span><span class="sxs-lookup"><span data-stu-id="fd5b3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd5b3-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="fd5b3-114">timeToPersist</span></span>|<span data-ttu-id="fd5b3-115">Timespan 值，指定工作流程變成閒置，且會保存的時間之間的持續時間。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="fd5b3-116">預設值為 TimeSpan.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="fd5b3-117">持續期間會開始在工作流程執行個體閒置時開始消逝。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="fd5b3-118">這個屬性是很有用，如果您想要更積極地保存工作流程執行個體，同時仍保留在記憶體中的 盡可能長時間的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="fd5b3-119">這個屬性才有效，如果其值為小於**timeToUnload**屬性。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="fd5b3-120">如果此屬性的值較大，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="fd5b3-121">如果這個屬性所指定的值之前要經過**timeToUnload**屬性持續性必須先完成工作流程已卸載。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="fd5b3-122">也就是說，卸載作業可能會延遲到保存工作流程之後。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="fd5b3-123">保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="fd5b3-124">因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="fd5b3-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="fd5b3-125">timeToUnload</span></span>|<span data-ttu-id="fd5b3-126">Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="fd5b3-127">預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="fd5b3-128">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="fd5b3-129">如果這個屬性設定為零的工作流程執行個體保留及卸載之後立即工作流程變成閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="fd5b3-130">將此屬性設定為 timespan.maxvalue 可有效地停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="fd5b3-131">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd5b3-132">子元素</span><span class="sxs-lookup"><span data-stu-id="fd5b3-132">Child Elements</span></span>  
 <span data-ttu-id="fd5b3-133">無。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd5b3-134">父項目</span><span class="sxs-lookup"><span data-stu-id="fd5b3-134">Parent Elements</span></span>  
  
|<span data-ttu-id="fd5b3-135">項目</span><span class="sxs-lookup"><span data-stu-id="fd5b3-135">Element</span></span>|<span data-ttu-id="fd5b3-136">描述</span><span class="sxs-lookup"><span data-stu-id="fd5b3-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd5b3-137">\<行為 > 的\<v ></span><span class="sxs-lookup"><span data-stu-id="fd5b3-137">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fd5b3-138">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="fd5b3-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd5b3-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd5b3-139">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
