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
ms.openlocfilehash: 79d78517b62e4476106ff1ed7978c770a17caf2a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="1466a-102">&lt;synchronousReceive&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="1466a-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="1466a-103">這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="1466a-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="1466a-104">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="1466a-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="1466a-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1466a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1466a-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1466a-106">\<behaviors></span></span>  
<span data-ttu-id="1466a-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1466a-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="1466a-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1466a-108">\<behavior></span></span>  
<span data-ttu-id="1466a-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="1466a-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1466a-110">語法</span><span class="sxs-lookup"><span data-stu-id="1466a-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1466a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1466a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1466a-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1466a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1466a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1466a-113">Attributes</span></span>  
 <span data-ttu-id="1466a-114">無。</span><span class="sxs-lookup"><span data-stu-id="1466a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1466a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="1466a-115">Child Elements</span></span>  
 <span data-ttu-id="1466a-116">無。</span><span class="sxs-lookup"><span data-stu-id="1466a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1466a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1466a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1466a-118">項目</span><span class="sxs-lookup"><span data-stu-id="1466a-118">Element</span></span>|<span data-ttu-id="1466a-119">說明</span><span class="sxs-lookup"><span data-stu-id="1466a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1466a-120">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1466a-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1466a-121">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="1466a-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1466a-122">備註</span><span class="sxs-lookup"><span data-stu-id="1466a-122">Remarks</span></span>  
 <span data-ttu-id="1466a-123">您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。</span><span class="sxs-lookup"><span data-stu-id="1466a-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="1466a-124"> 會發出新的執行緒，以提取每個接受的通道。</span><span class="sxs-lookup"><span data-stu-id="1466a-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="1466a-125">如果有許多個通道，執行緒可能會用完。</span><span class="sxs-lookup"><span data-stu-id="1466a-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1466a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1466a-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
