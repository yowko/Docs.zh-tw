---
title: 串流服務與重複的欄位-適用于 WCF 開發人員的 gRPC
description: 比較重複的欄位與串流服務，做為使用 gRPC 傳遞資料集合的方式。
ms.date: 09/02/2019
ms.openlocfilehash: 0e717df57ba2bb52d63a063072d8a45bf0f7e395
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503380"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a><span data-ttu-id="2f900-103">gRPC 串流服務與重複欄位的比較</span><span class="sxs-lookup"><span data-stu-id="2f900-103">gRPC streaming services vs. repeated fields</span></span>

<span data-ttu-id="2f900-104">gRPC services 提供兩種方法來傳回資料集或物件清單。</span><span class="sxs-lookup"><span data-stu-id="2f900-104">gRPC services provide two ways of returning datasets, or lists of objects.</span></span> <span data-ttu-id="2f900-105">通訊協定緩衝區訊息規格會使用 `repeated` 關鍵字，來宣告另一個訊息中的清單或訊息陣列。</span><span class="sxs-lookup"><span data-stu-id="2f900-105">The Protocol Buffers message specification uses the `repeated` keyword for declaring lists or arrays of messages within another message.</span></span> <span data-ttu-id="2f900-106">GRPC 服務規格會使用 `stream` 關鍵字來宣告長時間執行的持續性連接。</span><span class="sxs-lookup"><span data-stu-id="2f900-106">The gRPC service specification uses the `stream` keyword to declare a long-running persistent connection.</span></span> <span data-ttu-id="2f900-107">透過該連接，就會傳送多則訊息，而且可以個別處理。</span><span class="sxs-lookup"><span data-stu-id="2f900-107">Over that connection, multiple messages are sent, and can be processed, individually.</span></span> 

<span data-ttu-id="2f900-108">您也可以使用 `stream` 功能進行長時間執行的時態性資料，例如通知或記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="2f900-108">You can also use the `stream` feature for long-running temporal data such as notifications or log messages.</span></span> <span data-ttu-id="2f900-109">但這一章會考慮使用它來傳回單一資料集。</span><span class="sxs-lookup"><span data-stu-id="2f900-109">But this chapter will consider its use for returning a single dataset.</span></span>

<span data-ttu-id="2f900-110">您應該使用的取決於下列因素：</span><span class="sxs-lookup"><span data-stu-id="2f900-110">Which you should use depends on factors such as:</span></span>

- <span data-ttu-id="2f900-111">資料集的整體大小。</span><span class="sxs-lookup"><span data-stu-id="2f900-111">The overall size of the dataset.</span></span>
- <span data-ttu-id="2f900-112">在用戶端或伺服器端建立資料集所花的時間。</span><span class="sxs-lookup"><span data-stu-id="2f900-112">The time it took to create the dataset at either the client or server end.</span></span>
- <span data-ttu-id="2f900-113">資料集的取用者是否可以在第一個專案可用時立即開始作用，或需要完整的資料集來執行任何有用的工作。</span><span class="sxs-lookup"><span data-stu-id="2f900-113">Whether the consumer of the dataset can start acting on it as soon as the first item is available, or needs the complete dataset to do anything useful.</span></span>

## <a name="when-to-use-repeated-fields"></a><span data-ttu-id="2f900-114">使用 `repeated` 欄位的時機</span><span class="sxs-lookup"><span data-stu-id="2f900-114">When to use `repeated` fields</span></span>

<span data-ttu-id="2f900-115">對於大小限制，而且可以在短時間內完整產生的任何資料集（例如，在一秒內），您應該使用一般 Protobuf 訊息中的 `repeated` 欄位。</span><span class="sxs-lookup"><span data-stu-id="2f900-115">For any dataset that's constrained in size and that can be generated in its entirety in a short time—say, under one second—you should use a `repeated` field in a regular Protobuf message.</span></span> <span data-ttu-id="2f900-116">例如，在電子商務系統中，若要建立訂單中的專案清單可能很快，而且清單不會很大。</span><span class="sxs-lookup"><span data-stu-id="2f900-116">For example, in an e-commerce system, to build a list of items within an order is probably quick and the list won't be very large.</span></span> <span data-ttu-id="2f900-117">以 `repeated` 欄位傳回單一訊息的順序，比使用 `stream` 更快，而且會產生較少的網路額外負荷。</span><span class="sxs-lookup"><span data-stu-id="2f900-117">Returning a single message with a `repeated` field is an order of magnitude faster than using `stream` and incurs less network overhead.</span></span>

