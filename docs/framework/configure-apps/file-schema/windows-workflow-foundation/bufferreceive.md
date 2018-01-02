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
ms.workload: dotnet
ms.openlocfilehash: 5b5b6176e7c5b982bc9f41b13c669af104bf784f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="a3492-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="a3492-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="a3492-103">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3492-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="a3492-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a3492-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3492-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a3492-105">\<behaviors></span></span>  
<span data-ttu-id="a3492-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a3492-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a3492-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a3492-107">\<behavior></span></span>  
<span data-ttu-id="a3492-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="a3492-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3492-109">語法</span><span class="sxs-lookup"><span data-stu-id="a3492-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3492-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3492-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3492-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a3492-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3492-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a3492-112">Attributes</span></span>  
  
|<span data-ttu-id="a3492-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a3492-113">Attribute</span></span>|<span data-ttu-id="a3492-114">描述</span><span class="sxs-lookup"><span data-stu-id="a3492-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3492-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="a3492-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="a3492-116">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="a3492-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="a3492-117">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="a3492-117">The default value is 512.</span></span> <span data-ttu-id="a3492-118">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="a3492-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3492-119">子元素</span><span class="sxs-lookup"><span data-stu-id="a3492-119">Child Elements</span></span>  
 <span data-ttu-id="a3492-120">無。</span><span class="sxs-lookup"><span data-stu-id="a3492-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3492-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a3492-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a3492-122">項目</span><span class="sxs-lookup"><span data-stu-id="a3492-122">Element</span></span>|<span data-ttu-id="a3492-123">描述</span><span class="sxs-lookup"><span data-stu-id="a3492-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3492-124">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a3492-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a3492-125">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="a3492-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3492-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="a3492-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
