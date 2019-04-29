---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673143"
---
# <a name="workflowruntime"></a><span data-ttu-id="3f5a4-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="3f5a4-101">\<workflowRuntime></span></span>
<span data-ttu-id="3f5a4-102">指定的執行個體設定<xref:System.Workflow.Runtime.WorkflowRuntime>用於裝載工作流程為基礎的 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="3f5a4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f5a4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f5a4-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="3f5a4-104">\<behaviors></span></span>  
<span data-ttu-id="3f5a4-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3f5a4-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3f5a4-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3f5a4-106">\<behavior></span></span>  
<span data-ttu-id="3f5a4-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="3f5a4-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5a4-108">語法</span><span class="sxs-lookup"><span data-stu-id="3f5a4-108">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f5a4-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3f5a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f5a4-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f5a4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3f5a4-111">Attributes</span></span>  
  
|<span data-ttu-id="3f5a4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3f5a4-112">Attribute</span></span>|<span data-ttu-id="3f5a4-113">描述</span><span class="sxs-lookup"><span data-stu-id="3f5a4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f5a4-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="3f5a4-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="3f5a4-115">選擇性 <xref:System.TimeSpan> 值，指定工作流程執行個體在遭到強制卸載或中止之前，能以閒置狀態存留在記憶體中的最長期間。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="3f5a4-116">如果工作流程執行階段具有會執行 unloadOnIdle 的 `PersistenceService`，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="3f5a4-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="3f5a4-117">enablePerformanceCounters</span></span>|<span data-ttu-id="3f5a4-118">選擇性布林值，指定是否啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="3f5a4-119">效能計數器會提供各種工作流程的相關統計資料，但是當工作流程執行階段引擎啟動和工作流程執行個體正在執行時，會對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="3f5a4-120">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="3f5a4-121">名稱</span><span class="sxs-lookup"><span data-stu-id="3f5a4-121">name</span></span>|<span data-ttu-id="3f5a4-122">字串，包含工作流程執行階段引擎的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="3f5a4-123">名稱用於輸出以識別此執行階段及可能在系統執行的其他執行階段，例如在效能計數器中。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="3f5a4-124">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="3f5a4-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="3f5a4-125">validateOnCreate</span></span>|<span data-ttu-id="3f5a4-126">選擇性布林值，指定當 WorkflowServiceHost 開啟時，是否會發生工作流程定義驗證。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="3f5a4-127">當此屬性設定為 `true` 時，每次呼叫 `WorkflowServiceHost.Open` 都會執行一次工作流程驗證。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="3f5a4-128">如果發現驗證錯誤，則會擲回 <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="3f5a4-129">當此屬性設定為 `false` 時，將不會執行工作流程定義驗證。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="3f5a4-130">這個屬性的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f5a4-131">子元素</span><span class="sxs-lookup"><span data-stu-id="3f5a4-131">Child Elements</span></span>  
  
|<span data-ttu-id="3f5a4-132">項目</span><span class="sxs-lookup"><span data-stu-id="3f5a4-132">Element</span></span>|<span data-ttu-id="3f5a4-133">描述</span><span class="sxs-lookup"><span data-stu-id="3f5a4-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f5a4-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="3f5a4-134">commonParameters</span></span>|<span data-ttu-id="3f5a4-135">服務所使用的一般參數集合。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="3f5a4-136">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="3f5a4-137">服務</span><span class="sxs-lookup"><span data-stu-id="3f5a4-137">services</span></span>|<span data-ttu-id="3f5a4-138">要加入至 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎之服務的集合。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="3f5a4-139">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="3f5a4-140">集合中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="3f5a4-141">因此，集合中所指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="3f5a4-142">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f5a4-143">父項目</span><span class="sxs-lookup"><span data-stu-id="3f5a4-143">Parent Elements</span></span>  
  
|<span data-ttu-id="3f5a4-144">項目</span><span class="sxs-lookup"><span data-stu-id="3f5a4-144">Element</span></span>|<span data-ttu-id="3f5a4-145">描述</span><span class="sxs-lookup"><span data-stu-id="3f5a4-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f5a4-146">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3f5a4-146">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3f5a4-147">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f5a4-148">備註</span><span class="sxs-lookup"><span data-stu-id="3f5a4-148">Remarks</span></span>  
 <span data-ttu-id="3f5a4-149">如需使用組態檔來控制行為的詳細資訊<xref:System.Workflow.Runtime.WorkflowRuntime>物件的 Windows Workflow Foundation 主應用程式，請參閱[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="3f5a4-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f5a4-150">範例</span><span class="sxs-lookup"><span data-stu-id="3f5a4-150">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="3f5a4-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f5a4-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="3f5a4-152">[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3f5a4-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
