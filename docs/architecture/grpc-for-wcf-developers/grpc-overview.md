---
title: 適用于 WCF 開發人員的 gRPC-gRPC 總覽
description: 瞭解指導 gRPC 開發的一組原則。
ms.date: 12/15/2020
ms.openlocfilehash: 99e1bdb1f49469f444044027c3ac5d927f9cab13
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938399"
---
# <a name="grpc-overview"></a><span data-ttu-id="d6690-103">gRPC 總覽</span><span class="sxs-lookup"><span data-stu-id="d6690-103">gRPC overview</span></span>

<span data-ttu-id="d6690-104">在查看 Windows Communication Foundation 的 (WCF) 和 gRPC 的創世之後，這一章會考慮 gRPC 的一些主要功能，以及它們與 WCF 的比較。</span><span class="sxs-lookup"><span data-stu-id="d6690-104">After looking at the genesis of both Windows Communication Foundation (WCF) and gRPC in the last chapter, this chapter considers some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="d6690-105">ASP.NET Core 3.0 是原生支援 gRPC 的第一版 ASP.NET，其中的 Microsoft 團隊會參與 gRPC 的官方 .NET 實施。</span><span class="sxs-lookup"><span data-stu-id="d6690-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="d6690-106">建議您使用 .NET 來建立分散式應用程式，以便與其他主要的程式設計語言和架構交互操作。</span><span class="sxs-lookup"><span data-stu-id="d6690-106">It's recommended for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="d6690-107">主要原則</span><span class="sxs-lookup"><span data-stu-id="d6690-107">Key principles</span></span>

<span data-ttu-id="d6690-108">如第1章所述，Google 希望使用 HTTP/2 的引進來取代 Stubby，也就是其內部的一般用途 RPC 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d6690-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to replace Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="d6690-109">以 Stubby 為基礎的 gRPC 現在可以利用標準化，並將其適用性延伸至行動運算、雲端及物聯網。</span><span class="sxs-lookup"><span data-stu-id="d6690-109">gRPC, based on Stubby, now can take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="d6690-110">為了達成這項標準化， [雲端原生運算基礎 (CNCF) ](https://www.cncf.io/) 建立了一組管理 gRPC 的原則。</span><span class="sxs-lookup"><span data-stu-id="d6690-110">To achieve this standardization, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="d6690-111">下列清單顯示最相關的專案，其主要考慮最大化的存取範圍和可用性：</span><span class="sxs-lookup"><span data-stu-id="d6690-111">The following list shows the most relevant ones, which are primarily concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="d6690-112">**免費且開放** ：所有成品都應該是開放原始碼，並具有授權，而不會限制開發人員採用 gRPC。</span><span class="sxs-lookup"><span data-stu-id="d6690-112">**Free and open** – All artifacts should be open source, with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="d6690-113">**涵蓋範圍和簡單性** – gRPC 應該可在每個受歡迎的平臺上使用，且相當簡單，可以在任何平臺上建立。</span><span class="sxs-lookup"><span data-stu-id="d6690-113">**Coverage and simplicity** – gRPC should be available across every popular platform, and simple enough to build on any platform.</span></span>
- <span data-ttu-id="d6690-114">**互通性和觸及** –無論頻寬或延遲為何，都應該使用廣泛可用的網路標準，在任何網路上使用 gRPC。</span><span class="sxs-lookup"><span data-stu-id="d6690-114">**Interoperability and reach** – It should be possible to use gRPC on any network, regardless of bandwidth or latency, by using widely available network standards.</span></span>
- <span data-ttu-id="d6690-115">**一般用途和** 效能–架構應該盡可能廣泛使用案例，而不會影響效能。</span><span class="sxs-lookup"><span data-stu-id="d6690-115">**General purpose and performant** – The framework should be usable by as broad a range of use-cases as possible, without compromising performance.</span></span>
- <span data-ttu-id="d6690-116">**串流** –通訊協定應提供大型資料集或非同步訊息的資料流程處理。</span><span class="sxs-lookup"><span data-stu-id="d6690-116">**Streaming** – The protocol should provide streaming semantics for large datasets or asynchronous messaging.</span></span>
- <span data-ttu-id="d6690-117">**中繼資料交換** -通訊協定可讓非商務資料（例如驗證權杖）與實際商務資料分開處理。</span><span class="sxs-lookup"><span data-stu-id="d6690-117">**Metadata exchange** – The protocol allows non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="d6690-118">**標準化狀態碼** –應減少錯誤碼的變化性，讓錯誤處理決策更清楚。</span><span class="sxs-lookup"><span data-stu-id="d6690-118">**Standardized status codes** – The variability of error codes should be reduced to make error handling decisions clearer.</span></span> <span data-ttu-id="d6690-119">如果需要更豐富的錯誤處理，則應該提供機制來管理中繼資料交換內的行為。</span><span class="sxs-lookup"><span data-stu-id="d6690-119">Where additional, richer error handling is required, a mechanism should be provided for managing behavior within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d6690-120">[上一個](introduction.md) 
>[下一步](approach.md)</span><span class="sxs-lookup"><span data-stu-id="d6690-120">[Previous](introduction.md)
[Next](approach.md)</span></span>
