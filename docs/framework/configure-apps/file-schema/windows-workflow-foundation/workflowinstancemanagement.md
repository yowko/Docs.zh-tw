---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 532d4c31a582b2b0cd90f6f42b20e00790f9ab02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148655"
---
# \<workflowInstanceManagement>

<span data-ttu-id="b13e9-101">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="b13e9-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="b13e9-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b13e9-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b13e9-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b13e9-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b13e9-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b13e9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b13e9-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b13e9-105">Attributes</span></span>  
  
|<span data-ttu-id="b13e9-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b13e9-106">Attribute</span></span>|<span data-ttu-id="b13e9-107">描述</span><span class="sxs-lookup"><span data-stu-id="b13e9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b13e9-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="b13e9-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="b13e9-109">子元素</span><span class="sxs-lookup"><span data-stu-id="b13e9-109">Child Elements</span></span>  

 <span data-ttu-id="b13e9-110">無。</span><span class="sxs-lookup"><span data-stu-id="b13e9-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b13e9-111">父項目</span><span class="sxs-lookup"><span data-stu-id="b13e9-111">Parent Elements</span></span>  
  
|<span data-ttu-id="b13e9-112">項目</span><span class="sxs-lookup"><span data-stu-id="b13e9-112">Element</span></span>|<span data-ttu-id="b13e9-113">描述</span><span class="sxs-lookup"><span data-stu-id="b13e9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b13e9-114">\<behavior> 次數 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b13e9-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b13e9-115">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="b13e9-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b13e9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b13e9-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
