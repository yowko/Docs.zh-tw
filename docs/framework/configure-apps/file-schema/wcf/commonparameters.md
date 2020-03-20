---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153018"
---
# <a name="commonparameters"></a><span data-ttu-id="c458d-101">\<共同參數></span><span class="sxs-lookup"><span data-stu-id="c458d-101">\<commonParameters></span></span>
<span data-ttu-id="c458d-102">代表參數集合，這些參數可跨多項服務全域使用。</span><span class="sxs-lookup"><span data-stu-id="c458d-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="c458d-103">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="c458d-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="c458d-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c458d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c458d-105">&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c458d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c458d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c458d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c458d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c458d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c458d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c458d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c458d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流運行時>**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="c458d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="c458d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<公共參數>**</span><span class="sxs-lookup"><span data-stu-id="c458d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c458d-111">語法</span><span class="sxs-lookup"><span data-stu-id="c458d-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c458d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c458d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c458d-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c458d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c458d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c458d-114">Attributes</span></span>  
 <span data-ttu-id="c458d-115">無。</span><span class="sxs-lookup"><span data-stu-id="c458d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c458d-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c458d-116">Child Elements</span></span>  
  
|<span data-ttu-id="c458d-117">元素</span><span class="sxs-lookup"><span data-stu-id="c458d-117">Element</span></span>|<span data-ttu-id="c458d-118">描述</span><span class="sxs-lookup"><span data-stu-id="c458d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c458d-119">\<添加></span><span class="sxs-lookup"><span data-stu-id="c458d-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="c458d-120">將服務所使用的一般名稱/值組參數加入至集合。</span><span class="sxs-lookup"><span data-stu-id="c458d-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c458d-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c458d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c458d-122">元素</span><span class="sxs-lookup"><span data-stu-id="c458d-122">Element</span></span>|<span data-ttu-id="c458d-123">描述</span><span class="sxs-lookup"><span data-stu-id="c458d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c458d-124">\<工作流運行時></span><span class="sxs-lookup"><span data-stu-id="c458d-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="c458d-125">指定<xref:System.Workflow.Runtime.WorkflowRuntime>託管基於工作流的 Windows 通信基礎 （WCF） 服務的實例的設置。</span><span class="sxs-lookup"><span data-stu-id="c458d-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c458d-126">備註</span><span class="sxs-lookup"><span data-stu-id="c458d-126">Remarks</span></span>  
 <span data-ttu-id="c458d-127">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="c458d-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c458d-128">如果 `ConnectionString` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `<commonParameters>` 值。</span><span class="sxs-lookup"><span data-stu-id="c458d-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="c458d-129">這項服務的某些作業 (例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 (Property)) 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="c458d-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="c458d-130">若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 (Attribute)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c458d-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="c458d-131">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c458d-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="c458d-132">請注意，`EnableRetries`參數可以在全域級別設置（如 *"通用參數*"部分所示），也可以設置支援`EnableRetries`的各個服務（如 *"服務*"部分所示）。</span><span class="sxs-lookup"><span data-stu-id="c458d-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="c458d-133">以下示例代碼演示如何以程式設計方式更改公共參數：</span><span class="sxs-lookup"><span data-stu-id="c458d-133">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="c458d-134">有關使用設定檔控制 Windows 工作流基礎主機應用程式<xref:System.Workflow.Runtime.WorkflowRuntime>物件的行為的詳細資訊，請參閱[工作流設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="c458d-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c458d-135">範例</span><span class="sxs-lookup"><span data-stu-id="c458d-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="c458d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c458d-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="c458d-137">[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c458d-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="c458d-138">\<添加></span><span class="sxs-lookup"><span data-stu-id="c458d-138">\<add></span></span>](add-of-commonparameters.md)
