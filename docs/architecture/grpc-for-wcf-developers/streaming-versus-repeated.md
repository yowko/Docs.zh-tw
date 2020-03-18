---
title: 流服務與重複欄位 - gRPC 面向 WCF 開發人員
description: 將重複欄位與流服務進行比較，作為使用 gRPC 傳遞資料集合的方法。
ms.date: 09/02/2019
ms.openlocfilehash: 542ebc393f9c9c1ad717d02d01fab33d85c18917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147746"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a><span data-ttu-id="f1292-103">gRPC 串流服務與重複欄位的比較</span><span class="sxs-lookup"><span data-stu-id="f1292-103">gRPC streaming services vs. repeated fields</span></span>

<span data-ttu-id="f1292-104">gRPC 服務提供兩種返回資料集或物件清單的方法。</span><span class="sxs-lookup"><span data-stu-id="f1292-104">gRPC services provide two ways of returning datasets, or lists of objects.</span></span> <span data-ttu-id="f1292-105">協定緩衝區消息規範使用 關鍵字`repeated`聲明另一消息中的消息清單或陣列。</span><span class="sxs-lookup"><span data-stu-id="f1292-105">The Protocol Buffers message specification uses the `repeated` keyword for declaring lists or arrays of messages within another message.</span></span> <span data-ttu-id="f1292-106">gRPC 服務規範使用`stream`關鍵字聲明長時間運行的持久連接。</span><span class="sxs-lookup"><span data-stu-id="f1292-106">The gRPC service specification uses the `stream` keyword to declare a long-running persistent connection.</span></span> <span data-ttu-id="f1292-107">通過該連接，將發送多條消息，並可以單獨處理。</span><span class="sxs-lookup"><span data-stu-id="f1292-107">Over that connection, multiple messages are sent, and can be processed, individually.</span></span>

<span data-ttu-id="f1292-108">您還可以使用該`stream`功能對長時間運行的時間資料（如通知或日誌消息）使用。</span><span class="sxs-lookup"><span data-stu-id="f1292-108">You can also use the `stream` feature for long-running temporal data such as notifications or log messages.</span></span> <span data-ttu-id="f1292-109">但本章將考慮用於返回單個資料集。</span><span class="sxs-lookup"><span data-stu-id="f1292-109">But this chapter will consider its use for returning a single dataset.</span></span>

<span data-ttu-id="f1292-110">您應該使用哪些取決於如下因素：</span><span class="sxs-lookup"><span data-stu-id="f1292-110">Which you should use depends on factors such as:</span></span>

- <span data-ttu-id="f1292-111">資料集的總體大小。</span><span class="sxs-lookup"><span data-stu-id="f1292-111">The overall size of the dataset.</span></span>
- <span data-ttu-id="f1292-112">在用戶端或伺服器端創建資料集所花的時間。</span><span class="sxs-lookup"><span data-stu-id="f1292-112">The time it took to create the dataset at either the client or server end.</span></span>
- <span data-ttu-id="f1292-113">資料集的消費者是否可以在第一個專案可用時立即開始對它進行操作，或者需要完整的資料集執行任何有用的操作。</span><span class="sxs-lookup"><span data-stu-id="f1292-113">Whether the consumer of the dataset can start acting on it as soon as the first item is available, or needs the complete dataset to do anything useful.</span></span>

## <a name="when-to-use-repeated-fields"></a><span data-ttu-id="f1292-114">何時使用`repeated`欄位</span><span class="sxs-lookup"><span data-stu-id="f1292-114">When to use `repeated` fields</span></span>

<span data-ttu-id="f1292-115">對於大小受限且可以在短時間內生成完整資料集的任何資料集（例如，在一秒以下），應在常規 Protobuf 消息中使用`repeated`欄位。</span><span class="sxs-lookup"><span data-stu-id="f1292-115">For any dataset that's constrained in size and that can be generated in its entirety in a short time—say, under one second—you should use a `repeated` field in a regular Protobuf message.</span></span> <span data-ttu-id="f1292-116">例如，在電子商務系統中，在訂單中生成專案清單可能很快，並且清單不會很大。</span><span class="sxs-lookup"><span data-stu-id="f1292-116">For example, in an e-commerce system, to build a list of items within an order is probably quick and the list won't be very large.</span></span> <span data-ttu-id="f1292-117">使用`repeated`欄位返回單個消息比使用`stream`快一個數量級，並且產生的網路開銷更少。</span><span class="sxs-lookup"><span data-stu-id="f1292-117">Returning a single message with a `repeated` field is an order of magnitude faster than using `stream` and incurs less network overhead.</span></span>

