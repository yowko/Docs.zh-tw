---
title: 負載平衡 gRPC-適用于 WCF 開發人員的 gRPC
description: 選擇要使用 gRPC 服務的負載平衡器。
ms.date: 12/15/2020
ms.openlocfilehash: 55f61608dce1f159b11d7265a47938ba49e9e188
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938581"
---
# <a name="load-balancing-grpc"></a>負載平衡 gRPC

GRPC 應用程式的一般部署包含許多相同的服務實例，可提供復原能力和水準的擴充性。 負載平衡會將連入要求分散到這些實例，以提供所有可用資源的完整使用。 若要讓用戶端看不到此負載平衡，通常會使用 proxy 負載平衡器伺服器來處理來自用戶端的要求，並將其路由傳送至後端實例。

負載平衡器會根據其運作的 *層* 級進行分類。 第4層負載平衡器適用于 *傳輸* 層級，例如使用 TCP 通訊端、連線和封包。 第7層負載平衡器會在 *應用* 層級運作，尤其是處理 gRPC 應用程式的 HTTP/2 要求。

## <a name="l4-load-balancers"></a>L4 負載平衡器

L4 負載平衡器會接受來自用戶端的 TCP 連線要求、開啟另一個後端實例的連接，並在兩個連線之間複製資料，而不會進行實際處理。 L4 提供絕佳的效能和低延遲，但幾乎沒有控制或智慧。 只要用戶端讓連線保持開啟，所有的要求都會導向至相同的後端實例。

 [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) 是 L4 負載平衡器的範例。

## <a name="l7-load-balancers"></a>L7 負載平衡器

L7 負載平衡器會剖析傳入的 HTTP/2 要求，並依要求傳遞至後端實例，不論用戶端的連線時間長度為何。

L7 負載平衡器的範例：

- [NGINX](https://www.nginx.com/)
- [HAProxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

根據經驗法則，L7 負載平衡器是 gRPC 和其他 HTTP/2 應用程式的最佳選擇， (和 HTTP 應用程式通常是) 。 L4 負載平衡器可 *搭配* gRPC 應用程式使用，但在低延遲和低負荷很重要的情況下，它們主要是很有用的。

> [!IMPORTANT]
> 在撰寫本文時，有些 L7 負載平衡器不支援 gRPC 服務所需的 HTTP/2 規格的所有部分，例如尾端的標頭。

如果您使用 TLS 加密，負載平衡器可以終止 TLS 連線，並將未加密的要求傳遞給後端應用程式，或者可以傳遞加密的要求。 無論何種方式，負載平衡器都必須使用伺服器的公開和私密金鑰進行設定，以便解密要求以進行處理。

請參閱您慣用的負載平衡器檔，以瞭解如何設定它以使用後端服務處理 HTTP/2 要求。

## <a name="load-balancing-within-kubernetes"></a>Kubernetes 內的負載平衡

請參閱 [服務網格的一節](service-mesh.md) ，以瞭解 Kubernetes 上的內部服務之間的負載平衡。

>[!div class="step-by-step"]
>[上一個](service-mesh.md) 
>[下一步](application-performance-management.md)
