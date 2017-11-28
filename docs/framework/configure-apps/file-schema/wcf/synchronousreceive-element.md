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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b630f5ad2fbf5e3f20667e0bd1b7ae711992dc18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="99752-102">&lt;synchronousReceive&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="99752-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="99752-103">這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="99752-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="99752-104">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="99752-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="99752-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="99752-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="99752-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="99752-106">\<behaviors></span></span>  
<span data-ttu-id="99752-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="99752-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="99752-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="99752-108">\<behavior></span></span>  
<span data-ttu-id="99752-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="99752-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99752-110">語法</span><span class="sxs-lookup"><span data-stu-id="99752-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99752-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99752-111">Attributes and Elements</span></span>  
 <span data-ttu-id="99752-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="99752-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99752-113">屬性</span><span class="sxs-lookup"><span data-stu-id="99752-113">Attributes</span></span>  
 <span data-ttu-id="99752-114">無。</span><span class="sxs-lookup"><span data-stu-id="99752-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99752-115">子元素</span><span class="sxs-lookup"><span data-stu-id="99752-115">Child Elements</span></span>  
 <span data-ttu-id="99752-116">無。</span><span class="sxs-lookup"><span data-stu-id="99752-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99752-117">父項目</span><span class="sxs-lookup"><span data-stu-id="99752-117">Parent Elements</span></span>  
  
|<span data-ttu-id="99752-118">項目</span><span class="sxs-lookup"><span data-stu-id="99752-118">Element</span></span>|<span data-ttu-id="99752-119">說明</span><span class="sxs-lookup"><span data-stu-id="99752-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99752-120">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="99752-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="99752-121">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="99752-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99752-122">備註</span><span class="sxs-lookup"><span data-stu-id="99752-122">Remarks</span></span>  
 <span data-ttu-id="99752-123">您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。</span><span class="sxs-lookup"><span data-stu-id="99752-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="99752-124"> 會發出新的執行緒，以提取每個接受的通道。</span><span class="sxs-lookup"><span data-stu-id="99752-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="99752-125">如果有許多個通道，執行緒可能會用完。</span><span class="sxs-lookup"><span data-stu-id="99752-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99752-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99752-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
