---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: caf5be7aaff0df436be3a1d618a9f89bb32e6bb7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254843"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="c580d-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="c580d-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="c580d-102">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c580d-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="c580d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c580d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c580d-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c580d-104">\<behaviors></span></span>  
<span data-ttu-id="c580d-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c580d-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c580d-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c580d-106">\<behavior></span></span>  
<span data-ttu-id="c580d-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="c580d-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c580d-108">語法</span><span class="sxs-lookup"><span data-stu-id="c580d-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c580d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c580d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c580d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c580d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c580d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c580d-111">Attributes</span></span>  
  
|<span data-ttu-id="c580d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c580d-112">Attribute</span></span>|<span data-ttu-id="c580d-113">描述</span><span class="sxs-lookup"><span data-stu-id="c580d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c580d-114">action</span><span class="sxs-lookup"><span data-stu-id="c580d-114">action</span></span>|<span data-ttu-id="c580d-115">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c580d-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="c580d-116">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="c580d-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c580d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c580d-117">Child Elements</span></span>  
 <span data-ttu-id="c580d-118">無。</span><span class="sxs-lookup"><span data-stu-id="c580d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c580d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c580d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c580d-120">項目</span><span class="sxs-lookup"><span data-stu-id="c580d-120">Element</span></span>|<span data-ttu-id="c580d-121">描述</span><span class="sxs-lookup"><span data-stu-id="c580d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c580d-122">\<行為 > 的\<v ></span><span class="sxs-lookup"><span data-stu-id="c580d-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c580d-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="c580d-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c580d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c580d-124">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
