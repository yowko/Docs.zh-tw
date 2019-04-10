---
title: <add> 的 <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: c07b3377db4f5b434fd021b09de510c1d43ec832
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219183"
---
# <a name="add-of-services"></a><span data-ttu-id="57a12-102">\<add> of \<services></span><span class="sxs-lookup"><span data-stu-id="57a12-102">\<add> of \<services></span></span>
<span data-ttu-id="57a12-103">指定的執行個體設定<xref:System.Workflow.Runtime.WorkflowRuntime>用於裝載工作流程為基礎的 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="57a12-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="57a12-104">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="57a12-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="57a12-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="57a12-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="57a12-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="57a12-106">\<behaviors></span></span>  
<span data-ttu-id="57a12-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="57a12-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="57a12-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="57a12-108">\<behavior></span></span>  
<span data-ttu-id="57a12-109">\<services></span><span class="sxs-lookup"><span data-stu-id="57a12-109">\<services></span></span>  
<span data-ttu-id="57a12-110">\<add></span><span class="sxs-lookup"><span data-stu-id="57a12-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a12-111">語法</span><span class="sxs-lookup"><span data-stu-id="57a12-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57a12-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57a12-112">Attributes and Elements</span></span>  
 <span data-ttu-id="57a12-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="57a12-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57a12-114">屬性</span><span class="sxs-lookup"><span data-stu-id="57a12-114">Attributes</span></span>  
  
|<span data-ttu-id="57a12-115">屬性</span><span class="sxs-lookup"><span data-stu-id="57a12-115">Attribute</span></span>|<span data-ttu-id="57a12-116">描述</span><span class="sxs-lookup"><span data-stu-id="57a12-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57a12-117">類型</span><span class="sxs-lookup"><span data-stu-id="57a12-117">type</span></span>|<span data-ttu-id="57a12-118">字串，指定要初始化之服務的組件限定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="57a12-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="57a12-119">指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="57a12-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="57a12-120">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="57a12-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57a12-121">子元素</span><span class="sxs-lookup"><span data-stu-id="57a12-121">Child Elements</span></span>  
 <span data-ttu-id="57a12-122">無。</span><span class="sxs-lookup"><span data-stu-id="57a12-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57a12-123">父項目</span><span class="sxs-lookup"><span data-stu-id="57a12-123">Parent Elements</span></span>  
  
|<span data-ttu-id="57a12-124">項目</span><span class="sxs-lookup"><span data-stu-id="57a12-124">Element</span></span>|<span data-ttu-id="57a12-125">描述</span><span class="sxs-lookup"><span data-stu-id="57a12-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57a12-126">\<services></span><span class="sxs-lookup"><span data-stu-id="57a12-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="57a12-127">要加入至 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎之服務的集合。</span><span class="sxs-lookup"><span data-stu-id="57a12-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="57a12-128">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="57a12-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="57a12-129">集合中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="57a12-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="57a12-130">因此，集合中所指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="57a12-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="57a12-131">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="57a12-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57a12-132">備註</span><span class="sxs-lookup"><span data-stu-id="57a12-132">Remarks</span></span>  
 <span data-ttu-id="57a12-133">此項目中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="57a12-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="57a12-134">因此，指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="57a12-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="57a12-135">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="57a12-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57a12-136">範例</span><span class="sxs-lookup"><span data-stu-id="57a12-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57a12-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57a12-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [<span data-ttu-id="57a12-138">工作流程組態檔</span><span class="sxs-lookup"><span data-stu-id="57a12-138">Workflow Configuration Files</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
