---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a92a81062e92f832be78af2bfd75270390eaac3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919485"
---
# <a name="commonparameters"></a><span data-ttu-id="83481-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="83481-101">\<commonParameters></span></span>
<span data-ttu-id="83481-102">代表參數集合，這些參數可跨多項服務全域使用。</span><span class="sxs-lookup"><span data-stu-id="83481-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="83481-103">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="83481-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="83481-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="83481-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="83481-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="83481-105">\<behaviors></span></span>  
<span data-ttu-id="83481-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="83481-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="83481-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="83481-107">\<behavior></span></span>  
<span data-ttu-id="83481-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="83481-108">\<workflowRuntime></span></span>  
<span data-ttu-id="83481-109">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="83481-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83481-110">語法</span><span class="sxs-lookup"><span data-stu-id="83481-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83481-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83481-111">Attributes and Elements</span></span>  
 <span data-ttu-id="83481-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="83481-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83481-113">屬性</span><span class="sxs-lookup"><span data-stu-id="83481-113">Attributes</span></span>  
 <span data-ttu-id="83481-114">無。</span><span class="sxs-lookup"><span data-stu-id="83481-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="83481-115">子元素</span><span class="sxs-lookup"><span data-stu-id="83481-115">Child Elements</span></span>  
  
|<span data-ttu-id="83481-116">項目</span><span class="sxs-lookup"><span data-stu-id="83481-116">Element</span></span>|<span data-ttu-id="83481-117">說明</span><span class="sxs-lookup"><span data-stu-id="83481-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83481-118">\<add></span><span class="sxs-lookup"><span data-stu-id="83481-118">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="83481-119">將服務所使用的一般名稱/值組參數加入至集合。</span><span class="sxs-lookup"><span data-stu-id="83481-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83481-120">父項目</span><span class="sxs-lookup"><span data-stu-id="83481-120">Parent Elements</span></span>  
  
|<span data-ttu-id="83481-121">項目</span><span class="sxs-lookup"><span data-stu-id="83481-121">Element</span></span>|<span data-ttu-id="83481-122">描述</span><span class="sxs-lookup"><span data-stu-id="83481-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83481-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="83481-123">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="83481-124">針對裝載以工作流程為<xref:System.Workflow.Runtime.WorkflowRuntime>基礎的 Windows Communication Foundation (WCF) 服務, 指定實例的設定。</span><span class="sxs-lookup"><span data-stu-id="83481-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83481-125">備註</span><span class="sxs-lookup"><span data-stu-id="83481-125">Remarks</span></span>  
 <span data-ttu-id="83481-126">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="83481-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83481-127">如果 `ConnectionString` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `<commonParameters>` 值。</span><span class="sxs-lookup"><span data-stu-id="83481-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="83481-128">這項服務的某些作業 (例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 (Property)) 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="83481-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="83481-129">若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 (Attribute)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="83481-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="83481-130">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="83481-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="83481-131">請注意, `EnableRetries`您可以在全域層級 (如*CommonParameters*一節所示), 或針對支援`EnableRetries`的個別服務 (如 [*服務*] 區段中所示) 設定參數。</span><span class="sxs-lookup"><span data-stu-id="83481-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="83481-132">下列範例程式碼會示範如何以程式設計方式變更常見的參數。</span><span class="sxs-lookup"><span data-stu-id="83481-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="83481-133">如需使用設定檔控制 Windows Workflow Foundation 主應用程式之<xref:System.Workflow.Runtime.WorkflowRuntime>物件行為的詳細資訊, 請參閱[工作流程設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="83481-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83481-134">範例</span><span class="sxs-lookup"><span data-stu-id="83481-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="83481-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83481-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="83481-136">[工作流程設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="83481-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="83481-137">\<add></span><span class="sxs-lookup"><span data-stu-id="83481-137">\<add></span></span>](add-of-commonparameters.md)
