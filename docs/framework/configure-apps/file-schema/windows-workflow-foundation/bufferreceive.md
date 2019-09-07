---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398840"
---
# <a name="bufferreceive"></a><span data-ttu-id="66d7e-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="66d7e-101">\<bufferReceive></span></span>
<span data-ttu-id="66d7e-102">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="66d7e-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="66d7e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66d7e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66d7e-104">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="66d7e-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="66d7e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="66d7e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="66d7e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="66d7e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="66d7e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="66d7e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="66d7e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bufferReceive >**</span><span class="sxs-lookup"><span data-stu-id="66d7e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d7e-109">語法</span><span class="sxs-lookup"><span data-stu-id="66d7e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66d7e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66d7e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="66d7e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66d7e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66d7e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="66d7e-112">Attributes</span></span>  
  
|<span data-ttu-id="66d7e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="66d7e-113">Attribute</span></span>|<span data-ttu-id="66d7e-114">描述</span><span class="sxs-lookup"><span data-stu-id="66d7e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66d7e-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="66d7e-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="66d7e-116">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="66d7e-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="66d7e-117">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="66d7e-117">The default value is 512.</span></span> <span data-ttu-id="66d7e-118">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="66d7e-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66d7e-119">子元素</span><span class="sxs-lookup"><span data-stu-id="66d7e-119">Child Elements</span></span>  
 <span data-ttu-id="66d7e-120">無。</span><span class="sxs-lookup"><span data-stu-id="66d7e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66d7e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="66d7e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="66d7e-122">項目</span><span class="sxs-lookup"><span data-stu-id="66d7e-122">Element</span></span>|<span data-ttu-id="66d7e-123">描述</span><span class="sxs-lookup"><span data-stu-id="66d7e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66d7e-124">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="66d7e-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="66d7e-125">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="66d7e-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66d7e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d7e-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
