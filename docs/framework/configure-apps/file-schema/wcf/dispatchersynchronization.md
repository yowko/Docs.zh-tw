---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398007"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="83ab1-101">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="83ab1-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="83ab1-102">語法</span><span class="sxs-lookup"><span data-stu-id="83ab1-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="83ab1-103">類型</span><span class="sxs-lookup"><span data-stu-id="83ab1-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83ab1-104">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="83ab1-104">Attributes and elements</span></span>  
  
<span data-ttu-id="83ab1-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="83ab1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83ab1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="83ab1-106">Attributes</span></span>

| <span data-ttu-id="83ab1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="83ab1-107">Attribute</span></span>               | <span data-ttu-id="83ab1-108">描述</span><span class="sxs-lookup"><span data-stu-id="83ab1-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="83ab1-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="83ab1-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="83ab1-110">布林值，指定是否啟用非同步傳送行為。</span><span class="sxs-lookup"><span data-stu-id="83ab1-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="83ab1-111">整數，指定可在通道發行之並行接收的數目。</span><span class="sxs-lookup"><span data-stu-id="83ab1-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="83ab1-112">唯有在您正確設定服務節流閥行為後，才可設定這個值。</span><span class="sxs-lookup"><span data-stu-id="83ab1-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="83ab1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="83ab1-113">Child elements</span></span>

<span data-ttu-id="83ab1-114">無。</span><span class="sxs-lookup"><span data-stu-id="83ab1-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83ab1-115">父元素</span><span class="sxs-lookup"><span data-stu-id="83ab1-115">Parent elements</span></span>

| <span data-ttu-id="83ab1-116">元素</span><span class="sxs-lookup"><span data-stu-id="83ab1-116">Element</span></span> | <span data-ttu-id="83ab1-117">描述</span><span class="sxs-lookup"><span data-stu-id="83ab1-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="83ab1-118">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="83ab1-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="83ab1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83ab1-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
