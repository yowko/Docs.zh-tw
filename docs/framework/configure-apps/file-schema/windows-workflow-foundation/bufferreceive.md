---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 16d4546bce461b55695e0deed093396ce1c2b0b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189561"
---
# \<bufferReceive>

<span data-ttu-id="f0a8f-101">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="f0a8f-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0a8f-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0a8f-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f0a8f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f0a8f-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0a8f-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f0a8f-105">Attributes</span></span>  
  
|<span data-ttu-id="f0a8f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f0a8f-106">Attribute</span></span>|<span data-ttu-id="f0a8f-107">描述</span><span class="sxs-lookup"><span data-stu-id="f0a8f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0a8f-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="f0a8f-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="f0a8f-109">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="f0a8f-110">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-110">The default value is 512.</span></span> <span data-ttu-id="f0a8f-111">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0a8f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f0a8f-112">Child Elements</span></span>  

 <span data-ttu-id="f0a8f-113">無。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0a8f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="f0a8f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f0a8f-115">項目</span><span class="sxs-lookup"><span data-stu-id="f0a8f-115">Element</span></span>|<span data-ttu-id="f0a8f-116">描述</span><span class="sxs-lookup"><span data-stu-id="f0a8f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0a8f-117">\<behavior> 次數 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f0a8f-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f0a8f-118">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="f0a8f-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0a8f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0a8f-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