<span data-ttu-id="f1292-118">如果用戶端在開始處理之前需要所有資料，並且資料集足夠小，足以在記憶體中構造，則請考慮使用欄位`repeated`。</span><span class="sxs-lookup"><span data-stu-id="f1292-118">If the client needs all the data before starting to process it and the dataset is small enough to construct in memory, then consider using a `repeated` field.</span></span> <span data-ttu-id="f1292-119">即使伺服器上的記憶體中資料集的創建速度較慢，也請考慮它。</span><span class="sxs-lookup"><span data-stu-id="f1292-119">Consider it even if the creation of the dataset in memory on the server is slower.</span></span>

## <a name="when-to-use-stream-methods"></a><span data-ttu-id="f1292-120">何時使用`stream`方法</span><span class="sxs-lookup"><span data-stu-id="f1292-120">When to use `stream` methods</span></span>

<span data-ttu-id="f1292-121">當資料集中的消息物件可能非常大時，最好使用流式處理請求或回應來傳輸它們。</span><span class="sxs-lookup"><span data-stu-id="f1292-121">When the message objects in your datasets are potentially very large, it's best for you transfer them by using streaming requests or responses.</span></span> <span data-ttu-id="f1292-122">在記憶體中構造大型物件、將其寫入網路，然後釋放資源會更有效。</span><span class="sxs-lookup"><span data-stu-id="f1292-122">It's more efficient to construct a large object in memory, write it to the network, and then free up the resources.</span></span> <span data-ttu-id="f1292-123">此方法將提高服務的可擴充性。</span><span class="sxs-lookup"><span data-stu-id="f1292-123">This approach will improve the scalability of your service.</span></span>

<span data-ttu-id="f1292-124">同樣，您應該在流上發送無約束大小的資料集，以避免在構造時記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="f1292-124">Similarly, you should send datasets of unconstrained size over streams to avoid running out of memory while constructing them.</span></span>

<span data-ttu-id="f1292-125">對於消費者可以單獨處理每個專案的資料集，如果意味著可以向使用者指示進度，則應考慮使用流。</span><span class="sxs-lookup"><span data-stu-id="f1292-125">For datasets where the consumer can separately process each item, you should consider using a stream if it means that progress can be indicated to the user.</span></span> <span data-ttu-id="f1292-126">使用流可以提高應用程式的回應能力，但應平衡它與應用程式的整體性能。</span><span class="sxs-lookup"><span data-stu-id="f1292-126">Using a stream can improve the responsiveness of an application, but you should balance it against the overall performance of the application.</span></span>

<span data-ttu-id="f1292-127">流可能有用的另一個方案是跨多個服務處理消息。</span><span class="sxs-lookup"><span data-stu-id="f1292-127">Another scenario where streams can be useful is where a message is being processed across multiple services.</span></span> <span data-ttu-id="f1292-128">如果鏈中的每個服務返回一個流，則終端服務（即鏈中的最後一個服務）可以開始返回消息。</span><span class="sxs-lookup"><span data-stu-id="f1292-128">If each service in a chain returns a stream, then the terminal service (that is, the last one in the chain) can start returning messages.</span></span> <span data-ttu-id="f1292-129">這些消息可以處理，並沿鏈傳回原始要求者。</span><span class="sxs-lookup"><span data-stu-id="f1292-129">These messages can be processed and passed back along the chain to the original requestor.</span></span> <span data-ttu-id="f1292-130">要求者可以返回流或將結果聚合到單個回應訊息中。</span><span class="sxs-lookup"><span data-stu-id="f1292-130">The requestor can either return a stream or aggregate the results into a single response message.</span></span> <span data-ttu-id="f1292-131">此方法非常適合像 MapReduce 這樣的模式。</span><span class="sxs-lookup"><span data-stu-id="f1292-131">This approach lends itself well to patterns like MapReduce.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f1292-132">[上一個](migrate-duplex-services.md)
>[下一個](client-libraries.md)</span><span class="sxs-lookup"><span data-stu-id="f1292-132">[Previous](migrate-duplex-services.md)
[Next](client-libraries.md)</span></span>
