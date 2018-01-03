---
title: '&lt;workflowUnhandledException&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4266eb6480c98c7ea1b96f2325a018b0fdcba041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="7f9f4-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="7f9f4-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="7f9f4-103">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="7f9f4-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="7f9f4-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7f9f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f9f4-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7f9f4-105">\<behaviors></span></span>  
<span data-ttu-id="7f9f4-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f9f4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7f9f4-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7f9f4-107">\<behavior></span></span>  
<span data-ttu-id="7f9f4-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="7f9f4-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9f4-109">語法</span><span class="sxs-lookup"><span data-stu-id="7f9f4-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f9f4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f9f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f9f4-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7f9f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f9f4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7f9f4-112">Attributes</span></span>  
  
|<span data-ttu-id="7f9f4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7f9f4-113">Attribute</span></span>|<span data-ttu-id="7f9f4-114">描述</span><span class="sxs-lookup"><span data-stu-id="7f9f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f9f4-115">action</span><span class="sxs-lookup"><span data-stu-id="7f9f4-115">action</span></span>|<span data-ttu-id="7f9f4-116">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="7f9f4-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="7f9f4-117">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="7f9f4-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f9f4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="7f9f4-118">Child Elements</span></span>  
 <span data-ttu-id="7f9f4-119">無。</span><span class="sxs-lookup"><span data-stu-id="7f9f4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f9f4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="7f9f4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7f9f4-121">項目</span><span class="sxs-lookup"><span data-stu-id="7f9f4-121">Element</span></span>|<span data-ttu-id="7f9f4-122">描述</span><span class="sxs-lookup"><span data-stu-id="7f9f4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f9f4-123">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f9f4-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7f9f4-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="7f9f4-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f9f4-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9f4-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
