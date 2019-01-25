---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 5c5dddc6d126811d7fd1eaae2f85df1e42c1cd41
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700867"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="c2f80-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="c2f80-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="c2f80-103">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c2f80-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="c2f80-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c2f80-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c2f80-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c2f80-105">\<behaviors></span></span>  
<span data-ttu-id="c2f80-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c2f80-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c2f80-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c2f80-107">\<behavior></span></span>  
<span data-ttu-id="c2f80-108">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="c2f80-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f80-109">語法</span><span class="sxs-lookup"><span data-stu-id="c2f80-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2f80-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c2f80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c2f80-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c2f80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2f80-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c2f80-112">Attributes</span></span>  
  
|<span data-ttu-id="c2f80-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c2f80-113">Attribute</span></span>|<span data-ttu-id="c2f80-114">描述</span><span class="sxs-lookup"><span data-stu-id="c2f80-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2f80-115">action</span><span class="sxs-lookup"><span data-stu-id="c2f80-115">action</span></span>|<span data-ttu-id="c2f80-116">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c2f80-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="c2f80-117">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="c2f80-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2f80-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c2f80-118">Child Elements</span></span>  
 <span data-ttu-id="c2f80-119">無。</span><span class="sxs-lookup"><span data-stu-id="c2f80-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2f80-120">父項目</span><span class="sxs-lookup"><span data-stu-id="c2f80-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c2f80-121">項目</span><span class="sxs-lookup"><span data-stu-id="c2f80-121">Element</span></span>|<span data-ttu-id="c2f80-122">描述</span><span class="sxs-lookup"><span data-stu-id="c2f80-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2f80-123">\<行為 > 的\<v ></span><span class="sxs-lookup"><span data-stu-id="c2f80-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c2f80-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="c2f80-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2f80-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2f80-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
