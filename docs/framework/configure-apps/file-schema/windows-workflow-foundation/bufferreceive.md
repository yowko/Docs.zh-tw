---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 6ed37d73440dac22288ae1da526d81b2d0b990a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286620"
---
# <a name="bufferreceive"></a><span data-ttu-id="04803-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="04803-101">\<bufferReceive></span></span>
<span data-ttu-id="04803-102">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="04803-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="04803-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04803-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="04803-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="04803-104">\<behaviors></span></span>  
<span data-ttu-id="04803-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="04803-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="04803-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="04803-106">\<behavior></span></span>  
<span data-ttu-id="04803-107">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="04803-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04803-108">語法</span><span class="sxs-lookup"><span data-stu-id="04803-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04803-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04803-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04803-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="04803-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04803-111">屬性</span><span class="sxs-lookup"><span data-stu-id="04803-111">Attributes</span></span>  
  
|<span data-ttu-id="04803-112">屬性</span><span class="sxs-lookup"><span data-stu-id="04803-112">Attribute</span></span>|<span data-ttu-id="04803-113">描述</span><span class="sxs-lookup"><span data-stu-id="04803-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04803-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="04803-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="04803-115">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="04803-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="04803-116">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="04803-116">The default value is 512.</span></span> <span data-ttu-id="04803-117">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="04803-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04803-118">子元素</span><span class="sxs-lookup"><span data-stu-id="04803-118">Child Elements</span></span>  
 <span data-ttu-id="04803-119">無。</span><span class="sxs-lookup"><span data-stu-id="04803-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04803-120">父項目</span><span class="sxs-lookup"><span data-stu-id="04803-120">Parent Elements</span></span>  
  
|<span data-ttu-id="04803-121">項目</span><span class="sxs-lookup"><span data-stu-id="04803-121">Element</span></span>|<span data-ttu-id="04803-122">描述</span><span class="sxs-lookup"><span data-stu-id="04803-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04803-123">\<行為 > 的\<v ></span><span class="sxs-lookup"><span data-stu-id="04803-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="04803-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="04803-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04803-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04803-125">See also</span></span>
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
