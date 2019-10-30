---
title: 錯誤處理-WCF 開發人員的 gRPC
description: 要寫入的
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 91f5789d8ed0f01f3ce2f3f9a6c6ccf14f245290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094227"
---
# <a name="error-handling"></a>錯誤處理

WCF 會使用 `FaultException<T>` 和 `FaultContract` 來提供詳細的錯誤資訊，包括支援 SOAP 錯誤標準。

可惜的是，目前版本的 gRPC 缺少 WCF 所發現的複雜，而且只有以簡單狀態碼和中繼資料為基礎的內建錯誤處理。 下表是最常使用的狀態碼快速指南：

| 狀態碼 | 問題 |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | 尚未撰寫方法。 |
| `GRPC_STATUS_UNAVAILABLE` | 整個服務的問題。 |
| `GRPC_STATUS_UNKNOWN` | 不正確回應。 |
| `GRPC_STATUS_INTERNAL` | 編碼/解碼的問題。 |
| `GRPC_STATUS_UNAUTHENTICATED` | 驗證失敗。 |
| `GRPC_STATUS_PERMISSION_DENIED` | 授權失敗。 |
| `GRPC_STATUS_CANCELLED` | 呼叫已取消，通常是由呼叫端。 |

## <a name="raising-errors-in-aspnet-core-grpc"></a>在 ASP.NET Core gRPC 中引發錯誤

ASP.NET Core gRPC 服務可以藉由擲回 `RpcException`來傳送錯誤回應，而用戶端可以攔截此訊息，如同在同一個進程中。 `RpcException` 必須包含狀態碼和描述，而且可以選擇性地包含中繼資料和較長的例外狀況訊息。 中繼資料可用來傳送支援的資料，類似于 `FaultContract` 物件如何針對 WCF 錯誤執行額外的資料。

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catching-errors-in-grpc-clients"></a>攔截 gRPC 用戶端中的錯誤

就像 WCF 用戶端可以攔截 <xref:System.ServiceModel.FaultException%601> 錯誤，gRPC 用戶端可以攔截 `RpcException` 來處理錯誤。 因為 `RpcException` 不是泛型型別，所以您無法在不同的區塊中攔截不同的錯誤類型C#，但是您可以使用的*例外狀況篩選*功能，針對不同的狀態碼宣告個別的`catch`區塊，如下列範例所示：

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> 當您提供錯誤的其他中繼資料時，請務必記錄 API 檔中的相關索引鍵和值，或 `.proto` 檔案中的批註。

## <a name="grpc-richer-error-model"></a>gRPC 更豐富的錯誤模型

在C#未來，Google 已開發出更[豐富的錯誤模型](https://cloud.google.com/apis/design/errors#error_model)，更像 WCF 的[FaultContract](xref:System.ServiceModel.FaultContractAttribute)，但尚不支援。 目前僅適用于 Go、JAVA、Python 和C++，但的C#支援預計會在下一年推出。

>[!div class="step-by-step"]
>[上一頁](metadata.md)
>[下一頁](ws-protocols.md)
