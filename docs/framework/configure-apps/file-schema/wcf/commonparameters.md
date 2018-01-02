---
title: "&lt;一般參數&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efd4f37adb19940e81109924c3ec313d71bf6e7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="bcb6e-102">&lt;一般參數&gt;</span><span class="sxs-lookup"><span data-stu-id="bcb6e-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="bcb6e-103">代表參數集合，這些參數可跨多項服務全域使用。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="bcb6e-104">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="bcb6e-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bcb6e-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-106">\<behaviors></span></span>  
<span data-ttu-id="bcb6e-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="bcb6e-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-108">\<behavior></span></span>  
<span data-ttu-id="bcb6e-109">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-109">\<workflowRuntime></span></span>  
<span data-ttu-id="bcb6e-110">\<一般參數 ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb6e-111">語法</span><span class="sxs-lookup"><span data-stu-id="bcb6e-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcb6e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bcb6e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bcb6e-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcb6e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="bcb6e-114">Attributes</span></span>  
 <span data-ttu-id="bcb6e-115">無。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bcb6e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="bcb6e-116">Child Elements</span></span>  
  
|<span data-ttu-id="bcb6e-117">項目</span><span class="sxs-lookup"><span data-stu-id="bcb6e-117">Element</span></span>|<span data-ttu-id="bcb6e-118">描述</span><span class="sxs-lookup"><span data-stu-id="bcb6e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcb6e-119">\<add></span><span class="sxs-lookup"><span data-stu-id="bcb6e-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="bcb6e-120">將服務所使用的一般名稱/值組參數加入至集合。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcb6e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="bcb6e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bcb6e-122">項目</span><span class="sxs-lookup"><span data-stu-id="bcb6e-122">Element</span></span>|<span data-ttu-id="bcb6e-123">描述</span><span class="sxs-lookup"><span data-stu-id="bcb6e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcb6e-124">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="bcb6e-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="bcb6e-125">指定 <xref:System.Workflow.Runtime.WorkflowRuntime> 之執行個體的設定，以裝載工作流程架構的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcb6e-126">備註</span><span class="sxs-lookup"><span data-stu-id="bcb6e-126">Remarks</span></span>  
 <span data-ttu-id="bcb6e-127">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcb6e-128">如果 `ConnectionString` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `<commonParameters>` 值。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="bcb6e-129">這項服務的某些作業 (例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 (Property)) 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="bcb6e-130">若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 (Attribute)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="bcb6e-131">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bcb6e-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="bcb6e-132">請注意，`EnableRetries`參數可以設定在全域層級 (如中所示*CommonParameters* > 一節) 或個別服務支援的`EnableRetries`(如中所示*服務*> 一節)。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="bcb6e-133">下列範例程式碼會示範如何以程式設計方式變更常見的參數。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="bcb6e-134">如需有關使用組態檔來控制行為的<xref:System.Workflow.Runtime.WorkflowRuntime>物件的 Windows Workflow Foundation 主應用程式，請參閱[工作流程組態檔](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)。</span><span class="sxs-lookup"><span data-stu-id="bcb6e-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcb6e-135">範例</span><span class="sxs-lookup"><span data-stu-id="bcb6e-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcb6e-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="bcb6e-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="bcb6e-137">工作流程組態檔</span><span class="sxs-lookup"><span data-stu-id="bcb6e-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="bcb6e-138">\<add></span><span class="sxs-lookup"><span data-stu-id="bcb6e-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
