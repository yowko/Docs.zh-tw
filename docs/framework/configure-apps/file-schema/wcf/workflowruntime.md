---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 4a450fb6f02bbf0f1681f7b2fabea9da7b65cbea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183594"
---
# \<workflowRuntime>

<span data-ttu-id="0952b-101">指定實例的設定， <xref:System.Workflow.Runtime.WorkflowRuntime> 以裝載以工作流程為基礎的 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="0952b-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="0952b-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0952b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0952b-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0952b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0952b-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0952b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0952b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="0952b-105">Attributes</span></span>  
  
|<span data-ttu-id="0952b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="0952b-106">Attribute</span></span>|<span data-ttu-id="0952b-107">描述</span><span class="sxs-lookup"><span data-stu-id="0952b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0952b-108">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="0952b-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="0952b-109">選擇性 <xref:System.TimeSpan> 值，指定工作流程執行個體在遭到強制卸載或中止之前，能以閒置狀態存留在記憶體中的最長期間。</span><span class="sxs-lookup"><span data-stu-id="0952b-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="0952b-110">如果工作流程執行階段具有會執行 unloadOnIdle 的 `PersistenceService`，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="0952b-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="0952b-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="0952b-111">enablePerformanceCounters</span></span>|<span data-ttu-id="0952b-112">選擇性布林值，指定是否啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0952b-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="0952b-113">效能計數器會提供各種工作流程的相關統計資料，但是當工作流程執行階段引擎啟動和工作流程執行個體正在執行時，會對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="0952b-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="0952b-114">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="0952b-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="0952b-115">NAME</span><span class="sxs-lookup"><span data-stu-id="0952b-115">name</span></span>|<span data-ttu-id="0952b-116">字串，包含工作流程執行階段引擎的名稱。</span><span class="sxs-lookup"><span data-stu-id="0952b-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="0952b-117">名稱用於輸出以識別此執行階段及可能在系統執行的其他執行階段，例如在效能計數器中。</span><span class="sxs-lookup"><span data-stu-id="0952b-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="0952b-118">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="0952b-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="0952b-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="0952b-119">validateOnCreate</span></span>|<span data-ttu-id="0952b-120">選擇性布林值，指定當 WorkflowServiceHost 開啟時，是否會發生工作流程定義驗證。</span><span class="sxs-lookup"><span data-stu-id="0952b-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="0952b-121">當此屬性設定為 `true` 時，每次呼叫 `WorkflowServiceHost.Open` 都會執行一次工作流程驗證。</span><span class="sxs-lookup"><span data-stu-id="0952b-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="0952b-122">如果發現驗證錯誤，則會擲回 <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="0952b-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="0952b-123">當此屬性設定為 `false` 時，將不會執行工作流程定義驗證。</span><span class="sxs-lookup"><span data-stu-id="0952b-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="0952b-124">這個屬性的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="0952b-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0952b-125">子元素</span><span class="sxs-lookup"><span data-stu-id="0952b-125">Child Elements</span></span>  
  
|<span data-ttu-id="0952b-126">項目</span><span class="sxs-lookup"><span data-stu-id="0952b-126">Element</span></span>|<span data-ttu-id="0952b-127">描述</span><span class="sxs-lookup"><span data-stu-id="0952b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0952b-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="0952b-128">commonParameters</span></span>|<span data-ttu-id="0952b-129">服務所使用的一般參數集合。</span><span class="sxs-lookup"><span data-stu-id="0952b-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="0952b-130">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="0952b-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="0952b-131">服務</span><span class="sxs-lookup"><span data-stu-id="0952b-131">services</span></span>|<span data-ttu-id="0952b-132">要加入至 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎之服務的集合。</span><span class="sxs-lookup"><span data-stu-id="0952b-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="0952b-133">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0952b-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="0952b-134">集合中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="0952b-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="0952b-135">因此，集合中所指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="0952b-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="0952b-136">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0952b-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0952b-137">父項目</span><span class="sxs-lookup"><span data-stu-id="0952b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="0952b-138">項目</span><span class="sxs-lookup"><span data-stu-id="0952b-138">Element</span></span>|<span data-ttu-id="0952b-139">描述</span><span class="sxs-lookup"><span data-stu-id="0952b-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0952b-140">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="0952b-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0952b-141">備註</span><span class="sxs-lookup"><span data-stu-id="0952b-141">Remarks</span></span>  

 <span data-ttu-id="0952b-142">如需使用設定檔來控制 <xref:System.Workflow.Runtime.WorkflowRuntime> Windows Workflow Foundation 主應用程式之物件行為的詳細資訊，請參閱 [工作流程設定檔](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0952b-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0952b-143">範例</span><span class="sxs-lookup"><span data-stu-id="0952b-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0952b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0952b-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="0952b-145">[工作流程組態檔](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0952b-145">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
