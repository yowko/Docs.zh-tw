---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397527"
---
# \<workflowInstanceManagement>
<span data-ttu-id="3128b-101">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="3128b-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="3128b-102">語法</span><span class="sxs-lookup"><span data-stu-id="3128b-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3128b-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3128b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3128b-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3128b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3128b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="3128b-105">Attributes</span></span>  
  
|<span data-ttu-id="3128b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3128b-106">Attribute</span></span>|<span data-ttu-id="3128b-107">描述</span><span class="sxs-lookup"><span data-stu-id="3128b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3128b-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="3128b-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="3128b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="3128b-109">Child Elements</span></span>  
 <span data-ttu-id="3128b-110">無。</span><span class="sxs-lookup"><span data-stu-id="3128b-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3128b-111">父項目</span><span class="sxs-lookup"><span data-stu-id="3128b-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3128b-112">元素</span><span class="sxs-lookup"><span data-stu-id="3128b-112">Element</span></span>|<span data-ttu-id="3128b-113">描述</span><span class="sxs-lookup"><span data-stu-id="3128b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3128b-114">\<behavior>的\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3128b-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3128b-115">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="3128b-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3128b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3128b-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
