---
title: '&lt;services&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc68357332ebe06affd18f1539a66587b6ed1b91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549989"
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="72710-102">&lt;services&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="72710-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="72710-103">指定的執行個體設定<xref:System.Workflow.Runtime.WorkflowRuntime>用於裝載工作流程為基礎的 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="72710-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="72710-104">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="72710-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="72710-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="72710-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="72710-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="72710-106">\<behaviors></span></span>  
<span data-ttu-id="72710-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="72710-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="72710-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="72710-108">\<behavior></span></span>  
<span data-ttu-id="72710-109">\<services></span><span class="sxs-lookup"><span data-stu-id="72710-109">\<services></span></span>  
<span data-ttu-id="72710-110">\<add></span><span class="sxs-lookup"><span data-stu-id="72710-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72710-111">語法</span><span class="sxs-lookup"><span data-stu-id="72710-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72710-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="72710-112">Attributes and Elements</span></span>  
 <span data-ttu-id="72710-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="72710-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72710-114">屬性</span><span class="sxs-lookup"><span data-stu-id="72710-114">Attributes</span></span>  
  
|<span data-ttu-id="72710-115">屬性</span><span class="sxs-lookup"><span data-stu-id="72710-115">Attribute</span></span>|<span data-ttu-id="72710-116">描述</span><span class="sxs-lookup"><span data-stu-id="72710-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72710-117">類型</span><span class="sxs-lookup"><span data-stu-id="72710-117">type</span></span>|<span data-ttu-id="72710-118">字串，指定要初始化之服務的組件限定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="72710-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="72710-119">指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="72710-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="72710-120">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="72710-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72710-121">子元素</span><span class="sxs-lookup"><span data-stu-id="72710-121">Child Elements</span></span>  
 <span data-ttu-id="72710-122">無。</span><span class="sxs-lookup"><span data-stu-id="72710-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72710-123">父項目</span><span class="sxs-lookup"><span data-stu-id="72710-123">Parent Elements</span></span>  
  
|<span data-ttu-id="72710-124">項目</span><span class="sxs-lookup"><span data-stu-id="72710-124">Element</span></span>|<span data-ttu-id="72710-125">描述</span><span class="sxs-lookup"><span data-stu-id="72710-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72710-126">\<services></span><span class="sxs-lookup"><span data-stu-id="72710-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="72710-127">要加入至 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎之服務的集合。</span><span class="sxs-lookup"><span data-stu-id="72710-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="72710-128">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="72710-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="72710-129">集合中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="72710-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="72710-130">因此，集合中所指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="72710-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="72710-131">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="72710-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72710-132">備註</span><span class="sxs-lookup"><span data-stu-id="72710-132">Remarks</span></span>  
 <span data-ttu-id="72710-133">此項目中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="72710-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="72710-134">因此，指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="72710-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="72710-135">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="72710-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72710-136">範例</span><span class="sxs-lookup"><span data-stu-id="72710-136">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="72710-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72710-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="72710-138">[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="72710-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
