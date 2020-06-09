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
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>HOW TO：判斷探查要求的探索版本

探索 Proxy 可能會公開使用不同探索版本的多個探索端點。 當 UDP 多播探查要求抵達 proxy 時，proxy 應該會回應多播隱藏訊息。 為了這麼做，它必須知道要求的探索版本。

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>若要判斷探查要求的探索版本

在回應探查要求的方法中（例如 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ），使用靜態 <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> 屬性來搜尋 <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> ，如下列程式碼所示。

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [實作探索 Proxy](implementing-a-discovery-proxy.md)
