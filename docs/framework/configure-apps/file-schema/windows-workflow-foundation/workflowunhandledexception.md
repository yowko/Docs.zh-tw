---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398558"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="bd16f-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="bd16f-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="bd16f-102">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="bd16f-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="bd16f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd16f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd16f-104">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bd16f-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="bd16f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bd16f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="bd16f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bd16f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="bd16f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bd16f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="bd16f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowUnhandledException >**</span><span class="sxs-lookup"><span data-stu-id="bd16f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd16f-109">語法</span><span class="sxs-lookup"><span data-stu-id="bd16f-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd16f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd16f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd16f-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bd16f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd16f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bd16f-112">Attributes</span></span>  
  
|<span data-ttu-id="bd16f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bd16f-113">Attribute</span></span>|<span data-ttu-id="bd16f-114">描述</span><span class="sxs-lookup"><span data-stu-id="bd16f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd16f-115">action</span><span class="sxs-lookup"><span data-stu-id="bd16f-115">action</span></span>|<span data-ttu-id="bd16f-116">字串，可指定發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="bd16f-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="bd16f-117">此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="bd16f-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd16f-118">子元素</span><span class="sxs-lookup"><span data-stu-id="bd16f-118">Child Elements</span></span>  
 <span data-ttu-id="bd16f-119">無。</span><span class="sxs-lookup"><span data-stu-id="bd16f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd16f-120">父項目</span><span class="sxs-lookup"><span data-stu-id="bd16f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bd16f-121">項目</span><span class="sxs-lookup"><span data-stu-id="bd16f-121">Element</span></span>|<span data-ttu-id="bd16f-122">描述</span><span class="sxs-lookup"><span data-stu-id="bd16f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd16f-123">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="bd16f-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="bd16f-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="bd16f-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd16f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd16f-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
