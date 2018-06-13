---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: d9db6ecc2e95e0d1ec5738f1d2f4a09a89c57f21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755132"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="4e4cc-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="4e4cc-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="4e4cc-103">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4e4cc-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="4e4cc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e4cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e4cc-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4e4cc-105">\<behaviors></span></span>  
<span data-ttu-id="4e4cc-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4e4cc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4e4cc-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4e4cc-107">\<behavior></span></span>  
<span data-ttu-id="4e4cc-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="4e4cc-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e4cc-109">語法</span><span class="sxs-lookup"><span data-stu-id="4e4cc-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e4cc-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e4cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4e4cc-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e4cc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e4cc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4e4cc-112">Attributes</span></span>  
  
|<span data-ttu-id="4e4cc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4e4cc-113">Attribute</span></span>|<span data-ttu-id="4e4cc-114">描述</span><span class="sxs-lookup"><span data-stu-id="4e4cc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e4cc-115">action</span><span class="sxs-lookup"><span data-stu-id="4e4cc-115">action</span></span>|<span data-ttu-id="4e4cc-116">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4e4cc-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="4e4cc-117">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="4e4cc-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e4cc-118">子項目</span><span class="sxs-lookup"><span data-stu-id="4e4cc-118">Child Elements</span></span>  
 <span data-ttu-id="4e4cc-119">無。</span><span class="sxs-lookup"><span data-stu-id="4e4cc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e4cc-120">父項目</span><span class="sxs-lookup"><span data-stu-id="4e4cc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4e4cc-121">項目</span><span class="sxs-lookup"><span data-stu-id="4e4cc-121">Element</span></span>|<span data-ttu-id="4e4cc-122">描述</span><span class="sxs-lookup"><span data-stu-id="4e4cc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e4cc-123">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4e4cc-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4e4cc-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4e4cc-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e4cc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e4cc-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
