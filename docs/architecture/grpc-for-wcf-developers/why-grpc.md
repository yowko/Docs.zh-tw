---
title: 為什麼我們建議 WCF 開發人員的 gRPC-針對 WCF 開發人員的 gRPC
description: 討論為什麼 gRPC 是適合想要遷移至現代化架構和平臺的 WCF 開發人員。
ms.date: 09/02/2019
ms.openlocfilehash: fc93ca4c8f2a28dc4d3a0b0466d19c86273b40b8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503321"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a><span data-ttu-id="33dc2-103">為什麼我們建議 WCF 開發人員 gRPC</span><span class="sxs-lookup"><span data-stu-id="33dc2-103">Why we recommend gRPC for WCF developers</span></span>

<span data-ttu-id="33dc2-104">在深入探討 gRPC 的語言和技術之前，值得討論為什麼 gRPC 是適合想要遷移至 .NET Core 之 Windows Communication Foundation （WCF）開發人員的正確解決方案。</span><span class="sxs-lookup"><span data-stu-id="33dc2-104">Before we dive deeply into the language and techniques of gRPC, it's worth discussing why gRPC is the right solution for Windows Communication Foundation (WCF) developers who want to migrate to .NET Core.</span></span>

## <a name="similarity-to-wcf"></a><span data-ttu-id="33dc2-105">WCF 的相似性</span><span class="sxs-lookup"><span data-stu-id="33dc2-105">Similarity to WCF</span></span>

<span data-ttu-id="33dc2-106">雖然 gRPC 的實和方法不同，但使用 gRPC 開發和使用服務的經驗，對於 WCF 開發人員而言應該是直覺的。</span><span class="sxs-lookup"><span data-stu-id="33dc2-106">Although the implementation and approach are different for gRPC, the experience of developing and consuming services with gRPC should be intuitive for WCF developers.</span></span> <span data-ttu-id="33dc2-107">基礎目標是相同的：讓程式碼可以如同用戶端和伺服器位於相同的平臺上，而不需要擔心網路功能。</span><span class="sxs-lookup"><span data-stu-id="33dc2-107">The underlying goal is the same: make it possible to code as though the client and server are on the same platform, without needing to worry about networking.</span></span> 

<span data-ttu-id="33dc2-108">這兩種平臺都共用宣告和執行介面的原則，即使宣告該介面的程式不同也是一樣。</span><span class="sxs-lookup"><span data-stu-id="33dc2-108">Both platforms share the principle of declaring and then implementing an interface, even though the process for declaring that interface is different.</span></span> <span data-ttu-id="33dc2-109">如您在第5章所見，gRPC 支援的各種 RPC 呼叫類型，都能正確對應到 WCF 服務可用的系結。</span><span class="sxs-lookup"><span data-stu-id="33dc2-109">And as you'll see in chapter 5, the different types of RPC calls that gRPC supports map well to the bindings available to WCF services.</span></span>

## <a name="benefits-of-grpc"></a><span data-ttu-id="33dc2-110">GRPC 的優點</span><span class="sxs-lookup"><span data-stu-id="33dc2-110">Benefits of gRPC</span></span>

<span data-ttu-id="33dc2-111">gRPC 會因下列原因而代表其他解決方案。</span><span class="sxs-lookup"><span data-stu-id="33dc2-111">gRPC stands above other solutions for the following reasons.</span></span>

### <a name="performance"></a><span data-ttu-id="33dc2-112">效能</span><span class="sxs-lookup"><span data-stu-id="33dc2-112">Performance</span></span>

<span data-ttu-id="33dc2-113">使用 HTTP/2 而不是 HTTP/1.1，會移除人們可讀取訊息的需求，而改為使用較小、更快的二進位通訊協定。</span><span class="sxs-lookup"><span data-stu-id="33dc2-113">Using HTTP/2 rather than HTTP/1.1 removes the requirement for human-readable messages and instead uses the smaller, faster binary protocol.</span></span> <span data-ttu-id="33dc2-114">這對於要剖析的電腦更有效率。</span><span class="sxs-lookup"><span data-stu-id="33dc2-114">This is more efficient for computers to parse.</span></span> <span data-ttu-id="33dc2-115">HTTP/2 也支援透過單一連接進行多工處理要求。</span><span class="sxs-lookup"><span data-stu-id="33dc2-115">HTTP/2 also supports multiplexing requests over a single connection.</span></span> <span data-ttu-id="33dc2-116">這項支援可讓回應在準備好時立即傳送，而不需要在佇列中等候。</span><span class="sxs-lookup"><span data-stu-id="33dc2-116">This support enables responses to be sent as soon as they're ready without the need to wait in a queue.</span></span> <span data-ttu-id="33dc2-117">（在 HTTP/1.1 中，此問題稱為「行首（逾越）封鎖」）。使用 gRPC 時，您需要較少的資源，這讓它成為適用于行動裝置和較慢網路的絕佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="33dc2-117">(In HTTP/1.1, this issue is known as "head-of-line (HOL) blocking.") You need fewer resources when using gRPC, which makes it a good solution to use for mobile devices and over slower networks.</span></span>

### <a name="interoperability"></a><span data-ttu-id="33dc2-118">互通性</span><span class="sxs-lookup"><span data-stu-id="33dc2-118">Interoperability</span></span>

