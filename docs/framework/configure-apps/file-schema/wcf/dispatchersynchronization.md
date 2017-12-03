---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0a6349f50c8810d834d7887daecb6ac9cffb2e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="2a7fd-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="2a7fd-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="2a7fd-103">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="2a7fd-104">\<system.serviceModel >\<行為 > \<endpointBehaviors >\<行為 ></span><span class="sxs-lookup"><span data-stu-id="2a7fd-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="2a7fd-105">語法</span><span class="sxs-lookup"><span data-stu-id="2a7fd-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="2a7fd-106">類型</span><span class="sxs-lookup"><span data-stu-id="2a7fd-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="2a7fd-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2a7fd-107">Attributes and elements</span></span>

<span data-ttu-id="2a7fd-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a7fd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2a7fd-109">Attributes</span></span>

| <span data-ttu-id="2a7fd-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2a7fd-110">Attribute</span></span>               | <span data-ttu-id="2a7fd-111">描述</span><span class="sxs-lookup"><span data-stu-id="2a7fd-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="2a7fd-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="2a7fd-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="2a7fd-113">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="2a7fd-114">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="2a7fd-115">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="2a7fd-116">子元素</span><span class="sxs-lookup"><span data-stu-id="2a7fd-116">Child elements</span></span>

<span data-ttu-id="2a7fd-117">無。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a7fd-118">父元素</span><span class="sxs-lookup"><span data-stu-id="2a7fd-118">Parent elements</span></span>

| <span data-ttu-id="2a7fd-119">元素</span><span class="sxs-lookup"><span data-stu-id="2a7fd-119">Element</span></span> | <span data-ttu-id="2a7fd-120">說明</span><span class="sxs-lookup"><span data-stu-id="2a7fd-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="2a7fd-121">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="2a7fd-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2a7fd-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="2a7fd-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="2a7fd-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a7fd-123">See also</span></span>

 <span data-ttu-id="2a7fd-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="2a7fd-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
