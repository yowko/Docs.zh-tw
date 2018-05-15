---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 34c12a05ee363df6b6cfc9ff3809bab50ee8d522
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="adb83-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="adb83-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="adb83-103">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="adb83-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="adb83-104">\<system.serviceModel >\<行為 > \<endpointBehaviors >\<行為 ></span><span class="sxs-lookup"><span data-stu-id="adb83-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="adb83-105">語法</span><span class="sxs-lookup"><span data-stu-id="adb83-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="adb83-106">類型</span><span class="sxs-lookup"><span data-stu-id="adb83-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="adb83-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="adb83-107">Attributes and elements</span></span>

<span data-ttu-id="adb83-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="adb83-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="adb83-109">屬性</span><span class="sxs-lookup"><span data-stu-id="adb83-109">Attributes</span></span>

| <span data-ttu-id="adb83-110">屬性</span><span class="sxs-lookup"><span data-stu-id="adb83-110">Attribute</span></span>               | <span data-ttu-id="adb83-111">描述</span><span class="sxs-lookup"><span data-stu-id="adb83-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="adb83-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="adb83-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="adb83-113">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="adb83-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="adb83-114">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="adb83-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="adb83-115">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="adb83-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="adb83-116">子元素</span><span class="sxs-lookup"><span data-stu-id="adb83-116">Child elements</span></span>

<span data-ttu-id="adb83-117">無。</span><span class="sxs-lookup"><span data-stu-id="adb83-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="adb83-118">父元素</span><span class="sxs-lookup"><span data-stu-id="adb83-118">Parent elements</span></span>

| <span data-ttu-id="adb83-119">元素</span><span class="sxs-lookup"><span data-stu-id="adb83-119">Element</span></span> | <span data-ttu-id="adb83-120">描述</span><span class="sxs-lookup"><span data-stu-id="adb83-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="adb83-121">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="adb83-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="adb83-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="adb83-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="adb83-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adb83-123">See also</span></span>

 <span data-ttu-id="adb83-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="adb83-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
