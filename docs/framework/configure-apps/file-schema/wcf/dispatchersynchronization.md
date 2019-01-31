---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273328"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="f09e4-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="f09e4-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="f09e4-102">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="f09e4-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="f09e4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f09e4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f09e4-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f09e4-104">\<behaviors></span></span>  
<span data-ttu-id="f09e4-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f09e4-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="f09e4-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f09e4-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f09e4-107">語法</span><span class="sxs-lookup"><span data-stu-id="f09e4-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f09e4-108">類型</span><span class="sxs-lookup"><span data-stu-id="f09e4-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f09e4-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f09e4-109">Attributes and elements</span></span>  
  
<span data-ttu-id="f09e4-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f09e4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f09e4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f09e4-111">Attributes</span></span>

| <span data-ttu-id="f09e4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f09e4-112">Attribute</span></span>               | <span data-ttu-id="f09e4-113">描述</span><span class="sxs-lookup"><span data-stu-id="f09e4-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="f09e4-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="f09e4-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="f09e4-115">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="f09e4-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="f09e4-116">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="f09e4-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="f09e4-117">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="f09e4-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f09e4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="f09e4-118">Child elements</span></span>

<span data-ttu-id="f09e4-119">無。</span><span class="sxs-lookup"><span data-stu-id="f09e4-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f09e4-120">父元素</span><span class="sxs-lookup"><span data-stu-id="f09e4-120">Parent elements</span></span>

| <span data-ttu-id="f09e4-121">元素</span><span class="sxs-lookup"><span data-stu-id="f09e4-121">Element</span></span> | <span data-ttu-id="f09e4-122">描述</span><span class="sxs-lookup"><span data-stu-id="f09e4-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="f09e4-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f09e4-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f09e4-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="f09e4-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f09e4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f09e4-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
