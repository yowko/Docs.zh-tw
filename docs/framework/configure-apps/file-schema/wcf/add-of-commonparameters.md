---
title: '&lt;commonParameters&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 93e82aa3bd44a747d1e85986c51c21522d709bd0
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841387"
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="c9979-102">&lt;commonParameters&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="c9979-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="c9979-103">指定跨多項服務全域使用之名稱/值組的參數。</span><span class="sxs-lookup"><span data-stu-id="c9979-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="c9979-104">這個參數通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="c9979-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="c9979-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9979-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9979-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c9979-106">\<behaviors></span></span>  
<span data-ttu-id="c9979-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c9979-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="c9979-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c9979-108">\<behavior></span></span>  
<span data-ttu-id="c9979-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="c9979-109">\<workflowRuntime></span></span>  
<span data-ttu-id="c9979-110">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="c9979-110">\<commonParameters></span></span>  
<span data-ttu-id="c9979-111">\<add></span><span class="sxs-lookup"><span data-stu-id="c9979-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9979-112">語法</span><span class="sxs-lookup"><span data-stu-id="c9979-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9979-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9979-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c9979-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9979-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9979-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c9979-115">Attributes</span></span>  
  
|<span data-ttu-id="c9979-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c9979-116">Attribute</span></span>|<span data-ttu-id="c9979-117">描述</span><span class="sxs-lookup"><span data-stu-id="c9979-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9979-118">name</span><span class="sxs-lookup"><span data-stu-id="c9979-118">name</span></span>|<span data-ttu-id="c9979-119">為服務指定的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c9979-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="c9979-120">value</span><span class="sxs-lookup"><span data-stu-id="c9979-120">value</span></span>|<span data-ttu-id="c9979-121">為服務指定的參數值。</span><span class="sxs-lookup"><span data-stu-id="c9979-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9979-122">子元素</span><span class="sxs-lookup"><span data-stu-id="c9979-122">Child Elements</span></span>  
 <span data-ttu-id="c9979-123">無。</span><span class="sxs-lookup"><span data-stu-id="c9979-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9979-124">父項目</span><span class="sxs-lookup"><span data-stu-id="c9979-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c9979-125">項目</span><span class="sxs-lookup"><span data-stu-id="c9979-125">Element</span></span>|<span data-ttu-id="c9979-126">描述</span><span class="sxs-lookup"><span data-stu-id="c9979-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9979-127">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="c9979-127">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="c9979-128">服務所使用的一般參數集合。</span><span class="sxs-lookup"><span data-stu-id="c9979-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="c9979-129">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="c9979-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9979-130">備註</span><span class="sxs-lookup"><span data-stu-id="c9979-130">Remarks</span></span>  
 <span data-ttu-id="c9979-131">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="c9979-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="c9979-132">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c9979-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="c9979-133">請注意，`EnableRetries`參數可以設定在的全域層級 (如中所示*CommonParameters*區段) 或針對個別支援的服務`EnableRetries`(如中所示*Services*一節)。</span><span class="sxs-lookup"><span data-stu-id="c9979-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="c9979-134">如需使用組態檔來控制行為的詳細資訊<xref:System.Workflow.Runtime.WorkflowRuntime>物件的 Windows Workflow Foundation 主應用程式，請參閱[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="c9979-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9979-135">範例</span><span class="sxs-lookup"><span data-stu-id="c9979-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9979-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9979-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="c9979-137">[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c9979-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="c9979-138">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="c9979-138">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
