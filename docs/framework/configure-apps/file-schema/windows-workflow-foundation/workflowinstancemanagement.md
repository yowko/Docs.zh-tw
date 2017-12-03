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
ms.openlocfilehash: 28e0f2b0ed88ee73edb52a8c18346746beb34771
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="be1bb-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="be1bb-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="be1bb-103">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="be1bb-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="be1bb-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="be1bb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be1bb-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="be1bb-105">\<behaviors></span></span>  
<span data-ttu-id="be1bb-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="be1bb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="be1bb-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="be1bb-107">\<behavior></span></span>  
<span data-ttu-id="be1bb-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="be1bb-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1bb-109">語法</span><span class="sxs-lookup"><span data-stu-id="be1bb-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be1bb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="be1bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="be1bb-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="be1bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be1bb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="be1bb-112">Attributes</span></span>  
  
|<span data-ttu-id="be1bb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="be1bb-113">Attribute</span></span>|<span data-ttu-id="be1bb-114">描述</span><span class="sxs-lookup"><span data-stu-id="be1bb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be1bb-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="be1bb-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="be1bb-116">子元素</span><span class="sxs-lookup"><span data-stu-id="be1bb-116">Child Elements</span></span>  
 <span data-ttu-id="be1bb-117">無。</span><span class="sxs-lookup"><span data-stu-id="be1bb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be1bb-118">父項目</span><span class="sxs-lookup"><span data-stu-id="be1bb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="be1bb-119">項目</span><span class="sxs-lookup"><span data-stu-id="be1bb-119">Element</span></span>|<span data-ttu-id="be1bb-120">說明</span><span class="sxs-lookup"><span data-stu-id="be1bb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be1bb-121">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="be1bb-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="be1bb-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="be1bb-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be1bb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1bb-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
