---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925850"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="3fb16-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="3fb16-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="3fb16-102">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="3fb16-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="3fb16-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3fb16-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3fb16-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3fb16-104">\<behaviors></span></span>  
<span data-ttu-id="3fb16-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3fb16-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="3fb16-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3fb16-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb16-107">語法</span><span class="sxs-lookup"><span data-stu-id="3fb16-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="3fb16-108">類型</span><span class="sxs-lookup"><span data-stu-id="3fb16-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fb16-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="3fb16-109">Attributes and elements</span></span>  
  
<span data-ttu-id="3fb16-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3fb16-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fb16-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3fb16-111">Attributes</span></span>

| <span data-ttu-id="3fb16-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3fb16-112">Attribute</span></span>               | <span data-ttu-id="3fb16-113">描述</span><span class="sxs-lookup"><span data-stu-id="3fb16-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="3fb16-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="3fb16-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="3fb16-115">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="3fb16-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="3fb16-116">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="3fb16-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="3fb16-117">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="3fb16-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="3fb16-118">子元素</span><span class="sxs-lookup"><span data-stu-id="3fb16-118">Child elements</span></span>

<span data-ttu-id="3fb16-119">無。</span><span class="sxs-lookup"><span data-stu-id="3fb16-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3fb16-120">父元素</span><span class="sxs-lookup"><span data-stu-id="3fb16-120">Parent elements</span></span>

| <span data-ttu-id="3fb16-121">元素</span><span class="sxs-lookup"><span data-stu-id="3fb16-121">Element</span></span> | <span data-ttu-id="3fb16-122">描述</span><span class="sxs-lookup"><span data-stu-id="3fb16-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="3fb16-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3fb16-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3fb16-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="3fb16-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3fb16-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fb16-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
