---
title: '&lt;bufferReceive&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0fc3fb901e0f70b616f403b98abc7b9645b2b44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="c33ad-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="c33ad-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="c33ad-103">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="c33ad-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="c33ad-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c33ad-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c33ad-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c33ad-105">\<behaviors></span></span>  
<span data-ttu-id="c33ad-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c33ad-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c33ad-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c33ad-107">\<behavior></span></span>  
<span data-ttu-id="c33ad-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="c33ad-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c33ad-109">語法</span><span class="sxs-lookup"><span data-stu-id="c33ad-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c33ad-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c33ad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c33ad-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c33ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c33ad-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c33ad-112">Attributes</span></span>  
  
|<span data-ttu-id="c33ad-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c33ad-113">Attribute</span></span>|<span data-ttu-id="c33ad-114">描述</span><span class="sxs-lookup"><span data-stu-id="c33ad-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c33ad-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="c33ad-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="c33ad-116">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="c33ad-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="c33ad-117">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="c33ad-117">The default value is 512.</span></span> <span data-ttu-id="c33ad-118">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="c33ad-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c33ad-119">子元素</span><span class="sxs-lookup"><span data-stu-id="c33ad-119">Child Elements</span></span>  
 <span data-ttu-id="c33ad-120">無。</span><span class="sxs-lookup"><span data-stu-id="c33ad-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c33ad-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c33ad-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c33ad-122">項目</span><span class="sxs-lookup"><span data-stu-id="c33ad-122">Element</span></span>|<span data-ttu-id="c33ad-123">說明</span><span class="sxs-lookup"><span data-stu-id="c33ad-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c33ad-124">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c33ad-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c33ad-125">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="c33ad-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c33ad-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c33ad-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
