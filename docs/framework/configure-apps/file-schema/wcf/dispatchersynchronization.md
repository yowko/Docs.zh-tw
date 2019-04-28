---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673403"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="4b17e-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="4b17e-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="4b17e-102">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="4b17e-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="4b17e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4b17e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4b17e-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="4b17e-104">\<behaviors></span></span>  
<span data-ttu-id="4b17e-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4b17e-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="4b17e-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4b17e-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b17e-107">語法</span><span class="sxs-lookup"><span data-stu-id="4b17e-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="4b17e-108">類型</span><span class="sxs-lookup"><span data-stu-id="4b17e-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b17e-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="4b17e-109">Attributes and elements</span></span>  
  
<span data-ttu-id="4b17e-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4b17e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b17e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4b17e-111">Attributes</span></span>

| <span data-ttu-id="4b17e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4b17e-112">Attribute</span></span>               | <span data-ttu-id="4b17e-113">描述</span><span class="sxs-lookup"><span data-stu-id="4b17e-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="4b17e-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="4b17e-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="4b17e-115">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="4b17e-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="4b17e-116">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="4b17e-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="4b17e-117">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="4b17e-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="4b17e-118">子元素</span><span class="sxs-lookup"><span data-stu-id="4b17e-118">Child elements</span></span>

<span data-ttu-id="4b17e-119">無。</span><span class="sxs-lookup"><span data-stu-id="4b17e-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4b17e-120">父元素</span><span class="sxs-lookup"><span data-stu-id="4b17e-120">Parent elements</span></span>

| <span data-ttu-id="4b17e-121">元素</span><span class="sxs-lookup"><span data-stu-id="4b17e-121">Element</span></span> | <span data-ttu-id="4b17e-122">描述</span><span class="sxs-lookup"><span data-stu-id="4b17e-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="4b17e-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4b17e-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4b17e-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="4b17e-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4b17e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b17e-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
