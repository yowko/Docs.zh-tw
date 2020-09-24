---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 6e3993e43aac746f380a30341fe4ebffcd257c5f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148512"
---
# \<workflowUnhandledException>

<span data-ttu-id="4123a-101">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4123a-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="4123a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="4123a-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4123a-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4123a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4123a-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4123a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4123a-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4123a-105">Attributes</span></span>  
  
|<span data-ttu-id="4123a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4123a-106">Attribute</span></span>|<span data-ttu-id="4123a-107">描述</span><span class="sxs-lookup"><span data-stu-id="4123a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4123a-108">動作</span><span class="sxs-lookup"><span data-stu-id="4123a-108">action</span></span>|<span data-ttu-id="4123a-109">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4123a-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="4123a-110">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="4123a-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4123a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4123a-111">Child Elements</span></span>  

 <span data-ttu-id="4123a-112">無。</span><span class="sxs-lookup"><span data-stu-id="4123a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4123a-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4123a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4123a-114">項目</span><span class="sxs-lookup"><span data-stu-id="4123a-114">Element</span></span>|<span data-ttu-id="4123a-115">描述</span><span class="sxs-lookup"><span data-stu-id="4123a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4123a-116">\<behavior> 次數 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4123a-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4123a-117">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4123a-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4123a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4123a-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
