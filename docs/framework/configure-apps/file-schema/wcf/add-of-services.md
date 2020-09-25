---
title: <add> 的 <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 31a4d2a5a3baf3d53cf18ab6e37edfaf7acb8540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204979"
---
# <a name="add-of-services"></a><span data-ttu-id="0010b-102">\<add> 的 \<services></span><span class="sxs-lookup"><span data-stu-id="0010b-102">\<add> of \<services></span></span>

<span data-ttu-id="0010b-103">指定實例的設定， <xref:System.Workflow.Runtime.WorkflowRuntime> 以裝載以工作流程為基礎的 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="0010b-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="0010b-104">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0010b-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0010b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0010b-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0010b-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0010b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0010b-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0010b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0010b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0010b-108">Attributes</span></span>  
  
|<span data-ttu-id="0010b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0010b-109">Attribute</span></span>|<span data-ttu-id="0010b-110">描述</span><span class="sxs-lookup"><span data-stu-id="0010b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0010b-111">type</span><span class="sxs-lookup"><span data-stu-id="0010b-111">type</span></span>|<span data-ttu-id="0010b-112">字串，指定要初始化之服務的組件限定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0010b-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="0010b-113">指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="0010b-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="0010b-114">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0010b-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0010b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="0010b-115">Child Elements</span></span>  

 <span data-ttu-id="0010b-116">無。</span><span class="sxs-lookup"><span data-stu-id="0010b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0010b-117">父項目</span><span class="sxs-lookup"><span data-stu-id="0010b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0010b-118">項目</span><span class="sxs-lookup"><span data-stu-id="0010b-118">Element</span></span>|<span data-ttu-id="0010b-119">描述</span><span class="sxs-lookup"><span data-stu-id="0010b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="0010b-120">要加入至 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎之服務的集合。</span><span class="sxs-lookup"><span data-stu-id="0010b-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="0010b-121">此項目的型別為 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0010b-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="0010b-122">集合中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="0010b-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="0010b-123">因此，集合中所指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="0010b-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="0010b-124">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0010b-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0010b-125">備註</span><span class="sxs-lookup"><span data-stu-id="0010b-125">Remarks</span></span>  

 <span data-ttu-id="0010b-126">此項目中所指定的服務會由工作流程執行階段引擎初始化，並在呼叫適當的 <xref:System.Workflow.Runtime.WorkflowRuntime> 建構函式時新增至其服務中。</span><span class="sxs-lookup"><span data-stu-id="0010b-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="0010b-127">因此，指定的服務必須遵循有關其建構函式之簽章的特定規則。</span><span class="sxs-lookup"><span data-stu-id="0010b-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="0010b-128">如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="0010b-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0010b-129">範例</span><span class="sxs-lookup"><span data-stu-id="0010b-129">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="0010b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0010b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="0010b-131">[工作流程組態檔](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0010b-131">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
