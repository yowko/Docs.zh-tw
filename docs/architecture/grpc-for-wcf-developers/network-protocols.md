---
title: 網路通訊協定-適用于 WCF 開發人員的 gRPC
description: GRPC 網路通訊協定的總覽。
ms.date: 09/02/2019
ms.openlocfilehash: 801d57c95aec748e5dcf667ca480775ff945b55c
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938555"
---
# <a name="network-protocols"></a><span data-ttu-id="c72d6-103">網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="c72d6-103">Network protocols</span></span>

<span data-ttu-id="c72d6-104">不同于 WCF) 的 Windows Communication Foundation (，gRPC 會使用 HTTP/2 做為其網路功能的基礎。</span><span class="sxs-lookup"><span data-stu-id="c72d6-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="c72d6-105">此通訊協定可提供比 WCF 和 SOAP 更顯著的優點，而這只會在 HTTP/1.1 上運作。</span><span class="sxs-lookup"><span data-stu-id="c72d6-105">This protocol offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="c72d6-106">對於想要使用 gRPC 的開發人員，假設沒有 HTTP/2 的替代方案，則看起來應該是更詳細探索 HTTP/2 的理想時機，並找出使用 gRPC 的其他好處。</span><span class="sxs-lookup"><span data-stu-id="c72d6-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="c72d6-107">由2015中的網際網路工程任務推動小組所發行的 HTTP/2，衍生自已由 Google 使用的實驗性 SPDY 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c72d6-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="c72d6-108">其設計目的是要比 HTTP/1.1 更有效率、更快速且更安全。</span><span class="sxs-lookup"><span data-stu-id="c72d6-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="c72d6-109">HTTP/2 的主要功能</span><span class="sxs-lookup"><span data-stu-id="c72d6-109">Key features of HTTP/2</span></span>

<span data-ttu-id="c72d6-110">此清單顯示 HTTP/2 的一些主要功能和優點：</span><span class="sxs-lookup"><span data-stu-id="c72d6-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="c72d6-111">二進位通訊協定</span><span class="sxs-lookup"><span data-stu-id="c72d6-111">Binary protocol</span></span>

<span data-ttu-id="c72d6-112">要求/回應迴圈不再需要文字命令。</span><span class="sxs-lookup"><span data-stu-id="c72d6-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="c72d6-113">此活動可簡化並加速命令的執行。</span><span class="sxs-lookup"><span data-stu-id="c72d6-113">This activity simplifies and speeds up the implementation of commands.</span></span> <span data-ttu-id="c72d6-114">具體來說，剖析資料的速度較快，且使用的記憶體較少，網路延遲會因為速度明顯的相關改良而降低，而網路資源的整體使用也會更好。</span><span class="sxs-lookup"><span data-stu-id="c72d6-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="c72d6-115">串流</span><span class="sxs-lookup"><span data-stu-id="c72d6-115">Streams</span></span>

<span data-ttu-id="c72d6-116">資料流程可讓您建立傳送者與收件者之間的長期連接，以非同步方式傳送多個訊息或框架。</span><span class="sxs-lookup"><span data-stu-id="c72d6-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="c72d6-117">多個資料流程可以在單一 HTTP/2 連接上獨立運作。</span><span class="sxs-lookup"><span data-stu-id="c72d6-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="c72d6-118">透過單一 TCP 連接要求多工</span><span class="sxs-lookup"><span data-stu-id="c72d6-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="c72d6-119">這項功能是 HTTP/2 最重要的創新之一。</span><span class="sxs-lookup"><span data-stu-id="c72d6-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="c72d6-120">因為它允許對資料進行多個平行要求，所以現在可以從單一伺服器同時下載 web 檔案。</span><span class="sxs-lookup"><span data-stu-id="c72d6-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="c72d6-121">網站的載入速度更快，而優化的需求也會降低。</span><span class="sxs-lookup"><span data-stu-id="c72d6-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="c72d6-122">標頭 (住) 封鎖的情況下，已就緒的回應必須等待傳送，直到先前的要求完成為止 (，但仍封鎖仍可在) 的 TCP 傳輸層級進行。</span><span class="sxs-lookup"><span data-stu-id="c72d6-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="c72d6-123">Net.tcp （類似 TCP）效能，跨平臺</span><span class="sxs-lookup"><span data-stu-id="c72d6-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="c72d6-124">基本上，gRPC 和 HTTP/2 的組合可為開發人員提供 WCF 的 Net.tcp 系結的同等速度和效率，而且在某些情況下，速度和效率更高。</span><span class="sxs-lookup"><span data-stu-id="c72d6-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="c72d6-125">但是，與 Net.tcp 不同的是，透過 HTTP/2 的 gRPC 不受限於 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c72d6-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c72d6-126">[上一個](interface-definition-language.md) 
>[下一步](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="c72d6-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
