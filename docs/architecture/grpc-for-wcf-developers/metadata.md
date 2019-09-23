---
title: WCF 開發人員的中繼資料 gRPC
description: 如何在 gRPC 中使用中繼資料來傳遞用戶端與伺服器之間的其他內容
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1a2131fa3ee3112eaa3c3e7f7c97017fea6b1004
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184327"
---
# <a name="metadata"></a>中繼資料

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

「中繼資料」指的是處理要求和回應時可能有用的其他資料，但不屬於實際的應用程式資料。 中繼資料可能包含驗證權杖、要求識別碼和標記以供監視之用，或是資料集內的記錄數目等相關資訊。

您可以使用<xref:System.ServiceModel.OperationContextScope> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType>和屬性，將泛型索引鍵/值標頭新增至 WCF 訊息，並使用<xref:System.ServiceModel.Channels.MessageProperties>來處理它們。

gRPC 呼叫和回應也可以包含類似 HTTP 標頭的中繼資料。 這些主要不是 gRPC 本身，而且會傳遞給您的應用程式代碼或中介軟體來處理。 中繼資料會以索引鍵/值組表示，其中的索引鍵為字串，而值為字串或二進位資料。 您不需要指定檔案中的`.proto`中繼資料。

中繼資料的處理方式`Metadata`是使用[Grpc](https://www.nuget.org/packages/Grpc.Core/) NuGet 套件中的類別。 這個類別可以與集合初始化運算式語法搭配使用。

下列範例顯示如何將中繼資料新增至C#用戶端的呼叫：

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

gRPC 服務可以從`ServerCallContext`引數的`RequestHeaders`屬性存取中繼資料：

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

服務可以使用`ResponseTrailers`的`ServerCallContext`屬性，將中繼資料傳送給用戶端：

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[上一頁](rpc-types.md)
>[下一頁](error-handling.md)
