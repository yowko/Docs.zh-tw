---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151841"
---
# \<workflowIdle>
<span data-ttu-id="85421-101">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="85421-101">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="85421-102">語法</span><span class="sxs-lookup"><span data-stu-id="85421-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85421-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85421-103">Attributes and Elements</span></span>  
 <span data-ttu-id="85421-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85421-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85421-105">屬性</span><span class="sxs-lookup"><span data-stu-id="85421-105">Attributes</span></span>  
  
|<span data-ttu-id="85421-106">屬性</span><span class="sxs-lookup"><span data-stu-id="85421-106">Attribute</span></span>|<span data-ttu-id="85421-107">描述</span><span class="sxs-lookup"><span data-stu-id="85421-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85421-108">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="85421-108">timeToPersist</span></span>|<span data-ttu-id="85421-109">Timespan 值，可指定在工作流程進入閒置狀態以及保存之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="85421-109">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="85421-110">預設值為 TimeSpan.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="85421-110">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="85421-111">持續期間會開始在工作流程執行個體閒置時開始消逝。</span><span class="sxs-lookup"><span data-stu-id="85421-111">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="85421-112">如果您想要透過盡可能延長將該執行個體保留在記憶體的時間，更積極地保存工作流程執行個體，這個屬性就非常實用。</span><span class="sxs-lookup"><span data-stu-id="85421-112">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="85421-113">只有在其值小於**timeToUnload**屬性時，這個屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="85421-113">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="85421-114">如果此屬性的值較大，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="85421-114">If it is greater, it is ignored.</span></span> <span data-ttu-id="85421-115">如果此屬性在**timeToUnload**屬性所指定的值之前過期，則持續性必須在卸載工作流程之前完成。</span><span class="sxs-lookup"><span data-stu-id="85421-115">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="85421-116">也就是說，卸載作業可能會延遲到保存工作流程之後。</span><span class="sxs-lookup"><span data-stu-id="85421-116">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="85421-117">保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="85421-117">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="85421-118">因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="85421-118">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="85421-119">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="85421-119">timeToUnload</span></span>|<span data-ttu-id="85421-120">Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。</span><span class="sxs-lookup"><span data-stu-id="85421-120">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="85421-121">預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="85421-121">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="85421-122">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="85421-122">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="85421-123">如果將這個屬性設定為零，則會在工作流程閒置之後，立刻保留及卸載工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="85421-123">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="85421-124">將這個屬性設定為 TimeSpan.MaxValue 可有效地停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="85421-124">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="85421-125">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="85421-125">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85421-126">子元素</span><span class="sxs-lookup"><span data-stu-id="85421-126">Child Elements</span></span>  
 <span data-ttu-id="85421-127">無。</span><span class="sxs-lookup"><span data-stu-id="85421-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85421-128">父項目</span><span class="sxs-lookup"><span data-stu-id="85421-128">Parent Elements</span></span>  
  
|<span data-ttu-id="85421-129">元素</span><span class="sxs-lookup"><span data-stu-id="85421-129">Element</span></span>|<span data-ttu-id="85421-130">描述</span><span class="sxs-lookup"><span data-stu-id="85421-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85421-131">\<behavior>的\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="85421-131">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="85421-132">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="85421-132">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85421-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85421-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
