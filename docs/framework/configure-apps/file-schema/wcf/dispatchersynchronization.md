---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 537dee408f1af29a06042de439a2c1e7d7874222
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555384"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="f130c-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="f130c-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="f130c-103">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="f130c-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="f130c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f130c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f130c-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f130c-105">\<behaviors></span></span>  
<span data-ttu-id="f130c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f130c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f130c-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f130c-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f130c-108">語法</span><span class="sxs-lookup"><span data-stu-id="f130c-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f130c-109">類型</span><span class="sxs-lookup"><span data-stu-id="f130c-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f130c-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f130c-110">Attributes and elements</span></span>  
  
<span data-ttu-id="f130c-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f130c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f130c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f130c-112">Attributes</span></span>

| <span data-ttu-id="f130c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f130c-113">Attribute</span></span>               | <span data-ttu-id="f130c-114">描述</span><span class="sxs-lookup"><span data-stu-id="f130c-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="f130c-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="f130c-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="f130c-116">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="f130c-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="f130c-117">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="f130c-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="f130c-118">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="f130c-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f130c-119">子元素</span><span class="sxs-lookup"><span data-stu-id="f130c-119">Child elements</span></span>

<span data-ttu-id="f130c-120">無。</span><span class="sxs-lookup"><span data-stu-id="f130c-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f130c-121">父元素</span><span class="sxs-lookup"><span data-stu-id="f130c-121">Parent elements</span></span>

| <span data-ttu-id="f130c-122">元素</span><span class="sxs-lookup"><span data-stu-id="f130c-122">Element</span></span> | <span data-ttu-id="f130c-123">描述</span><span class="sxs-lookup"><span data-stu-id="f130c-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="f130c-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f130c-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f130c-125">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="f130c-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f130c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f130c-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
