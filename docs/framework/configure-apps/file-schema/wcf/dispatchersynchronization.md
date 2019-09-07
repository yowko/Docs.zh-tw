---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398007"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="fbdef-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="fbdef-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="fbdef-102">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="fbdef-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="fbdef-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fbdef-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fbdef-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fbdef-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fbdef-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fbdef-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fbdef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fbdef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="fbdef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fbdef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="fbdef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**</span><span class="sxs-lookup"><span data-stu-id="fbdef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbdef-109">語法</span><span class="sxs-lookup"><span data-stu-id="fbdef-109">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="fbdef-110">類型</span><span class="sxs-lookup"><span data-stu-id="fbdef-110">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbdef-111">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="fbdef-111">Attributes and elements</span></span>  
  
<span data-ttu-id="fbdef-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fbdef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbdef-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fbdef-113">Attributes</span></span>

| <span data-ttu-id="fbdef-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fbdef-114">Attribute</span></span>               | <span data-ttu-id="fbdef-115">說明</span><span class="sxs-lookup"><span data-stu-id="fbdef-115">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="fbdef-116">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="fbdef-116">asynchronousSendEnabled</span></span> | <span data-ttu-id="fbdef-117">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="fbdef-117">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="fbdef-118">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="fbdef-118">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="fbdef-119">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="fbdef-119">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="fbdef-120">子元素</span><span class="sxs-lookup"><span data-stu-id="fbdef-120">Child elements</span></span>

<span data-ttu-id="fbdef-121">無。</span><span class="sxs-lookup"><span data-stu-id="fbdef-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fbdef-122">父元素</span><span class="sxs-lookup"><span data-stu-id="fbdef-122">Parent elements</span></span>

| <span data-ttu-id="fbdef-123">元素</span><span class="sxs-lookup"><span data-stu-id="fbdef-123">Element</span></span> | <span data-ttu-id="fbdef-124">描述</span><span class="sxs-lookup"><span data-stu-id="fbdef-124">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="fbdef-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="fbdef-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fbdef-126">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="fbdef-126">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fbdef-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbdef-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
