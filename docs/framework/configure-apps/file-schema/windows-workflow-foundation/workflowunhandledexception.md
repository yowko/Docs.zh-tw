---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398558"
---
# \<workflowUnhandledException>
<span data-ttu-id="a51f1-101">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a51f1-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="a51f1-102">語法</span><span class="sxs-lookup"><span data-stu-id="a51f1-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a51f1-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a51f1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a51f1-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a51f1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a51f1-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a51f1-105">Attributes</span></span>  
  
|<span data-ttu-id="a51f1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a51f1-106">Attribute</span></span>|<span data-ttu-id="a51f1-107">描述</span><span class="sxs-lookup"><span data-stu-id="a51f1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a51f1-108">動作</span><span class="sxs-lookup"><span data-stu-id="a51f1-108">action</span></span>|<span data-ttu-id="a51f1-109">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a51f1-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="a51f1-110">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="a51f1-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a51f1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a51f1-111">Child Elements</span></span>  
 <span data-ttu-id="a51f1-112">無。</span><span class="sxs-lookup"><span data-stu-id="a51f1-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a51f1-113">父項目</span><span class="sxs-lookup"><span data-stu-id="a51f1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a51f1-114">元素</span><span class="sxs-lookup"><span data-stu-id="a51f1-114">Element</span></span>|<span data-ttu-id="a51f1-115">描述</span><span class="sxs-lookup"><span data-stu-id="a51f1-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a51f1-116">\<behavior>的\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a51f1-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a51f1-117">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="a51f1-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a51f1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a51f1-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
