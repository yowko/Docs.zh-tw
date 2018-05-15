---
title: '&lt;workflowRuntime&gt;'
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 7c2bd4e2a8c1ddbdb98878d1d97c7acc41856310
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowruntimegt"></a><span data-ttu-id="7fc11-102">&lt;workflowRuntime&gt;</span><span class="sxs-lookup"><span data-stu-id="7fc11-102">&lt;workflowRuntime&gt;</span></span>
<span data-ttu-id="7fc11-103">指定的執行個體設定<xref:System.Workflow.Runtime.WorkflowRuntime>裝載工作流程為基礎的 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="7fc11-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="7fc11-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7fc11-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7fc11-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7fc11-105">\<behaviors></span></span>  
<span data-ttu-id="7fc11-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7fc11-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7fc11-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7fc11-107">\<behavior></span></span>  
<span data-ttu-id="7fc11-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="7fc11-108">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc11-109">語法</span><span class="sxs-lookup"><span data-stu-id="7fc11-109">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fc11-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7fc11-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7fc11-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7fc11-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fc11-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7fc11-112">Attributes</span></span>  
  
|<span data-ttu-id="7fc11-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7fc11-113">Attribute</span></span>|<span data-ttu-id="7fc11-114">描述</span><span class="sxs-lookup"><span data-stu-id="7fc11-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fc11-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="7fc11-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="7fc11-116">選擇性 <xref:System.TimeSpan> 值，指定工作流程執行個體在遭到強制卸載或中止之前，能以閒置狀態存留在記憶體中的最長期間。</span><span class="sxs-lookup"><span data-stu-id="7fc11-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="7fc11-117">如果工作流程執行階段具有會執行 unloadOnIdle 的 `PersistenceService`，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="7fc11-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="7fc11-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="7fc11-118">enablePerformanceCounters</span></span>|<span data-ttu-id="7fc11-119">選擇性布林值，指定是否啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="7fc11-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="7fc11-120">效能計數器會提供各種工作流程的相關統計資料，但是當工作流程執行階段引擎啟動和工作流程執行個體正在執行時，會對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="7fc11-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="7fc11-121">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="7fc11-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="7fc11-122">name</span><span class="sxs-lookup"><span data-stu-id="7fc11-122">name</span></span>|<span data-ttu-id="7fc11-123">字串，包含工作流程執行階段引擎的名稱。</span><span class="sxs-lookup"><span data-stu-id="7fc11-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="7fc11-124">名稱用於輸出以識別此執行階段及可能在系統執行的其他執行階段，例如在效能計數器中。</span><span class="sxs-lookup"><span data-stu-id="7fc11-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="7fc11-125">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="7fc11-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="7fc11-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="7fc11-126">validateOnCreate</span></span>|<span data-ttu-id="7fc11-127">選擇性布林值，指定當 WorkflowServiceHost 開啟時，是否會發生工作流程定義驗證。</span><span class="sxs-lookup"><span data-stu-id="7fc11-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="7fc11-128">當此屬性設定為 `true` 時，每次呼叫 `WorkflowServiceHost.Open` 都會執行一次工作流程驗證。</span><span class="sxs-lookup"><span data-stu-id="7fc11-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="7fc11-129">如果發現驗證錯誤，則會擲回 <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fc11-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="7fc11-130">當此屬性設定為 `false` 時，將不會執行工作流程定義驗證。</span><span class="sxs-lookup"><span data-stu-id="7fc11-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="7fc11-131">這個屬性的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7fc11-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fc11-132">子項目</span><span class="sxs-lookup"><span data-stu-id="7fc11-132">Child Elements</span></span>  
  
|<span data-ttu-id="7fc11-133">項目</span><span class="sxs-lookup"><span data-stu-id="7fc11-133">Element</span></span>|<span data-ttu-id="7fc11-134">描述</span><span class="sxs-lookup"><span data-stu-id="7fc11-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fc11-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="7fc11-135">commonParameters</span></span>|<span data-ttu-id="7fc11-136">服務所使用的一般參數集合。</span><span class="sxs-lookup"><span data-stu-id="7fc11-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="7fc11-137">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="7fc11-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="7fc11-138">服務</span><span class="sxs-lookup"><span data-stu-id="7fc11-138">services</span></span>|<span data-ttu-id="7fc11-139">要加入至 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎之服務的集合。</span><span class="sxs-lookup"><span data-stu-id="7fc11-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="7fc11-140">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="7fc11-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="7fc11-141">集合中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="7fc11-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="7fc11-142">因此，集合中所指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="7fc11-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="7fc11-143">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="7fc11-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fc11-144">父項目</span><span class="sxs-lookup"><span data-stu-id="7fc11-144">Parent Elements</span></span>  
  
|<span data-ttu-id="7fc11-145">項目</span><span class="sxs-lookup"><span data-stu-id="7fc11-145">Element</span></span>|<span data-ttu-id="7fc11-146">描述</span><span class="sxs-lookup"><span data-stu-id="7fc11-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fc11-147">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7fc11-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7fc11-148">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="7fc11-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fc11-149">備註</span><span class="sxs-lookup"><span data-stu-id="7fc11-149">Remarks</span></span>  
 <span data-ttu-id="7fc11-150">如需有關使用組態檔來控制行為的<xref:System.Workflow.Runtime.WorkflowRuntime>物件的 Windows Workflow Foundation 主應用程式，請參閱[工作流程組態檔](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)。</span><span class="sxs-lookup"><span data-stu-id="7fc11-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fc11-151">範例</span><span class="sxs-lookup"><span data-stu-id="7fc11-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fc11-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fc11-152">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="7fc11-153">工作流程組態檔</span><span class="sxs-lookup"><span data-stu-id="7fc11-153">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
