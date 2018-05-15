---
title: '&lt;bufferReceive&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 07d5b66b14d9495808f972734cdce4476efaefde
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="f8366-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="f8366-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="f8366-103">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="f8366-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="f8366-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f8366-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8366-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="f8366-105">\<behaviors></span></span>  
<span data-ttu-id="f8366-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f8366-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f8366-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="f8366-107">\<behavior></span></span>  
<span data-ttu-id="f8366-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="f8366-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8366-109">語法</span><span class="sxs-lookup"><span data-stu-id="f8366-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8366-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f8366-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f8366-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f8366-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8366-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f8366-112">Attributes</span></span>  
  
|<span data-ttu-id="f8366-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f8366-113">Attribute</span></span>|<span data-ttu-id="f8366-114">描述</span><span class="sxs-lookup"><span data-stu-id="f8366-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8366-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="f8366-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="f8366-116">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="f8366-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="f8366-117">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="f8366-117">The default value is 512.</span></span> <span data-ttu-id="f8366-118">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="f8366-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8366-119">子項目</span><span class="sxs-lookup"><span data-stu-id="f8366-119">Child Elements</span></span>  
 <span data-ttu-id="f8366-120">無。</span><span class="sxs-lookup"><span data-stu-id="f8366-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8366-121">父項目</span><span class="sxs-lookup"><span data-stu-id="f8366-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f8366-122">項目</span><span class="sxs-lookup"><span data-stu-id="f8366-122">Element</span></span>|<span data-ttu-id="f8366-123">描述</span><span class="sxs-lookup"><span data-stu-id="f8366-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8366-124">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f8366-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f8366-125">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="f8366-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8366-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8366-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
