---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191610"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="ee606-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ee606-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="ee606-102">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="ee606-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="ee606-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ee606-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee606-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="ee606-104">\<behaviors></span></span>  
<span data-ttu-id="ee606-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ee606-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ee606-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ee606-106">\<behavior></span></span>  
<span data-ttu-id="ee606-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ee606-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee606-108">語法</span><span class="sxs-lookup"><span data-stu-id="ee606-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee606-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ee606-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ee606-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ee606-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee606-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ee606-111">Attributes</span></span>  
  
|<span data-ttu-id="ee606-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ee606-112">Attribute</span></span>|<span data-ttu-id="ee606-113">描述</span><span class="sxs-lookup"><span data-stu-id="ee606-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee606-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="ee606-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="ee606-115">子元素</span><span class="sxs-lookup"><span data-stu-id="ee606-115">Child Elements</span></span>  
 <span data-ttu-id="ee606-116">無。</span><span class="sxs-lookup"><span data-stu-id="ee606-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee606-117">父項目</span><span class="sxs-lookup"><span data-stu-id="ee606-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ee606-118">項目</span><span class="sxs-lookup"><span data-stu-id="ee606-118">Element</span></span>|<span data-ttu-id="ee606-119">描述</span><span class="sxs-lookup"><span data-stu-id="ee606-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee606-120">\<行為 > 的\<v ></span><span class="sxs-lookup"><span data-stu-id="ee606-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ee606-121">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="ee606-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee606-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee606-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
