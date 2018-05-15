---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: d86b0f61c6741fa156e04da75a62853f459324d1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="2cd01-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="2cd01-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="2cd01-103">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="2cd01-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="2cd01-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2cd01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2cd01-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="2cd01-105">\<behaviors></span></span>  
<span data-ttu-id="2cd01-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2cd01-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2cd01-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="2cd01-107">\<behavior></span></span>  
<span data-ttu-id="2cd01-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="2cd01-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd01-109">語法</span><span class="sxs-lookup"><span data-stu-id="2cd01-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cd01-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2cd01-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2cd01-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2cd01-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cd01-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2cd01-112">Attributes</span></span>  
  
|<span data-ttu-id="2cd01-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2cd01-113">Attribute</span></span>|<span data-ttu-id="2cd01-114">描述</span><span class="sxs-lookup"><span data-stu-id="2cd01-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2cd01-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="2cd01-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="2cd01-116">子項目</span><span class="sxs-lookup"><span data-stu-id="2cd01-116">Child Elements</span></span>  
 <span data-ttu-id="2cd01-117">無。</span><span class="sxs-lookup"><span data-stu-id="2cd01-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cd01-118">父項目</span><span class="sxs-lookup"><span data-stu-id="2cd01-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2cd01-119">項目</span><span class="sxs-lookup"><span data-stu-id="2cd01-119">Element</span></span>|<span data-ttu-id="2cd01-120">描述</span><span class="sxs-lookup"><span data-stu-id="2cd01-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cd01-121">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2cd01-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="2cd01-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="2cd01-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cd01-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cd01-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
