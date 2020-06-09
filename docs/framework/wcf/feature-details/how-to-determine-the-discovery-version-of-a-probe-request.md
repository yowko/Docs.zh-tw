---
title: HOW TO：判斷探查要求的探索版本
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595410"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="6bdad-102">HOW TO：判斷探查要求的探索版本</span><span class="sxs-lookup"><span data-stu-id="6bdad-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="6bdad-103">探索 Proxy 可能會公開使用不同探索版本的多個探索端點。</span><span class="sxs-lookup"><span data-stu-id="6bdad-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="6bdad-104">當 UDP 多播探查要求抵達 proxy 時，proxy 應該會回應多播隱藏訊息。</span><span class="sxs-lookup"><span data-stu-id="6bdad-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="6bdad-105">為了這麼做，它必須知道要求的探索版本。</span><span class="sxs-lookup"><span data-stu-id="6bdad-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="6bdad-106">若要判斷探查要求的探索版本</span><span class="sxs-lookup"><span data-stu-id="6bdad-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="6bdad-107">在回應探查要求的方法中（例如 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ），使用靜態 <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> 屬性來搜尋 <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6bdad-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="6bdad-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="6bdad-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="6bdad-109">實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="6bdad-109">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
