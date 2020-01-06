---
title: 串流服務與重複的欄位-適用于 WCF 開發人員的 gRPC
description: 將重複的欄位與串流服務做比較，做為使用 gRPC 傳遞資料集合的方式。
ms.date: 09/02/2019
ms.openlocfilehash: 46586ab08df6b136cdafb990ce8be75435a6bf6c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337859"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a><span data-ttu-id="a0f46-103">gRPC 串流服務與重複的欄位</span><span class="sxs-lookup"><span data-stu-id="a0f46-103">gRPC streaming services versus repeated fields</span></span>

<span data-ttu-id="a0f46-104">gRPC services 提供兩種方法來傳回資料集或物件清單。</span><span class="sxs-lookup"><span data-stu-id="a0f46-104">gRPC services provide two ways of returning datasets, or lists of objects.</span></span> <span data-ttu-id="a0f46-105">通訊協定緩衝區訊息規格會使用 `repeated` 關鍵字，來宣告另一個訊息中的清單或訊息陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f46-105">The Protocol Buffers message specification uses the `repeated` keyword for declaring lists or arrays of messages within another message.</span></span> <span data-ttu-id="a0f46-106">GRPC 服務規格會使用 `stream` 關鍵字來宣告長時間執行的持續性連線，透過此連接會傳送多個訊息，並可個別處理。</span><span class="sxs-lookup"><span data-stu-id="a0f46-106">The gRPC service specification uses the `stream` keyword to declare a long-running persistent connection over which multiple messages are sent, and can be processed, individually.</span></span> <span data-ttu-id="a0f46-107">`stream` 功能也可以用於長時間執行的時態性資料（例如通知或記錄訊息），但本章會考慮使用它來傳回單一資料集。</span><span class="sxs-lookup"><span data-stu-id="a0f46-107">The `stream` feature can also be used for long-running temporal data such as notifications or log messages, but this chapter will consider its use for returning a single dataset.</span></span>

<span data-ttu-id="a0f46-108">您應該使用的取決於各種因素，例如資料集的整體大小、在用戶端或伺服器端建立資料集所花的時間，以及資料集的取用者是否可以在第一個專案可用時立即開始作用。，或需要完整的資料集來執行任何有用的工作。</span><span class="sxs-lookup"><span data-stu-id="a0f46-108">Which you should use depends on various factors, such as the overall size of the dataset, the time it took to create the dataset at either the client or server end, and whether the consumer of the dataset can start acting on it as soon as the first item is available, or needs the complete dataset to do anything useful.</span></span>

## <a name="when-to-use-repeated-fields"></a><span data-ttu-id="a0f46-109">使用 `repeated` 欄位的時機</span><span class="sxs-lookup"><span data-stu-id="a0f46-109">When to use `repeated` fields</span></span>

<span data-ttu-id="a0f46-110">對於大小限制，而且可以在短時間內完整產生的任何資料集（例如，在一秒內），您應該使用一般 Protobuf 訊息中的 `repeated` 欄位。</span><span class="sxs-lookup"><span data-stu-id="a0f46-110">For any dataset that is constrained in size and that can be generated in its entirety in a short time—say, under one second—you should use a `repeated` field in a regular Protobuf message.</span></span> <span data-ttu-id="a0f46-111">例如，在電子商務系統中，若要建立訂單中的專案清單可能很快，而且清單不會很大。</span><span class="sxs-lookup"><span data-stu-id="a0f46-111">For example, in an e-commerce system, to build a list of items within an order is probably quick and the list won't be very large.</span></span> <span data-ttu-id="a0f46-112">以 `repeated` 欄位傳回單一訊息的順序，比使用 `stream` 更快，而且會產生較少的網路額外負荷。</span><span class="sxs-lookup"><span data-stu-id="a0f46-112">Returning a single message with a `repeated` field is an order of magnitude faster than using a `stream` and incurs less network overhead.</span></span>

<span data-ttu-id="a0f46-113">如果用戶端在開始處理之前需要所有資料，而且資料集夠小，可在記憶體中建立，則即使在伺服器的記憶體中實際建立資料集的速度較慢，也請考慮使用 `repeated` 欄位。</span><span class="sxs-lookup"><span data-stu-id="a0f46-113">If the client needs all the data before starting to process it and the dataset is small enough to construct in memory, then consider using a `repeated` field even if the actual creation of the dataset in memory on the server is slower.</span></span>

## <a name="when-to-use-stream-methods"></a><span data-ttu-id="a0f46-114">使用 `stream` 方法的時機</span><span class="sxs-lookup"><span data-stu-id="a0f46-114">When to use `stream` methods</span></span>

<span data-ttu-id="a0f46-115">訊息物件可能非常大的資料集，最好使用串流要求或回應來傳輸。</span><span class="sxs-lookup"><span data-stu-id="a0f46-115">Datasets where the message objects are potentially very large are best transferred using streaming requests or responses.</span></span> <span data-ttu-id="a0f46-116">在記憶體中建立大型物件、將它寫入網路，然後釋放資源，會更有效率。</span><span class="sxs-lookup"><span data-stu-id="a0f46-116">It's more efficient to construct a large object in memory, write it to the network and then free up the resources.</span></span> <span data-ttu-id="a0f46-117">這種方法可以改善服務的擴充性。</span><span class="sxs-lookup"><span data-stu-id="a0f46-117">This approach will improve the scalability of your service.</span></span>

<span data-ttu-id="a0f46-118">同樣地，不受限制大小的資料集應該透過資料流程傳送，以避免在建立記憶體時用盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="a0f46-118">Similarly, datasets of unconstrained size should be sent over streams to avoid running out of memory while constructing them.</span></span>

<span data-ttu-id="a0f46-119">針對每個個別專案可由取用者分別進行處理的資料集，您應該考慮使用資料流程，如果這表示進度可以向使用者表示。</span><span class="sxs-lookup"><span data-stu-id="a0f46-119">For datasets where each individual item can be processed separately by the consumer, you should consider using a stream if it means that progress can be indicated to the end user.</span></span> <span data-ttu-id="a0f46-120">這可能會改善應用程式的明顯回應性，但這應該平衡應用程式的整體效能。</span><span class="sxs-lookup"><span data-stu-id="a0f46-120">This could improve the apparent responsiveness of an application, although this should be balanced against the overall performance of the application.</span></span>

<span data-ttu-id="a0f46-121">資料流程可能很有用的另一種情況是在多個服務之間處理訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="a0f46-121">Another scenario where streams can be useful is where a message is being processed across multiple services.</span></span> <span data-ttu-id="a0f46-122">如果鏈中的每個服務傳回資料流程，則終端機服務（也就是鏈中的最後一個）可以開始傳回可處理的訊息，並將鏈傳回給原始要求者，這可能會傳回資料流程或匯總產生單一回應訊息。</span><span class="sxs-lookup"><span data-stu-id="a0f46-122">If each service in a chain returns a stream, then the terminal service (that is, the last one in the chain) can start returning messages that can be processed and passed back along the chain to the original requestor, which can either return a stream or aggregate the results into a single response message.</span></span> <span data-ttu-id="a0f46-123">這種方法非常適合對應/減少之類的模式。</span><span class="sxs-lookup"><span data-stu-id="a0f46-123">This approach lends itself well to patterns like Map/Reduce.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a0f46-124">[上一頁](migrate-duplex-services.md)
>[下一頁](client-libraries.md)</span><span class="sxs-lookup"><span data-stu-id="a0f46-124">[Previous](migrate-duplex-services.md)
[Next](client-libraries.md)</span></span>
