---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3be696133bff5c1fc8858ab31093866ed05c98a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="0137e-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="0137e-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="0137e-103">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="0137e-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="0137e-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0137e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0137e-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0137e-105">\<behaviors></span></span>  
<span data-ttu-id="0137e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0137e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0137e-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0137e-107">\<behavior></span></span>  
<span data-ttu-id="0137e-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="0137e-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0137e-109">語法</span><span class="sxs-lookup"><span data-stu-id="0137e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0137e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0137e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0137e-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0137e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0137e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0137e-112">Attributes</span></span>  
  
|<span data-ttu-id="0137e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0137e-113">Attribute</span></span>|<span data-ttu-id="0137e-114">描述</span><span class="sxs-lookup"><span data-stu-id="0137e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0137e-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="0137e-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="0137e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="0137e-116">Child Elements</span></span>  
 <span data-ttu-id="0137e-117">無。</span><span class="sxs-lookup"><span data-stu-id="0137e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0137e-118">父項目</span><span class="sxs-lookup"><span data-stu-id="0137e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0137e-119">項目</span><span class="sxs-lookup"><span data-stu-id="0137e-119">Element</span></span>|<span data-ttu-id="0137e-120">描述</span><span class="sxs-lookup"><span data-stu-id="0137e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0137e-121">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0137e-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0137e-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="0137e-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0137e-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="0137e-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