<span data-ttu-id="33dc2-119">有適用于所有主要程式設計語言和平臺的 gRPC 工具和程式庫，包括 .NET、JAVA、Python C++、Go、Node.js、Swift、Dart、RUBY 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="33dc2-119">There are gRPC tools and libraries for all major programming languages and platforms, including .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby, and PHP.</span></span> <span data-ttu-id="33dc2-120">由於通訊協定會緩衝二進位電傳格式，並為每個平臺產生有效率的程式碼，因此開發人員可以建立高效能的應用程式，同時仍然享有完整的跨平臺支援。</span><span class="sxs-lookup"><span data-stu-id="33dc2-120">Thanks to the Protocol Buffers binary wire format and the efficient code generation for each platform, developers can build performant apps while still enjoying full cross-platform support.</span></span>

### <a name="usability-and-productivity"></a><span data-ttu-id="33dc2-121">可用性和產能</span><span class="sxs-lookup"><span data-stu-id="33dc2-121">Usability and productivity</span></span>

<span data-ttu-id="33dc2-122">gRPC 是一套完整的 RPC 解決方案。</span><span class="sxs-lookup"><span data-stu-id="33dc2-122">gRPC is a comprehensive RPC solution.</span></span> <span data-ttu-id="33dc2-123">它在多種語言和平臺上一致運作。</span><span class="sxs-lookup"><span data-stu-id="33dc2-123">It works consistently across multiple languages and platforms.</span></span> <span data-ttu-id="33dc2-124">它也提供絕佳的工具，並自動產生許多必要的重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="33dc2-124">It also provides excellent tooling, with much of the necessary boilerplate code automatically generated.</span></span> <span data-ttu-id="33dc2-125">更多的開發人員時間會被釋出，以專注于商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="33dc2-125">So more developer time is freed up to focus on business logic.</span></span>

### <a name="streaming"></a><span data-ttu-id="33dc2-126">串流</span><span class="sxs-lookup"><span data-stu-id="33dc2-126">Streaming</span></span>

<span data-ttu-id="33dc2-127">gRPC 具有完整的雙向串流，可提供 WCF 的全雙工服務的類似功能。</span><span class="sxs-lookup"><span data-stu-id="33dc2-127">gRPC has full bidirectional streaming, which provides similar functionality to WCF's full duplex services.</span></span> <span data-ttu-id="33dc2-128">gRPC 串流可以透過一般的網際網路連線、負載平衡器和服務網格運作。</span><span class="sxs-lookup"><span data-stu-id="33dc2-128">gRPC streaming can operate over regular internet connections, load balancers, and service meshes.</span></span>

### <a name="deadlinetimeouts-and-cancellation"></a><span data-ttu-id="33dc2-129">期限/超時和取消</span><span class="sxs-lookup"><span data-stu-id="33dc2-129">Deadline/timeouts and cancellation</span></span>

<span data-ttu-id="33dc2-130">gRPC 可讓用戶端指定 RPC 完成的最長時間。</span><span class="sxs-lookup"><span data-stu-id="33dc2-130">gRPC allows clients to specify a maximum time for an RPC to finish.</span></span> <span data-ttu-id="33dc2-131">如果超過指定的期限，伺服器就可以取消用戶端獨立的作業。</span><span class="sxs-lookup"><span data-stu-id="33dc2-131">If the specified deadline is exceeded, the server can cancel the operation independently of the client.</span></span> <span data-ttu-id="33dc2-132">您可以透過進一步的 gRPC 呼叫來傳播期限和取消，以協助強制執行資源使用限制。</span><span class="sxs-lookup"><span data-stu-id="33dc2-132">Deadlines and cancellations can be propagated through further gRPC calls to help enforce resource usage limits.</span></span> <span data-ttu-id="33dc2-133">用戶端也可以在超過期限時停止作業，或在必要時（例如，因為使用者互動）。</span><span class="sxs-lookup"><span data-stu-id="33dc2-133">Clients can also stop operations when a deadline is exceeded, or earlier if necessary (for example, because of a user interaction).</span></span>

### <a name="security"></a><span data-ttu-id="33dc2-134">安全性</span><span class="sxs-lookup"><span data-stu-id="33dc2-134">Security</span></span>

<span data-ttu-id="33dc2-135">當 gRPC 透過 TLS 端對端加密連線使用 HTTP/2 時，會隱含地保護。</span><span class="sxs-lookup"><span data-stu-id="33dc2-135">gRPC is implicitly secure when it's using HTTP/2 over a TLS end-to-end encrypted connection.</span></span> <span data-ttu-id="33dc2-136">支援用戶端憑證驗證（請參閱[第6章](security.md)）進一步增加用戶端與伺服器之間的安全性和信任。</span><span class="sxs-lookup"><span data-stu-id="33dc2-136">Support for client certificate authentication (see [chapter 6](security.md)) further increases security and trust between client and server.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="33dc2-137">[上一頁](network-protocols.md)
>[下一頁](protocol-buffers.md)</span><span class="sxs-lookup"><span data-stu-id="33dc2-137">[Previous](network-protocols.md)
[Next](protocol-buffers.md)</span></span>
