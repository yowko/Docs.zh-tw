---
title: <synchronousReceive> 項目
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399502"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="8f202-102">\<synchronousReceive > 元素</span><span class="sxs-lookup"><span data-stu-id="8f202-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="8f202-103">這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="8f202-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="8f202-104">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="8f202-104">It does not have any attributes or child elements.</span></span>  
  
<span data-ttu-id="8f202-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f202-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f202-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f202-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8f202-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8f202-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8f202-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8f202-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="8f202-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8f202-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="8f202-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<synchronousReceive >**</span><span class="sxs-lookup"><span data-stu-id="8f202-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f202-111">語法</span><span class="sxs-lookup"><span data-stu-id="8f202-111">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f202-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8f202-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8f202-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8f202-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f202-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8f202-114">Attributes</span></span>  
 <span data-ttu-id="8f202-115">無。</span><span class="sxs-lookup"><span data-stu-id="8f202-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f202-116">子元素</span><span class="sxs-lookup"><span data-stu-id="8f202-116">Child Elements</span></span>  
 <span data-ttu-id="8f202-117">無。</span><span class="sxs-lookup"><span data-stu-id="8f202-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f202-118">父項目</span><span class="sxs-lookup"><span data-stu-id="8f202-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8f202-119">項目</span><span class="sxs-lookup"><span data-stu-id="8f202-119">Element</span></span>|<span data-ttu-id="8f202-120">描述</span><span class="sxs-lookup"><span data-stu-id="8f202-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f202-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8f202-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8f202-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="8f202-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f202-123">備註</span><span class="sxs-lookup"><span data-stu-id="8f202-123">Remarks</span></span>  
 <span data-ttu-id="8f202-124">您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。</span><span class="sxs-lookup"><span data-stu-id="8f202-124">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="8f202-125">Windows Communication Foundation （WCF）會發出新的執行緒，以提取每個接受的通道。</span><span class="sxs-lookup"><span data-stu-id="8f202-125">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="8f202-126">如果有許多個通道，執行緒可能會用完。</span><span class="sxs-lookup"><span data-stu-id="8f202-126">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f202-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f202-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
