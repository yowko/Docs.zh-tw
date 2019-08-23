---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947152"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="07569-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="07569-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="07569-102">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="07569-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="07569-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="07569-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="07569-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="07569-104">\<behaviors></span></span>  
<span data-ttu-id="07569-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="07569-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="07569-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="07569-106">\<behavior></span></span>  
<span data-ttu-id="07569-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="07569-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07569-108">語法</span><span class="sxs-lookup"><span data-stu-id="07569-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07569-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="07569-109">Attributes and Elements</span></span>  
 <span data-ttu-id="07569-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="07569-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07569-111">屬性</span><span class="sxs-lookup"><span data-stu-id="07569-111">Attributes</span></span>  
  
|<span data-ttu-id="07569-112">屬性</span><span class="sxs-lookup"><span data-stu-id="07569-112">Attribute</span></span>|<span data-ttu-id="07569-113">說明</span><span class="sxs-lookup"><span data-stu-id="07569-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07569-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="07569-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="07569-115">子元素</span><span class="sxs-lookup"><span data-stu-id="07569-115">Child Elements</span></span>  
 <span data-ttu-id="07569-116">無。</span><span class="sxs-lookup"><span data-stu-id="07569-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07569-117">父項目</span><span class="sxs-lookup"><span data-stu-id="07569-117">Parent Elements</span></span>  
  
|<span data-ttu-id="07569-118">項目</span><span class="sxs-lookup"><span data-stu-id="07569-118">Element</span></span>|<span data-ttu-id="07569-119">描述</span><span class="sxs-lookup"><span data-stu-id="07569-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07569-120">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="07569-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="07569-121">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="07569-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07569-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07569-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
