---
title: 為什麼我們為 WCF 開發人員推薦 gRPC - gRPC 面向 WCF 開發人員
description: 討論 gRPC 為什麼非常適合想要遷移到現代體系結構和平臺的 WCF 開發人員。
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147642"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a><span data-ttu-id="b9b13-103">為何我們為 WCF 開發人員建議 gRPC</span><span class="sxs-lookup"><span data-stu-id="b9b13-103">Why we recommend gRPC for WCF developers</span></span>

<span data-ttu-id="b9b13-104">在我們深入探討 gRPC 的語言和技術之前，值得討論為什麼 gRPC 是 Windows 通信基礎 （WCF） 開發人員想要遷移到 .NET Core 的正確解決方案。</span><span class="sxs-lookup"><span data-stu-id="b9b13-104">Before we dive deeply into the language and techniques of gRPC, it's worth discussing why gRPC is the right solution for Windows Communication Foundation (WCF) developers who want to migrate to .NET Core.</span></span>

## <a name="similarity-to-wcf"></a><span data-ttu-id="b9b13-105">與 WCF 的相似性</span><span class="sxs-lookup"><span data-stu-id="b9b13-105">Similarity to WCF</span></span>

<span data-ttu-id="b9b13-106">儘管 gRPC 的實現和方法不同，但使用 gRPC 開發和使用服務的經驗對於 WCF 開發人員來說應該是直觀的。</span><span class="sxs-lookup"><span data-stu-id="b9b13-106">Although the implementation and approach are different for gRPC, the experience of developing and consuming services with gRPC should be intuitive for WCF developers.</span></span> <span data-ttu-id="b9b13-107">基本目標是相同的：使用戶端和伺服器位於同一平臺上，無需擔心網路，可以編寫代碼。</span><span class="sxs-lookup"><span data-stu-id="b9b13-107">The underlying goal is the same: make it possible to code as though the client and server are on the same platform, without needing to worry about networking.</span></span>

<span data-ttu-id="b9b13-108">兩個平臺共用聲明然後實現介面的原則，即使聲明該介面的過程是不同的。</span><span class="sxs-lookup"><span data-stu-id="b9b13-108">Both platforms share the principle of declaring and then implementing an interface, even though the process for declaring that interface is different.</span></span> <span data-ttu-id="b9b13-109">正如您將在第 5 章中看到的，gRPC 支援的不同類型的 RPC 調用很好地映射到 WCF 服務可用的綁定。</span><span class="sxs-lookup"><span data-stu-id="b9b13-109">And as you'll see in chapter 5, the different types of RPC calls that gRPC supports map well to the bindings available to WCF services.</span></span>

## <a name="benefits-of-grpc"></a><span data-ttu-id="b9b13-110">gRPC 的好處</span><span class="sxs-lookup"><span data-stu-id="b9b13-110">Benefits of gRPC</span></span>

<span data-ttu-id="b9b13-111">gRPC 高於其他解決方案，原因如下。</span><span class="sxs-lookup"><span data-stu-id="b9b13-111">gRPC stands above other solutions for the following reasons.</span></span>

### <a name="performance"></a><span data-ttu-id="b9b13-112">效能</span><span class="sxs-lookup"><span data-stu-id="b9b13-112">Performance</span></span>

<span data-ttu-id="b9b13-113">使用 HTTP/2 而不是 HTTP/1.1 可消除對人可讀消息的要求，而是使用更小、更快的二進位協定。</span><span class="sxs-lookup"><span data-stu-id="b9b13-113">Using HTTP/2 rather than HTTP/1.1 removes the requirement for human-readable messages and instead uses the smaller, faster binary protocol.</span></span> <span data-ttu-id="b9b13-114">這對電腦進行分析的效率更高。</span><span class="sxs-lookup"><span data-stu-id="b9b13-114">This is more efficient for computers to parse.</span></span> <span data-ttu-id="b9b13-115">HTTP/2 還支援通過單個連接進行多工請求。</span><span class="sxs-lookup"><span data-stu-id="b9b13-115">HTTP/2 also supports multiplexing requests over a single connection.</span></span> <span data-ttu-id="b9b13-116">此支援允許在回應準備就緒後立即發送，而無需在佇列中等待。</span><span class="sxs-lookup"><span data-stu-id="b9b13-116">This support enables responses to be sent as soon as they're ready without the need to wait in a queue.</span></span> <span data-ttu-id="b9b13-117">（在 HTTP/1.1 中，此問題稱為"線頭 （HOL） 阻塞"。使用 gRPC 時需要的資源更少，這使得它成為用於行動裝置和速度較慢的網路的良好解決方案。</span><span class="sxs-lookup"><span data-stu-id="b9b13-117">(In HTTP/1.1, this issue is known as "head-of-line (HOL) blocking.") You need fewer resources when using gRPC, which makes it a good solution to use for mobile devices and over slower networks.</span></span>

### <a name="interoperability"></a><span data-ttu-id="b9b13-118">互通性</span><span class="sxs-lookup"><span data-stu-id="b9b13-118">Interoperability</span></span>

