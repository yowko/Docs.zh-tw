---
title: WCF 開發人員的中繼資料 gRPC
description: 如何在 gRPC 中使用中繼資料來傳遞用戶端和伺服器之間的其他內容。
ms.date: 09/02/2019
ms.openlocfilehash: 64fa94d1e63af480cbc7363631de161c5b8b8fb8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628575"
---
# <a name="metadata"></a><span data-ttu-id="42f6b-103">中繼資料</span><span class="sxs-lookup"><span data-stu-id="42f6b-103">Metadata</span></span>

<span data-ttu-id="42f6b-104">*中繼資料*是指在處理要求和回應期間可能有用，但不屬於實際應用程式資料的其他資料。</span><span class="sxs-lookup"><span data-stu-id="42f6b-104">*Metadata* refers to additional data that might be useful during the processing of requests and responses but that’s not part of the actual application data.</span></span> <span data-ttu-id="42f6b-105">中繼資料可能包含驗證權杖、要求識別碼和標記以供監視之用，以及資料的相關資訊，例如 dataset 中的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="42f6b-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, and information about the data, like the number of records in a dataset.</span></span>

<span data-ttu-id="42f6b-106">您可以使用 <xref:System.ServiceModel.OperationContextScope> 和 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> 屬性，將泛型索引鍵/值標頭加入 Windows Communication Foundation （WCF）訊息中，然後使用 <xref:System.ServiceModel.Channels.MessageProperties>來處理它們。</span><span class="sxs-lookup"><span data-stu-id="42f6b-106">It's possible to add generic key/value headers to Windows Communication Foundation (WCF) messages by using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property and handle them by using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="42f6b-107">gRPC 呼叫和回應也可以包含類似 HTTP 標頭的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="42f6b-107">gRPC calls and responses can also include metadata that's similar to HTTP headers.</span></span> <span data-ttu-id="42f6b-108">此中繼資料主要不會 gRPC 本身，並會傳遞給您的應用程式代碼或中介軟體進行處理。</span><span class="sxs-lookup"><span data-stu-id="42f6b-108">This metadata is mostly invisible to gRPC itself and is passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="42f6b-109">中繼資料會以索引鍵/值組表示，其中索引鍵為字串，而值為字串或二進位資料。</span><span class="sxs-lookup"><span data-stu-id="42f6b-109">Metadata is represented as key/value pairs, where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="42f6b-110">您不需要指定 `.proto` 檔案中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="42f6b-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="42f6b-111">中繼資料是由[Grpc](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet 套件的 `Metadata` 類別所處理。</span><span class="sxs-lookup"><span data-stu-id="42f6b-111">Metadata is handled by the `Metadata` class of the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="42f6b-112">這個類別可以與集合初始化運算式語法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="42f6b-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="42f6b-113">這個範例示範如何將中繼資料新增至C#用戶端的呼叫：</span><span class="sxs-lookup"><span data-stu-id="42f6b-113">This example shows how to add metadata to a call from a C# client:</span></span>

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

<span data-ttu-id="42f6b-114">gRPC 服務可以從 `ServerCallContext` 引數的 `RequestHeaders` 屬性存取中繼資料：</span><span class="sxs-lookup"><span data-stu-id="42f6b-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

<span data-ttu-id="42f6b-115">服務可以使用 `ServerCallContext`的 `ResponseTrailers` 屬性，將中繼資料傳送給用戶端：</span><span class="sxs-lookup"><span data-stu-id="42f6b-115">Services can send metadata to clients by using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="42f6b-116">[上一頁](rpc-types.md)
>[下一頁](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="42f6b-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
