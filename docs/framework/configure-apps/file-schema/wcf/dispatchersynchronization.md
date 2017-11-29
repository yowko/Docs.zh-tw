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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24ae6dbf0fb67b5755aca848ea7fce6abda14b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="56bd6-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="56bd6-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="56bd6-103">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="56bd6-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="56bd6-104">\<system.serviceModel >\<行為 > \<endpointBehaviors >\<行為 ></span><span class="sxs-lookup"><span data-stu-id="56bd6-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="56bd6-105">語法</span><span class="sxs-lookup"><span data-stu-id="56bd6-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="56bd6-106">類型</span><span class="sxs-lookup"><span data-stu-id="56bd6-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="56bd6-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="56bd6-107">Attributes and elements</span></span>

<span data-ttu-id="56bd6-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="56bd6-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="56bd6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="56bd6-109">Attributes</span></span>

| <span data-ttu-id="56bd6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="56bd6-110">Attribute</span></span>               | <span data-ttu-id="56bd6-111">描述</span><span class="sxs-lookup"><span data-stu-id="56bd6-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="56bd6-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="56bd6-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="56bd6-113">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="56bd6-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="56bd6-114">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="56bd6-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="56bd6-115">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="56bd6-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="56bd6-116">子元素</span><span class="sxs-lookup"><span data-stu-id="56bd6-116">Child elements</span></span>

<span data-ttu-id="56bd6-117">無。</span><span class="sxs-lookup"><span data-stu-id="56bd6-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="56bd6-118">父元素</span><span class="sxs-lookup"><span data-stu-id="56bd6-118">Parent elements</span></span>

| <span data-ttu-id="56bd6-119">元素</span><span class="sxs-lookup"><span data-stu-id="56bd6-119">Element</span></span> | <span data-ttu-id="56bd6-120">說明</span><span class="sxs-lookup"><span data-stu-id="56bd6-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="56bd6-121">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="56bd6-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="56bd6-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="56bd6-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="56bd6-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="56bd6-123">See also</span></span>

 <span data-ttu-id="56bd6-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="56bd6-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
