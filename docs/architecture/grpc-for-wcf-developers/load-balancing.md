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
# <a name="load-balancing-grpc"></a><span data-ttu-id="75e75-103">負載平衡 gRPC</span><span class="sxs-lookup"><span data-stu-id="75e75-103">Load balancing gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="75e75-104">GRPC 應用程式的一般部署包含許多相同的服務實例，提供復原能力和水準擴充性。</span><span class="sxs-lookup"><span data-stu-id="75e75-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="75e75-105">對這些實例之間的分散式傳入要求進行負載平衡，以提供所有可用資源的完整使用量。</span><span class="sxs-lookup"><span data-stu-id="75e75-105">Load balancing distributed incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="75e75-106">若要讓用戶端看不到此負載平衡，通常會使用 proxy 負載平衡器伺服器來處理用戶端的要求，並將它們路由傳送至後端實例。</span><span class="sxs-lookup"><span data-stu-id="75e75-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="75e75-107">負載平衡器會根據其運作的*層*級分類。</span><span class="sxs-lookup"><span data-stu-id="75e75-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="75e75-108">第4層負載平衡器適用于*傳輸*層級，例如，使用 TCP 通訊端、連接和封包。</span><span class="sxs-lookup"><span data-stu-id="75e75-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections and packets.</span></span> <span data-ttu-id="75e75-109">第7層負載平衡器適用于*應用*層級，特別是處理 gRPC 應用程式的 HTTP/2 要求。</span><span class="sxs-lookup"><span data-stu-id="75e75-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="75e75-110">L4 負載平衡器</span><span class="sxs-lookup"><span data-stu-id="75e75-110">L4 load balancers</span></span>

<span data-ttu-id="75e75-111">L4 負載平衡器會接受來自用戶端的 TCP 連線要求、開啟與其中一個後端實例的另一個連接，並在兩個連接之間複製資料，而不需要實際處理。</span><span class="sxs-lookup"><span data-stu-id="75e75-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="75e75-112">L4 提供絕佳的效能和低延遲，但非常少控制或智慧。</span><span class="sxs-lookup"><span data-stu-id="75e75-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="75e75-113">只要用戶端讓連接保持開啟，所有要求都會導向至相同的後端實例。</span><span class="sxs-lookup"><span data-stu-id="75e75-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

<span data-ttu-id="75e75-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)是 L4 負載平衡器的範例。</span><span class="sxs-lookup"><span data-stu-id="75e75-114">An example of an L4 load balancer is the [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="75e75-115">L7 負載平衡器</span><span class="sxs-lookup"><span data-stu-id="75e75-115">L7 load balancers</span></span>

<span data-ttu-id="75e75-116">L7 負載平衡器會剖析傳入的 HTTP/2 要求，並依要求逐一將它們傳遞至後端實例，無論用戶端的連線時間長度為何。</span><span class="sxs-lookup"><span data-stu-id="75e75-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="75e75-117">L7 負載平衡器的範例包括：</span><span class="sxs-lookup"><span data-stu-id="75e75-117">Examples of L7 load balancers include:</span></span>

- [<span data-ttu-id="75e75-118">Nginx</span><span class="sxs-lookup"><span data-stu-id="75e75-118">Nginx</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="75e75-119">HAproxy</span><span class="sxs-lookup"><span data-stu-id="75e75-119">HAproxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="75e75-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="75e75-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="75e75-121">根據經驗法則，L7 負載平衡器是 gRPC 和其他 HTTP/2 應用程式（通常是 HTTP 應用程式）的最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="75e75-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="75e75-122">L4 負載平衡器可與 gRPC 應用程式*搭配*使用，但在低延遲和低負擔的重要性很重要時，主要很有用。</span><span class="sxs-lookup"><span data-stu-id="75e75-122">L4 load balancers will *work* with gRPC applications, but are primarily useful when low latency and low overhead are of paramount importance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75e75-123">在撰寫本文時，並非所有的 L7 負載平衡器都支援 gRPC 服務所需的 HTTP/2 規格的所有部分，例如尾端標頭。</span><span class="sxs-lookup"><span data-stu-id="75e75-123">At the time of this writing, not all L7 load balancers support all parts of the HTTP/2 specification required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="75e75-124">使用 TLS 加密時，負載平衡器可以終止 TLS 連線並將未加密的要求傳遞給後端應用程式，或傳遞加密的要求。</span><span class="sxs-lookup"><span data-stu-id="75e75-124">When using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or pass the encrypted request along.</span></span> <span data-ttu-id="75e75-125">不論是哪一種情況，負載平衡器都必須使用伺服器的公開和私密金鑰來設定，使其可以解密要求以進行處理。</span><span class="sxs-lookup"><span data-stu-id="75e75-125">Either way, the load balancer will need to be configured with the server's public and private key, so that it can decrypt requests for processing.</span></span>

<span data-ttu-id="75e75-126">請參閱您慣用的負載平衡器檔，以瞭解如何設定它以處理後端服務的 HTTP/2 要求。</span><span class="sxs-lookup"><span data-stu-id="75e75-126">Refer to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="75e75-127">Kubernetes 內的負載平衡</span><span class="sxs-lookup"><span data-stu-id="75e75-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="75e75-128">請參閱[服務網格一節](service-mesh.md)，以取得 Kubernetes 上內部服務的負載平衡討論。</span><span class="sxs-lookup"><span data-stu-id="75e75-128">See [the section on Service Meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="75e75-129">[上一頁](service-mesh.md)
>[下一頁](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="75e75-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
