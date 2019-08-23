---
title: <synchronousReceive> 項目
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938971"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="b41dd-102">\<synchronousReceive > 元素</span><span class="sxs-lookup"><span data-stu-id="b41dd-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="b41dd-103">這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="b41dd-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="b41dd-104">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="b41dd-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="b41dd-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b41dd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b41dd-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b41dd-106">\<behaviors></span></span>  
<span data-ttu-id="b41dd-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b41dd-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="b41dd-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b41dd-108">\<behavior></span></span>  
<span data-ttu-id="b41dd-109">\<synchronousReceive></span><span class="sxs-lookup"><span data-stu-id="b41dd-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b41dd-110">語法</span><span class="sxs-lookup"><span data-stu-id="b41dd-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b41dd-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b41dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b41dd-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b41dd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b41dd-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b41dd-113">Attributes</span></span>  
 <span data-ttu-id="b41dd-114">無。</span><span class="sxs-lookup"><span data-stu-id="b41dd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b41dd-115">子元素</span><span class="sxs-lookup"><span data-stu-id="b41dd-115">Child Elements</span></span>  
 <span data-ttu-id="b41dd-116">無。</span><span class="sxs-lookup"><span data-stu-id="b41dd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b41dd-117">父項目</span><span class="sxs-lookup"><span data-stu-id="b41dd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b41dd-118">項目</span><span class="sxs-lookup"><span data-stu-id="b41dd-118">Element</span></span>|<span data-ttu-id="b41dd-119">描述</span><span class="sxs-lookup"><span data-stu-id="b41dd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b41dd-120">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b41dd-120">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b41dd-121">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="b41dd-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b41dd-122">備註</span><span class="sxs-lookup"><span data-stu-id="b41dd-122">Remarks</span></span>  
 <span data-ttu-id="b41dd-123">您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。</span><span class="sxs-lookup"><span data-stu-id="b41dd-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="b41dd-124">Windows Communication Foundation (WCF) 會發出新的執行緒, 以提取每個接受的通道。</span><span class="sxs-lookup"><span data-stu-id="b41dd-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="b41dd-125">如果有許多個通道，執行緒可能會用完。</span><span class="sxs-lookup"><span data-stu-id="b41dd-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41dd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b41dd-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
