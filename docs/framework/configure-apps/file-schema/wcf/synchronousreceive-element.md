---
title: <synchronousReceive> 項目
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399502"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="ea3ed-102">\<synchronousReceive> 項目</span><span class="sxs-lookup"><span data-stu-id="ea3ed-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="ea3ed-103">這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="ea3ed-104">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="ea3ed-105">語法</span><span class="sxs-lookup"><span data-stu-id="ea3ed-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea3ed-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ea3ed-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ea3ed-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea3ed-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ea3ed-108">Attributes</span></span>  
 <span data-ttu-id="ea3ed-109">無。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea3ed-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ea3ed-110">Child Elements</span></span>  
 <span data-ttu-id="ea3ed-111">無。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea3ed-112">父項目</span><span class="sxs-lookup"><span data-stu-id="ea3ed-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ea3ed-113">元素</span><span class="sxs-lookup"><span data-stu-id="ea3ed-113">Element</span></span>|<span data-ttu-id="ea3ed-114">描述</span><span class="sxs-lookup"><span data-stu-id="ea3ed-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ea3ed-115">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea3ed-116">備註</span><span class="sxs-lookup"><span data-stu-id="ea3ed-116">Remarks</span></span>  
 <span data-ttu-id="ea3ed-117">您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="ea3ed-118">Windows Communication Foundation （WCF）會發出新的執行緒，以提取每個接受的通道。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="ea3ed-119">如果有許多個通道，執行緒可能會用完。</span><span class="sxs-lookup"><span data-stu-id="ea3ed-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea3ed-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea3ed-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
