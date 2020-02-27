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
# <a name="metadata"></a>中繼資料

*中繼資料*是指在處理要求和回應期間可能有用，但不屬於實際應用程式資料的其他資料。 中繼資料可能包含驗證權杖、要求識別碼和標記以供監視之用，以及資料的相關資訊，例如 dataset 中的記錄數目。

您可以使用 <xref:System.ServiceModel.OperationContextScope> 和 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> 屬性，將泛型索引鍵/值標頭加入 Windows Communication Foundation （WCF）訊息中，然後使用 <xref:System.ServiceModel.Channels.MessageProperties>來處理它們。

gRPC 呼叫和回應也可以包含類似 HTTP 標頭的中繼資料。 此中繼資料主要不會 gRPC 本身，並會傳遞給您的應用程式代碼或中介軟體進行處理。 中繼資料會以索引鍵/值組表示，其中索引鍵為字串，而值為字串或二進位資料。 您不需要指定 `.proto` 檔案中的中繼資料。

中繼資料是由[Grpc](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet 套件的 `Metadata` 類別所處理。 這個類別可以與集合初始化運算式語法搭配使用。

這個範例示範如何將中繼資料新增至C#用戶端的呼叫：

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

gRPC 服務可以從 `ServerCallContext` 引數的 `RequestHeaders` 屬性存取中繼資料：

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

服務可以使用 `ServerCallContext`的 `ResponseTrailers` 屬性，將中繼資料傳送給用戶端：

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
