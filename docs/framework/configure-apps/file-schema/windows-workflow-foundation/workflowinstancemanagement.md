---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397527"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="3e380-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="3e380-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="3e380-102">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="3e380-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="3e380-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e380-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e380-104">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3e380-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="3e380-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3e380-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3e380-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3e380-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3e380-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3e380-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3e380-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceManagement >**</span><span class="sxs-lookup"><span data-stu-id="3e380-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e380-109">語法</span><span class="sxs-lookup"><span data-stu-id="3e380-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e380-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3e380-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e380-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3e380-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e380-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3e380-112">Attributes</span></span>  
  
|<span data-ttu-id="3e380-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3e380-113">Attribute</span></span>|<span data-ttu-id="3e380-114">說明</span><span class="sxs-lookup"><span data-stu-id="3e380-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e380-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="3e380-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="3e380-116">子元素</span><span class="sxs-lookup"><span data-stu-id="3e380-116">Child Elements</span></span>  
 <span data-ttu-id="3e380-117">無。</span><span class="sxs-lookup"><span data-stu-id="3e380-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e380-118">父項目</span><span class="sxs-lookup"><span data-stu-id="3e380-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3e380-119">項目</span><span class="sxs-lookup"><span data-stu-id="3e380-119">Element</span></span>|<span data-ttu-id="3e380-120">描述</span><span class="sxs-lookup"><span data-stu-id="3e380-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e380-121">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3e380-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3e380-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="3e380-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e380-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e380-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
