---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153018"
---
# \<commonParameters>
<span data-ttu-id="464eb-101">代表參數集合，這些參數可跨多項服務全域使用。</span><span class="sxs-lookup"><span data-stu-id="464eb-101">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="464eb-102">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="464eb-102">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="464eb-103">語法</span><span class="sxs-lookup"><span data-stu-id="464eb-103">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="464eb-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="464eb-104">Attributes and Elements</span></span>  
 <span data-ttu-id="464eb-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="464eb-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="464eb-106">屬性</span><span class="sxs-lookup"><span data-stu-id="464eb-106">Attributes</span></span>  
 <span data-ttu-id="464eb-107">無。</span><span class="sxs-lookup"><span data-stu-id="464eb-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="464eb-108">子元素</span><span class="sxs-lookup"><span data-stu-id="464eb-108">Child Elements</span></span>  
  
|<span data-ttu-id="464eb-109">元素</span><span class="sxs-lookup"><span data-stu-id="464eb-109">Element</span></span>|<span data-ttu-id="464eb-110">描述</span><span class="sxs-lookup"><span data-stu-id="464eb-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="464eb-111">將服務所使用的一般名稱/值組參數加入至集合。</span><span class="sxs-lookup"><span data-stu-id="464eb-111">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="464eb-112">父項目</span><span class="sxs-lookup"><span data-stu-id="464eb-112">Parent Elements</span></span>  
  
|<span data-ttu-id="464eb-113">元素</span><span class="sxs-lookup"><span data-stu-id="464eb-113">Element</span></span>|<span data-ttu-id="464eb-114">描述</span><span class="sxs-lookup"><span data-stu-id="464eb-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="464eb-115"><xref:System.Workflow.Runtime.WorkflowRuntime>針對裝載以工作流程為基礎的 Windows Communication Foundation （WCF）服務，指定實例的設定。</span><span class="sxs-lookup"><span data-stu-id="464eb-115">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="464eb-116">備註</span><span class="sxs-lookup"><span data-stu-id="464eb-116">Remarks</span></span>  
 <span data-ttu-id="464eb-117">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="464eb-117">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="464eb-118">如果 `ConnectionString` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `<commonParameters>` 值。</span><span class="sxs-lookup"><span data-stu-id="464eb-118">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="464eb-119">這項服務的某些作業 (例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 (Property)) 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="464eb-119">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="464eb-120">若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 (Attribute)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="464eb-120">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="464eb-121">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="464eb-121">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="464eb-122">請注意，您 `EnableRetries` 可以在全域層級（如*CommonParameters*一節所示），或針對支援的個別服務 `EnableRetries` （如 [*服務*] 區段中所示）設定參數。</span><span class="sxs-lookup"><span data-stu-id="464eb-122">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="464eb-123">下列範例程式碼示範如何以程式設計方式變更一般參數：</span><span class="sxs-lookup"><span data-stu-id="464eb-123">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="464eb-124">如需使用設定檔控制 <xref:System.Workflow.Runtime.WorkflowRuntime> Windows Workflow Foundation 主應用程式之物件行為的詳細資訊，請參閱[工作流程設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="464eb-124">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="464eb-125">範例</span><span class="sxs-lookup"><span data-stu-id="464eb-125">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="464eb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="464eb-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="464eb-127">[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="464eb-127">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