<span data-ttu-id="b9b13-119">所有主要程式設計語言和平臺都有 gRPC 工具和庫，包括 .NET、JAVA、Python、Go、C++、Node.js、Swift、Dart、Ruby 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="b9b13-119">There are gRPC tools and libraries for all major programming languages and platforms, including .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby, and PHP.</span></span> <span data-ttu-id="b9b13-120">得益于協定緩衝區二進位線格式和每個平臺的有效代碼生成，開發人員可以構建執行應用程式，同時仍然享受全面的跨平臺支援。</span><span class="sxs-lookup"><span data-stu-id="b9b13-120">Thanks to the Protocol Buffers binary wire format and the efficient code generation for each platform, developers can build performant apps while still enjoying full cross-platform support.</span></span>

### <a name="usability-and-productivity"></a><span data-ttu-id="b9b13-121">可用性和產能</span><span class="sxs-lookup"><span data-stu-id="b9b13-121">Usability and productivity</span></span>

<span data-ttu-id="b9b13-122">gRPC 是一個全面的 RPC 解決方案。</span><span class="sxs-lookup"><span data-stu-id="b9b13-122">gRPC is a comprehensive RPC solution.</span></span> <span data-ttu-id="b9b13-123">它在多種語言和平臺上一致工作。</span><span class="sxs-lookup"><span data-stu-id="b9b13-123">It works consistently across multiple languages and platforms.</span></span> <span data-ttu-id="b9b13-124">它還提供了出色的工具，自動生成許多必要的樣板代碼。</span><span class="sxs-lookup"><span data-stu-id="b9b13-124">It also provides excellent tooling, with much of the necessary boilerplate code automatically generated.</span></span> <span data-ttu-id="b9b13-125">因此，可以騰出更多開發人員時間來關注業務邏輯。</span><span class="sxs-lookup"><span data-stu-id="b9b13-125">So more developer time is freed up to focus on business logic.</span></span>

### <a name="streaming"></a><span data-ttu-id="b9b13-126">串流</span><span class="sxs-lookup"><span data-stu-id="b9b13-126">Streaming</span></span>

<span data-ttu-id="b9b13-127">gRPC 具有完全雙向流式處理，提供與 WCF 全雙工服務類似的功能。</span><span class="sxs-lookup"><span data-stu-id="b9b13-127">gRPC has full bidirectional streaming, which provides similar functionality to WCF's full duplex services.</span></span> <span data-ttu-id="b9b13-128">gRPC 流可以通過常規互聯網連接、負載等化器和服務聯結運行。</span><span class="sxs-lookup"><span data-stu-id="b9b13-128">gRPC streaming can operate over regular internet connections, load balancers, and service meshes.</span></span>

### <a name="deadlinetimeouts-and-cancellation"></a><span data-ttu-id="b9b13-129">截止日期/超時和取消</span><span class="sxs-lookup"><span data-stu-id="b9b13-129">Deadline/timeouts and cancellation</span></span>

<span data-ttu-id="b9b13-130">gRPC 允許用戶端指定 RPC 完成的最大時間。</span><span class="sxs-lookup"><span data-stu-id="b9b13-130">gRPC allows clients to specify a maximum time for an RPC to finish.</span></span> <span data-ttu-id="b9b13-131">如果超過指定的截止時間，伺服器可以獨立于用戶端取消操作。</span><span class="sxs-lookup"><span data-stu-id="b9b13-131">If the specified deadline is exceeded, the server can cancel the operation independently of the client.</span></span> <span data-ttu-id="b9b13-132">截止和取消可以通過進一步的 gRPC 調用傳播，以説明強制實施資源使用限制。</span><span class="sxs-lookup"><span data-stu-id="b9b13-132">Deadlines and cancellations can be propagated through further gRPC calls to help enforce resource usage limits.</span></span> <span data-ttu-id="b9b13-133">用戶端也可以在超過截止時間時停止操作，或者在必要時更早停止操作（例如，由於使用者交互）。</span><span class="sxs-lookup"><span data-stu-id="b9b13-133">Clients can also stop operations when a deadline is exceeded, or earlier if necessary (for example, because of a user interaction).</span></span>

### <a name="security"></a><span data-ttu-id="b9b13-134">安全性</span><span class="sxs-lookup"><span data-stu-id="b9b13-134">Security</span></span>

<span data-ttu-id="b9b13-135">gRPC 在 TLS 端到端加密連接上使用 HTTP/2 時具有隱式安全。</span><span class="sxs-lookup"><span data-stu-id="b9b13-135">gRPC is implicitly secure when it's using HTTP/2 over a TLS end-to-end encrypted connection.</span></span> <span data-ttu-id="b9b13-136">對用戶端憑證身份驗證的支援（參見[第 6 章](security.md)）進一步增強了用戶端和伺服器之間的安全性和信任。</span><span class="sxs-lookup"><span data-stu-id="b9b13-136">Support for client certificate authentication (see [chapter 6](security.md)) further increases security and trust between client and server.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b9b13-137">[上一個](network-protocols.md)
>[下一個](protocol-buffers.md)</span><span class="sxs-lookup"><span data-stu-id="b9b13-137">[Previous](network-protocols.md)
[Next](protocol-buffers.md)</span></span>
