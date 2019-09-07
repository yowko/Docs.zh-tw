---
title: <add> 的 <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400672"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="67474-102">\<新增 commonParameters > \<的 ></span><span class="sxs-lookup"><span data-stu-id="67474-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="67474-103">指定跨多項服務全域使用之名稱/值組的參數。</span><span class="sxs-lookup"><span data-stu-id="67474-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="67474-104">這個參數通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="67474-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="67474-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="67474-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="67474-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="67474-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="67474-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="67474-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="67474-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="67474-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="67474-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="67474-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="67474-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowRuntime >** ](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="67474-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="67474-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<commonParameters >** ](commonparameters.md)</span><span class="sxs-lookup"><span data-stu-id="67474-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)</span></span>\
<span data-ttu-id="67474-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="67474-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67474-113">語法</span><span class="sxs-lookup"><span data-stu-id="67474-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67474-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67474-114">Attributes and Elements</span></span>  
 <span data-ttu-id="67474-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="67474-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67474-116">屬性</span><span class="sxs-lookup"><span data-stu-id="67474-116">Attributes</span></span>  
  
|<span data-ttu-id="67474-117">屬性</span><span class="sxs-lookup"><span data-stu-id="67474-117">Attribute</span></span>|<span data-ttu-id="67474-118">說明</span><span class="sxs-lookup"><span data-stu-id="67474-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67474-119">NAME</span><span class="sxs-lookup"><span data-stu-id="67474-119">name</span></span>|<span data-ttu-id="67474-120">為服務指定的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="67474-120">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="67474-121">value</span><span class="sxs-lookup"><span data-stu-id="67474-121">value</span></span>|<span data-ttu-id="67474-122">為服務指定的參數值。</span><span class="sxs-lookup"><span data-stu-id="67474-122">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67474-123">子元素</span><span class="sxs-lookup"><span data-stu-id="67474-123">Child Elements</span></span>  
 <span data-ttu-id="67474-124">無。</span><span class="sxs-lookup"><span data-stu-id="67474-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67474-125">父項目</span><span class="sxs-lookup"><span data-stu-id="67474-125">Parent Elements</span></span>  
  
|<span data-ttu-id="67474-126">項目</span><span class="sxs-lookup"><span data-stu-id="67474-126">Element</span></span>|<span data-ttu-id="67474-127">描述</span><span class="sxs-lookup"><span data-stu-id="67474-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67474-128">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="67474-128">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="67474-129">服務所使用的一般參數集合。</span><span class="sxs-lookup"><span data-stu-id="67474-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="67474-130">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="67474-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67474-131">備註</span><span class="sxs-lookup"><span data-stu-id="67474-131">Remarks</span></span>  
 <span data-ttu-id="67474-132">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="67474-132">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="67474-133">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="67474-133">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="67474-134">請注意， `EnableRetries`您可以在全域層級（如*CommonParameters*一節所示），或針對支援`EnableRetries`的個別服務（如 [*服務*] 區段中所示）設定參數。</span><span class="sxs-lookup"><span data-stu-id="67474-134">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="67474-135">如需使用設定檔控制 Windows Workflow Foundation 主應用程式之<xref:System.Workflow.Runtime.WorkflowRuntime>物件行為的詳細資訊，請參閱[工作流程設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="67474-135">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67474-136">範例</span><span class="sxs-lookup"><span data-stu-id="67474-136">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="67474-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67474-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="67474-138">[工作流程設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="67474-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="67474-139">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="67474-139">\<commonParameters></span></span>](commonparameters.md)
