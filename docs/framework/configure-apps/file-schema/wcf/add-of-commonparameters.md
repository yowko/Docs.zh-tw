---
title: <add> 的 <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 8328b6d08c1b57ad7a899c8cb489e07037e5af09
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558157"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="3b2d9-102">\<add> 的 \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="3b2d9-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="3b2d9-103">指定跨多項服務全域使用之名稱/值組的參數。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="3b2d9-104">這個參數通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="3b2d9-105">語法</span><span class="sxs-lookup"><span data-stu-id="3b2d9-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b2d9-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3b2d9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3b2d9-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b2d9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3b2d9-108">Attributes</span></span>  
  
|<span data-ttu-id="3b2d9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3b2d9-109">Attribute</span></span>|<span data-ttu-id="3b2d9-110">描述</span><span class="sxs-lookup"><span data-stu-id="3b2d9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b2d9-111">NAME</span><span class="sxs-lookup"><span data-stu-id="3b2d9-111">name</span></span>|<span data-ttu-id="3b2d9-112">為服務指定的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="3b2d9-113">值</span><span class="sxs-lookup"><span data-stu-id="3b2d9-113">value</span></span>|<span data-ttu-id="3b2d9-114">為服務指定的參數值。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b2d9-115">子元素</span><span class="sxs-lookup"><span data-stu-id="3b2d9-115">Child Elements</span></span>  
 <span data-ttu-id="3b2d9-116">無。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b2d9-117">父項目</span><span class="sxs-lookup"><span data-stu-id="3b2d9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3b2d9-118">項目</span><span class="sxs-lookup"><span data-stu-id="3b2d9-118">Element</span></span>|<span data-ttu-id="3b2d9-119">描述</span><span class="sxs-lookup"><span data-stu-id="3b2d9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="3b2d9-120">服務所使用的一般參數集合。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="3b2d9-121">這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b2d9-122">備註</span><span class="sxs-lookup"><span data-stu-id="3b2d9-122">Remarks</span></span>  
 <span data-ttu-id="3b2d9-123">`<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="3b2d9-124">針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3b2d9-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="3b2d9-125">請注意，您 `EnableRetries` 可以在全域層級設定參數 (如 *CommonParameters* 一節所示) 或個別支援 (的服務， `EnableRetries` 如 [ *服務* ] 區段) 所示。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="3b2d9-126">如需使用設定檔來控制 <xref:System.Workflow.Runtime.WorkflowRuntime> Windows Workflow Foundation 主應用程式之物件行為的詳細資訊，請參閱 [工作流程設定檔](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="3b2d9-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b2d9-127">範例</span><span class="sxs-lookup"><span data-stu-id="3b2d9-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="3b2d9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b2d9-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="3b2d9-129">[工作流程組態檔](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3b2d9-129">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
