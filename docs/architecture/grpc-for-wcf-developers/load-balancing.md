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
# <a name="load-balancing-grpc"></a><span data-ttu-id="159dd-103">負載平衡 gRPC</span><span class="sxs-lookup"><span data-stu-id="159dd-103">Load balancing gRPC</span></span>

<span data-ttu-id="159dd-104">GRPC 應用程式的一般部署包含許多相同的服務實例，可提供復原能力和水準的擴充性。</span><span class="sxs-lookup"><span data-stu-id="159dd-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="159dd-105">負載平衡會將連入要求分散到這些實例，以提供所有可用資源的完整使用。</span><span class="sxs-lookup"><span data-stu-id="159dd-105">Load balancing distributes incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="159dd-106">若要讓用戶端看不到此負載平衡，通常會使用 proxy 負載平衡器伺服器來處理來自用戶端的要求，並將其路由傳送至後端實例。</span><span class="sxs-lookup"><span data-stu-id="159dd-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="159dd-107">負載平衡器會根據其運作的 *層* 級進行分類。</span><span class="sxs-lookup"><span data-stu-id="159dd-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="159dd-108">第4層負載平衡器適用于 *傳輸* 層級，例如使用 TCP 通訊端、連線和封包。</span><span class="sxs-lookup"><span data-stu-id="159dd-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections, and packets.</span></span> <span data-ttu-id="159dd-109">第7層負載平衡器會在 *應用* 層級運作，尤其是處理 gRPC 應用程式的 HTTP/2 要求。</span><span class="sxs-lookup"><span data-stu-id="159dd-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="159dd-110">L4 負載平衡器</span><span class="sxs-lookup"><span data-stu-id="159dd-110">L4 load balancers</span></span>

<span data-ttu-id="159dd-111">L4 負載平衡器會接受來自用戶端的 TCP 連線要求、開啟另一個後端實例的連接，並在兩個連線之間複製資料，而不會進行實際處理。</span><span class="sxs-lookup"><span data-stu-id="159dd-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="159dd-112">L4 提供絕佳的效能和低延遲，但幾乎沒有控制或智慧。</span><span class="sxs-lookup"><span data-stu-id="159dd-112">L4 offers excellent performance and low latency, but with little control or intelligence.</span></span> <span data-ttu-id="159dd-113">只要用戶端讓連線保持開啟，所有的要求都會導向至相同的後端實例。</span><span class="sxs-lookup"><span data-stu-id="159dd-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

 <span data-ttu-id="159dd-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) 是 L4 負載平衡器的範例。</span><span class="sxs-lookup"><span data-stu-id="159dd-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) is an example of an L4 load balancer.</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="159dd-115">L7 負載平衡器</span><span class="sxs-lookup"><span data-stu-id="159dd-115">L7 load balancers</span></span>

<span data-ttu-id="159dd-116">L7 負載平衡器會剖析傳入的 HTTP/2 要求，並依要求傳遞至後端實例，不論用戶端的連線時間長度為何。</span><span class="sxs-lookup"><span data-stu-id="159dd-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="159dd-117">L7 負載平衡器的範例：</span><span class="sxs-lookup"><span data-stu-id="159dd-117">Examples of L7 load balancers:</span></span>

- [<span data-ttu-id="159dd-118">NGINX</span><span class="sxs-lookup"><span data-stu-id="159dd-118">NGINX</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="159dd-119">HAProxy</span><span class="sxs-lookup"><span data-stu-id="159dd-119">HAProxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="159dd-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="159dd-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="159dd-121">根據經驗法則，L7 負載平衡器是 gRPC 和其他 HTTP/2 應用程式的最佳選擇， (和 HTTP 應用程式通常是) 。</span><span class="sxs-lookup"><span data-stu-id="159dd-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="159dd-122">L4 負載平衡器可 *搭配* gRPC 應用程式使用，但在低延遲和低負荷很重要的情況下，它們主要是很有用的。</span><span class="sxs-lookup"><span data-stu-id="159dd-122">L4 load balancers will *work* with gRPC applications, but they're primarily useful when low latency and low overhead are important.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="159dd-123">在撰寫本文時，有些 L7 負載平衡器不支援 gRPC 服務所需的 HTTP/2 規格的所有部分，例如尾端的標頭。</span><span class="sxs-lookup"><span data-stu-id="159dd-123">At the time of this writing, some L7 load balancers don't support all the parts of the HTTP/2 specification that are required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="159dd-124">如果您使用 TLS 加密，負載平衡器可以終止 TLS 連線，並將未加密的要求傳遞給後端應用程式，或者可以傳遞加密的要求。</span><span class="sxs-lookup"><span data-stu-id="159dd-124">If you're using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or they can pass the encrypted request along.</span></span> <span data-ttu-id="159dd-125">無論何種方式，負載平衡器都必須使用伺服器的公開和私密金鑰進行設定，以便解密要求以進行處理。</span><span class="sxs-lookup"><span data-stu-id="159dd-125">Either way, the load balancer will need to be configured with the server's public and private key so it can decrypt requests for processing.</span></span>

<span data-ttu-id="159dd-126">請參閱您慣用的負載平衡器檔，以瞭解如何設定它以使用後端服務處理 HTTP/2 要求。</span><span class="sxs-lookup"><span data-stu-id="159dd-126">See to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="159dd-127">Kubernetes 內的負載平衡</span><span class="sxs-lookup"><span data-stu-id="159dd-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="159dd-128">請參閱 [服務網格的一節](service-mesh.md) ，以瞭解 Kubernetes 上的內部服務之間的負載平衡。</span><span class="sxs-lookup"><span data-stu-id="159dd-128">See [the section on service meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="159dd-129">[上一個](service-mesh.md) 
>[下一步](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="159dd-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
