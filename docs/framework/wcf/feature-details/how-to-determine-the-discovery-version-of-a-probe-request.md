---
title: HOW TO：判斷探查要求的探索版本
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425261"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>HOW TO：判斷探查要求的探索版本

探索 Proxy 可能會公開使用不同探索版本的多個探索端點。 當 UDP 多點傳送探查要求到達 proxy 時，proxy 應該使用多點傳送的隱藏訊息回應。 若要這樣做，您必須知道要求的探索版本。

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>若要判斷探查要求的探索版本

在回應探查要求的方法 (例如<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) 使用靜態<xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType>屬性來搜尋<xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>，如下列程式碼所示。

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [實作探索 Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
