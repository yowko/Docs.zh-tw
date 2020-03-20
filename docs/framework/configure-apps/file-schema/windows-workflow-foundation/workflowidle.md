---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151841"
---
# <a name="workflowidle"></a><span data-ttu-id="931d3-101">\<工作流 空閒></span><span class="sxs-lookup"><span data-stu-id="931d3-101">\<workflowIdle></span></span>
<span data-ttu-id="931d3-102">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="931d3-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="931d3-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="931d3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="931d3-104">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="931d3-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="931d3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="931d3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="931d3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="931d3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="931d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="931d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="931d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<工作流 空閒>**</span><span class="sxs-lookup"><span data-stu-id="931d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="931d3-109">語法</span><span class="sxs-lookup"><span data-stu-id="931d3-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="931d3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="931d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="931d3-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="931d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="931d3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="931d3-112">Attributes</span></span>  
  
|<span data-ttu-id="931d3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="931d3-113">Attribute</span></span>|<span data-ttu-id="931d3-114">描述</span><span class="sxs-lookup"><span data-stu-id="931d3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="931d3-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="931d3-115">timeToPersist</span></span>|<span data-ttu-id="931d3-116">Timespan 值，可指定在工作流程進入閒置狀態以及保存之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="931d3-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="931d3-117">預設值為 TimeSpan.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="931d3-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="931d3-118">持續期間會開始在工作流程執行個體閒置時開始消逝。</span><span class="sxs-lookup"><span data-stu-id="931d3-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="931d3-119">如果您想要透過盡可能延長將該執行個體保留在記憶體的時間，更積極地保存工作流程執行個體，這個屬性就非常實用。</span><span class="sxs-lookup"><span data-stu-id="931d3-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="931d3-120">僅當此屬性的值小於**timeToUnload**屬性時，此屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="931d3-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="931d3-121">如果此屬性的值較大，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="931d3-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="931d3-122">如果此屬性在**timeToUnload**屬性指定的值之前經過，則在卸載工作流之前必須完成持久性。</span><span class="sxs-lookup"><span data-stu-id="931d3-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="931d3-123">也就是說，卸載作業可能會延遲到保存工作流程之後。</span><span class="sxs-lookup"><span data-stu-id="931d3-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="931d3-124">保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="931d3-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="931d3-125">因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="931d3-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="931d3-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="931d3-126">timeToUnload</span></span>|<span data-ttu-id="931d3-127">Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="931d3-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="931d3-128">預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="931d3-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="931d3-129">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="931d3-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="931d3-130">如果將這個屬性設定為零，則會在工作流程閒置之後，立刻保留及卸載工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="931d3-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="931d3-131">將這個屬性設定為 TimeSpan.MaxValue 可有效地停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="931d3-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="931d3-132">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="931d3-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="931d3-133">子元素</span><span class="sxs-lookup"><span data-stu-id="931d3-133">Child Elements</span></span>  
 <span data-ttu-id="931d3-134">無。</span><span class="sxs-lookup"><span data-stu-id="931d3-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="931d3-135">父項目</span><span class="sxs-lookup"><span data-stu-id="931d3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="931d3-136">元素</span><span class="sxs-lookup"><span data-stu-id="931d3-136">Element</span></span>|<span data-ttu-id="931d3-137">描述</span><span class="sxs-lookup"><span data-stu-id="931d3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="931d3-138">\<服務行為行為\<>></span><span class="sxs-lookup"><span data-stu-id="931d3-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="931d3-139">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="931d3-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="931d3-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="931d3-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
