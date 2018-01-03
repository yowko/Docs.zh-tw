---
title: "&lt;synchronousReceive&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="7ccaf-102">&lt;synchronousReceive&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="7ccaf-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="7ccaf-103">這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="7ccaf-104">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="7ccaf-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7ccaf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ccaf-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7ccaf-106">\<behaviors></span></span>  
<span data-ttu-id="7ccaf-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7ccaf-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="7ccaf-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7ccaf-108">\<behavior></span></span>  
<span data-ttu-id="7ccaf-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="7ccaf-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ccaf-110">語法</span><span class="sxs-lookup"><span data-stu-id="7ccaf-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ccaf-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ccaf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7ccaf-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ccaf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7ccaf-113">Attributes</span></span>  
 <span data-ttu-id="7ccaf-114">無。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ccaf-115">子元素</span><span class="sxs-lookup"><span data-stu-id="7ccaf-115">Child Elements</span></span>  
 <span data-ttu-id="7ccaf-116">無。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ccaf-117">父項目</span><span class="sxs-lookup"><span data-stu-id="7ccaf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7ccaf-118">項目</span><span class="sxs-lookup"><span data-stu-id="7ccaf-118">Element</span></span>|<span data-ttu-id="7ccaf-119">描述</span><span class="sxs-lookup"><span data-stu-id="7ccaf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ccaf-120">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7ccaf-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7ccaf-121">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ccaf-122">備註</span><span class="sxs-lookup"><span data-stu-id="7ccaf-122">Remarks</span></span>  
 <span data-ttu-id="7ccaf-123">您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="7ccaf-124"> 會發出新的執行緒，以提取每個接受的通道。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="7ccaf-125">如果有許多個通道，執行緒可能會用完。</span><span class="sxs-lookup"><span data-stu-id="7ccaf-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ccaf-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ccaf-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