<span data-ttu-id="2f900-118">如果用戶端在開始處理之前需要所有資料，而且資料集夠小，可在記憶體中建立，則請考慮使用 `repeated` 欄位。</span><span class="sxs-lookup"><span data-stu-id="2f900-118">If the client needs all the data before starting to process it and the dataset is small enough to construct in memory, then consider using a `repeated` field.</span></span> <span data-ttu-id="2f900-119">即使在伺服器的記憶體中建立資料集的速度較慢，也請考慮這一點。</span><span class="sxs-lookup"><span data-stu-id="2f900-119">Consider it even if the creation of the dataset in memory on the server is slower.</span></span>

## <a name="when-to-use-stream-methods"></a><span data-ttu-id="2f900-120">使用 `stream` 方法的時機</span><span class="sxs-lookup"><span data-stu-id="2f900-120">When to use `stream` methods</span></span>

<span data-ttu-id="2f900-121">當您資料集中的訊息物件可能非常大時，最好是使用串流要求或回應來傳輸它們。</span><span class="sxs-lookup"><span data-stu-id="2f900-121">When the message objects in your datasets are potentially very large, it's best for you transfer them by using streaming requests or responses.</span></span> <span data-ttu-id="2f900-122">在記憶體中建立大型物件、將它寫入網路，然後釋放資源，會更有效率。</span><span class="sxs-lookup"><span data-stu-id="2f900-122">It's more efficient to construct a large object in memory, write it to the network, and then free up the resources.</span></span> <span data-ttu-id="2f900-123">這種方法可以改善服務的擴充性。</span><span class="sxs-lookup"><span data-stu-id="2f900-123">This approach will improve the scalability of your service.</span></span>

<span data-ttu-id="2f900-124">同樣地，您應該在資料流程上傳送不受限制大小的資料集，以避免在進行處理時記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="2f900-124">Similarly, you should send datasets of unconstrained size over streams to avoid running out of memory while constructing them.</span></span>

<span data-ttu-id="2f900-125">對於取用者可以個別處理每個專案的資料集，您應該考慮使用資料流程（如果它表示進度可以向使用者表示）。</span><span class="sxs-lookup"><span data-stu-id="2f900-125">For datasets where the consumer can separately process each item, you should consider using a stream if it means that progress can be indicated to the user.</span></span> <span data-ttu-id="2f900-126">使用資料流程可以改善應用程式的回應能力，但您應該將它與應用程式的整體效能進行平衡。</span><span class="sxs-lookup"><span data-stu-id="2f900-126">Using a stream can improve the responsiveness of an application, but you should balance it against the overall performance of the application.</span></span>

<span data-ttu-id="2f900-127">資料流程可能很有用的另一種情況是在多個服務之間處理訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="2f900-127">Another scenario where streams can be useful is where a message is being processed across multiple services.</span></span> <span data-ttu-id="2f900-128">如果鏈中的每個服務傳回資料流程，則終端機服務（也就是鏈中的最後一個）可以開始傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="2f900-128">If each service in a chain returns a stream, then the terminal service (that is, the last one in the chain) can start returning messages.</span></span> <span data-ttu-id="2f900-129">這些訊息可以進行處理，並沿著鏈傳回給原始要求者。</span><span class="sxs-lookup"><span data-stu-id="2f900-129">These messages can be processed and passed back along the chain to the original requestor.</span></span> <span data-ttu-id="2f900-130">要求者可以傳回資料流程，或將結果匯總成單一回應訊息。</span><span class="sxs-lookup"><span data-stu-id="2f900-130">The requestor can either return a stream or aggregate the results into a single response message.</span></span> <span data-ttu-id="2f900-131">這種方法很適合用於 MapReduce 之類的模式。</span><span class="sxs-lookup"><span data-stu-id="2f900-131">This approach lends itself well to patterns like MapReduce.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f900-132">[上一頁](migrate-duplex-services.md)
>[下一頁](client-libraries.md)</span><span class="sxs-lookup"><span data-stu-id="2f900-132">[Previous](migrate-duplex-services.md)
[Next](client-libraries.md)</span></span>
