---
title: 適用于 WCF 開發人員的負載平衡 gRPC-gRPC
description: 選擇要使用 gRPC 服務的負載平衡器。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5d4a9be9b8f4e511a72af6b68d8a005604fd984d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184390"
---
# <a name="load-balancing-grpc"></a>負載平衡 gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

GRPC 應用程式的一般部署包含許多相同的服務實例，提供復原能力和水準擴充性。 對這些實例之間的分散式傳入要求進行負載平衡，以提供所有可用資源的完整使用量。 若要讓用戶端看不到此負載平衡，通常會使用 proxy 負載平衡器伺服器來處理用戶端的要求，並將它們路由傳送至後端實例。

負載平衡器會根據其運作的*層*級分類。 第4層負載平衡器適用于*傳輸*層級，例如，使用 TCP 通訊端、連接和封包。 第7層負載平衡器適用于*應用*層級，特別是處理 gRPC 應用程式的 HTTP/2 要求。

## <a name="l4-load-balancers"></a>L4 負載平衡器

L4 負載平衡器會接受來自用戶端的 TCP 連線要求、開啟與其中一個後端實例的另一個連接，並在兩個連接之間複製資料，而不需要實際處理。 L4 提供絕佳的效能和低延遲，但非常少控制或智慧。 只要用戶端讓連接保持開啟，所有要求都會導向至相同的後端實例。

[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)是 L4 負載平衡器的範例。

## <a name="l7-load-balancers"></a>L7 負載平衡器

L7 負載平衡器會剖析傳入的 HTTP/2 要求，並依要求逐一將它們傳遞至後端實例，無論用戶端的連線時間長度為何。

L7 負載平衡器的範例包括：

- [Nginx](https://www.nginx.com/)
- [HAproxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

根據經驗法則，L7 負載平衡器是 gRPC 和其他 HTTP/2 應用程式（通常是 HTTP 應用程式）的最佳選擇。 L4 負載平衡器可與 gRPC 應用程式*搭配*使用，但在低延遲和低負擔的重要性很重要時，主要很有用。

> [!IMPORTANT]
> 在撰寫本文時，並非所有的 L7 負載平衡器都支援 gRPC 服務所需的 HTTP/2 規格的所有部分，例如尾端標頭。

使用 TLS 加密時，負載平衡器可以終止 TLS 連線並將未加密的要求傳遞給後端應用程式，或傳遞加密的要求。 不論是哪一種情況，負載平衡器都必須使用伺服器的公開和私密金鑰來設定，使其可以解密要求以進行處理。

請參閱您慣用的負載平衡器檔，以瞭解如何設定它以處理後端服務的 HTTP/2 要求。

## <a name="load-balancing-within-kubernetes"></a>Kubernetes 內的負載平衡

請參閱[服務網格一節](service-mesh.md)，以取得 Kubernetes 上內部服務的負載平衡討論。

>[!div class="step-by-step"]
>[上一頁](service-mesh.md)
>[下一頁](application-performance-management.md)
