---
title: 為什麼我們建議 WCF 開發人員的 gRPC-適用于 WCF 開發人員的 gRPC
description: 討論為何 gRPC 適合想要遷移至新式架構和平臺的 WCF 開發人員。
ms.date: 12/15/2020
ms.openlocfilehash: 058f85297610116e96c8580fcefb10ee6dfcf935
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937970"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a><span data-ttu-id="f4e55-103">為何我們為 WCF 開發人員建議 gRPC</span><span class="sxs-lookup"><span data-stu-id="f4e55-103">Why we recommend gRPC for WCF developers</span></span>

<span data-ttu-id="f4e55-104">在我們深入探討 gRPC 的語言和技巧之前，值得先討論為什麼 gRPC 是適合想要遷移至 .NET 的 Windows Communication Foundation (WCF) 開發人員的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f4e55-104">Before we dive deeply into the language and techniques of gRPC, it's worth discussing why gRPC is the right solution for Windows Communication Foundation (WCF) developers who want to migrate to .NET.</span></span>

## <a name="similarity-to-wcf"></a><span data-ttu-id="f4e55-105">與 WCF 的相似性</span><span class="sxs-lookup"><span data-stu-id="f4e55-105">Similarity to WCF</span></span>

<span data-ttu-id="f4e55-106">雖然 gRPC 的實和方法不同，但使用 gRPC 開發和取用服務的經驗對於 WCF 開發人員來說應該是直覺的。</span><span class="sxs-lookup"><span data-stu-id="f4e55-106">Although the implementation and approach are different for gRPC, the experience of developing and consuming services with gRPC should be intuitive for WCF developers.</span></span> <span data-ttu-id="f4e55-107">基礎目標相同：讓用戶端和伺服器在相同平臺上進行編碼，而不需要擔心網路功能。</span><span class="sxs-lookup"><span data-stu-id="f4e55-107">The underlying goal is the same: make it possible to code as though the client and server are on the same platform, without needing to worry about networking.</span></span>

<span data-ttu-id="f4e55-108">這兩個平臺都會共用宣告的原則，然後再執行介面，即使宣告該介面的程式不同也是一樣。</span><span class="sxs-lookup"><span data-stu-id="f4e55-108">Both platforms share the principle of declaring and then implementing an interface, even though the process for declaring that interface is different.</span></span> <span data-ttu-id="f4e55-109">您將會在第5章中看到，gRPC 支援對應到 WCF 服務可用系結的不同 RPC 呼叫類型。</span><span class="sxs-lookup"><span data-stu-id="f4e55-109">And as you'll see in chapter 5, the different types of RPC calls that gRPC supports map well to the bindings available to WCF services.</span></span>

## <a name="benefits-of-grpc"></a><span data-ttu-id="f4e55-110">GRPC 的優點</span><span class="sxs-lookup"><span data-stu-id="f4e55-110">Benefits of gRPC</span></span>

<span data-ttu-id="f4e55-111">gRPC 會因下列原因而出現在其他解決方案的上方。</span><span class="sxs-lookup"><span data-stu-id="f4e55-111">gRPC stands above other solutions for the following reasons.</span></span>

### <a name="performance"></a><span data-ttu-id="f4e55-112">效能</span><span class="sxs-lookup"><span data-stu-id="f4e55-112">Performance</span></span>

<span data-ttu-id="f4e55-113">使用 HTTP/2 而不是 HTTP/1.1 時，不需要人們可讀取的訊息，而是改用較小、更快的二進位通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f4e55-113">Using HTTP/2 rather than HTTP/1.1 removes the requirement for human-readable messages and instead uses the smaller, faster binary protocol.</span></span> <span data-ttu-id="f4e55-114">這對電腦進行剖析更有效率。</span><span class="sxs-lookup"><span data-stu-id="f4e55-114">This is more efficient for computers to parse.</span></span> <span data-ttu-id="f4e55-115">HTTP/2 也支援透過單一連接的多工要求。</span><span class="sxs-lookup"><span data-stu-id="f4e55-115">HTTP/2 also supports multiplexing requests over a single connection.</span></span> <span data-ttu-id="f4e55-116">這項支援可讓您立即傳送回應，而不需要在佇列中等候。</span><span class="sxs-lookup"><span data-stu-id="f4e55-116">This support enables responses to be sent as soon as they're ready without the need to wait in a queue.</span></span> <span data-ttu-id="f4e55-117"> (在 HTTP/1.1 中，此問題稱為「前端 (阻) 封鎖」。) 您在使用 gRPC 時需要較少的資源，這讓它成為適用于行動裝置和較慢網路的絕佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="f4e55-117">(In HTTP/1.1, this issue is known as "head-of-line (HOL) blocking.") You need fewer resources when using gRPC, which makes it a good solution to use for mobile devices and over slower networks.</span></span>

### <a name="interoperability"></a><span data-ttu-id="f4e55-118">互通性</span><span class="sxs-lookup"><span data-stu-id="f4e55-118">Interoperability</span></span>

