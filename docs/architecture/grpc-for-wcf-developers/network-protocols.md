---
title: 網路通訊協定-WCF 開發人員的 gRPC
description: GRPC 網路通訊協定的總覽。
ms.date: 09/02/2019
ms.openlocfilehash: 1ceb140f7b7ac7e796a87612ebb9d21e28d33968
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628484"
---
# <a name="network-protocols"></a><span data-ttu-id="55911-103">網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="55911-103">Network protocols</span></span>

<span data-ttu-id="55911-104">不同于 Windows Communication Foundation （WCF），gRPC 會使用 HTTP/2 做為其網路功能的基礎。</span><span class="sxs-lookup"><span data-stu-id="55911-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="55911-105">這在 WCF 和 SOAP 上提供顯著的優點，這只會在 HTTP/1.1 上運作。</span><span class="sxs-lookup"><span data-stu-id="55911-105">This offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="55911-106">對於想要使用 gRPC 的開發人員而言，假設沒有 HTTP/2 的替代方案，那麼最好的時機是探索 HTTP/2，並找出使用 gRPC 的其他優點。</span><span class="sxs-lookup"><span data-stu-id="55911-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="55911-107">2015中由網際網路工程任務推動小組發行的 HTTP/2 衍生自已由 Google 使用的實驗性 SPDY 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="55911-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="55911-108">其設計目的是要比 HTTP/1.1 更有效率、更快速且更安全。</span><span class="sxs-lookup"><span data-stu-id="55911-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="55911-109">HTTP/2 的主要功能</span><span class="sxs-lookup"><span data-stu-id="55911-109">Key features of HTTP/2</span></span>

<span data-ttu-id="55911-110">這份清單會顯示 HTTP/2 的一些主要功能和優點：</span><span class="sxs-lookup"><span data-stu-id="55911-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="55911-111">二進位通訊協定</span><span class="sxs-lookup"><span data-stu-id="55911-111">Binary protocol</span></span>

<span data-ttu-id="55911-112">要求/回應週期不再需要文字命令。</span><span class="sxs-lookup"><span data-stu-id="55911-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="55911-113">這可簡化和加速命令的執行。</span><span class="sxs-lookup"><span data-stu-id="55911-113">This simplifies and speeds up implementation of commands.</span></span> <span data-ttu-id="55911-114">具體而言，剖析資料的速度較快，且使用的記憶體較少，網路延遲會隨著速度的明顯相關改良而降低，而且會有更好的網路資源使用。</span><span class="sxs-lookup"><span data-stu-id="55911-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="55911-115">資料流</span><span class="sxs-lookup"><span data-stu-id="55911-115">Streams</span></span>

<span data-ttu-id="55911-116">資料流程可讓您在傳送者與接收者之間建立長期的連線，以便以非同步方式傳送多個訊息或框架。</span><span class="sxs-lookup"><span data-stu-id="55911-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="55911-117">多個資料流程可以在單一 HTTP/2 連接上獨立運作。</span><span class="sxs-lookup"><span data-stu-id="55911-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="55911-118">透過單一 TCP 連線要求多工處理</span><span class="sxs-lookup"><span data-stu-id="55911-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="55911-119">這項功能是 HTTP/2 其中一項最重要的創新。</span><span class="sxs-lookup"><span data-stu-id="55911-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="55911-120">因為它允許對資料進行多個平行要求，所以現在可以從單一伺服器同時下載 web 檔案。</span><span class="sxs-lookup"><span data-stu-id="55911-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="55911-121">網站的載入速度更快，而優化的需求也會減少。</span><span class="sxs-lookup"><span data-stu-id="55911-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="55911-122">標頭（逾越）封鎖，其中已準備好的回應必須等到先前的要求完成後才會被降低（雖然在 TCP 傳輸層級仍然會發生阻礙封鎖）。</span><span class="sxs-lookup"><span data-stu-id="55911-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="55911-123">Net.tcp like 效能，跨平臺</span><span class="sxs-lookup"><span data-stu-id="55911-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="55911-124">基本上，gRPC 和 HTTP/2 的組合可為開發人員提供與 WCF 的 Net.tcp 系結至少相等的速度和效率，而在某些情況下，甚至更快的速度和效率。</span><span class="sxs-lookup"><span data-stu-id="55911-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="55911-125">但不同于 Net.tcp，gRPC over HTTP/2 並不限於 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="55911-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="55911-126">[上一頁](interface-definition-language.md)
>[下一頁](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="55911-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