<span data-ttu-id="f4e55-119">所有主要的程式設計語言和平臺都有 gRPC 的工具和程式庫，包括 .NET、JAVA、Python、Go、c + +、Node.js、Swift、Dart、Ruby 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="f4e55-119">There are gRPC tools and libraries for all major programming languages and platforms, including .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby, and PHP.</span></span> <span data-ttu-id="f4e55-120">多虧了通訊協定緩衝區的二進位電傳格式和有效率的程式碼產生，開發人員可以建立高效能的應用程式，同時還能享受完整的跨平臺支援。</span><span class="sxs-lookup"><span data-stu-id="f4e55-120">Thanks to the Protocol Buffers binary wire format and the efficient code generation for each platform, developers can build performant apps while still enjoying full cross-platform support.</span></span>

### <a name="usability-and-productivity"></a><span data-ttu-id="f4e55-121">可用性和產能</span><span class="sxs-lookup"><span data-stu-id="f4e55-121">Usability and productivity</span></span>

<span data-ttu-id="f4e55-122">gRPC 是全方位的 RPC 解決方案。</span><span class="sxs-lookup"><span data-stu-id="f4e55-122">gRPC is a comprehensive RPC solution.</span></span> <span data-ttu-id="f4e55-123">它在多種語言和平臺上都能一致地運作。</span><span class="sxs-lookup"><span data-stu-id="f4e55-123">It works consistently across multiple languages and platforms.</span></span> <span data-ttu-id="f4e55-124">它也提供絕佳的工具，並自動產生許多必要的重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4e55-124">It also provides excellent tooling, with much of the necessary boilerplate code automatically generated.</span></span> <span data-ttu-id="f4e55-125">因此，更多的開發人員時間會釋出以專注于商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="f4e55-125">So more developer time is freed up to focus on business logic.</span></span>

### <a name="streaming"></a><span data-ttu-id="f4e55-126">串流</span><span class="sxs-lookup"><span data-stu-id="f4e55-126">Streaming</span></span>

<span data-ttu-id="f4e55-127">gRPC 具有完整的雙向串流，可提供 WCF 雙工服務的類似功能。</span><span class="sxs-lookup"><span data-stu-id="f4e55-127">gRPC has full bidirectional streaming, which provides similar functionality to WCF's full-duplex services.</span></span> <span data-ttu-id="f4e55-128">gRPC 串流可以透過一般的網際網路連線、負載平衡器和服務網格來運作。</span><span class="sxs-lookup"><span data-stu-id="f4e55-128">gRPC streaming can operate over regular internet connections, load balancers, and service meshes.</span></span>

### <a name="deadlinetimeouts-and-cancellation"></a><span data-ttu-id="f4e55-129">期限/超時和取消</span><span class="sxs-lookup"><span data-stu-id="f4e55-129">Deadline/timeouts and cancellation</span></span>

<span data-ttu-id="f4e55-130">gRPC 可讓用戶端指定 RPC 完成的最長時間。</span><span class="sxs-lookup"><span data-stu-id="f4e55-130">gRPC allows clients to specify a maximum time for an RPC to finish.</span></span> <span data-ttu-id="f4e55-131">如果超過指定的期限，伺服器可以在用戶端之外取消作業。</span><span class="sxs-lookup"><span data-stu-id="f4e55-131">If the specified deadline is exceeded, the server can cancel the operation independently of the client.</span></span> <span data-ttu-id="f4e55-132">期限和取消可透過進一步的 gRPC 呼叫傳播，以協助強制執行資源使用量限制。</span><span class="sxs-lookup"><span data-stu-id="f4e55-132">Deadlines and cancellations can be propagated through further gRPC calls to help enforce resource usage limits.</span></span> <span data-ttu-id="f4e55-133">用戶端也可以在超過期限時或稍早（如 (有需要）的情況下停止作業（例如，因為使用者互動) ）。</span><span class="sxs-lookup"><span data-stu-id="f4e55-133">Clients can also stop operations when a deadline is exceeded, or earlier if necessary (for example, because of a user interaction).</span></span>

### <a name="security"></a><span data-ttu-id="f4e55-134">安全性</span><span class="sxs-lookup"><span data-stu-id="f4e55-134">Security</span></span>

<span data-ttu-id="f4e55-135">gRPC 在透過 TLS 端對端加密連線使用 HTTP/2 時，會隱含地受到保護。</span><span class="sxs-lookup"><span data-stu-id="f4e55-135">gRPC is implicitly secure when it's using HTTP/2 over a TLS end-to-end encrypted connection.</span></span> <span data-ttu-id="f4e55-136">支援用戶端憑證驗證 (請參閱 [第6章](security.md)) 進一步提高用戶端與伺服器之間的安全性與信任。</span><span class="sxs-lookup"><span data-stu-id="f4e55-136">Support for client certificate authentication (see [chapter 6](security.md)) further increases security and trust between client and server.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f4e55-137">[上一個](network-protocols.md) 
>[下一步](protocol-buffers.md)</span><span class="sxs-lookup"><span data-stu-id="f4e55-137">[Previous](network-protocols.md)
[Next](protocol-buffers.md)</span></span>
