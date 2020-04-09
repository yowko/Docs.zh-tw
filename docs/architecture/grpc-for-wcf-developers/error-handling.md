---
title: 錯誤處理 - GRPC,適用於 WCF 開發人員
description: 與 gRPC 中的錯誤處理相關的主題。 包括最常用的狀態代碼的表。
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988943"
---
# <a name="error-handling"></a>錯誤處理

Windows 通訊基礎 (WCF) 使用<xref:System.ServiceModel.FaultException%601>和[故障合同](xref:System.ServiceModel.FaultContractAttribute)提供詳細的錯誤資訊,包括支援 SOAP 故障標準。

遺憾的是,gRPC 的當前版本缺乏 WCF 的成熟度,並且僅根據簡單的狀態代碼和元數據進行有限的內置錯誤處理。 下表是最常用的狀態代碼的快速指南:

| 狀態碼 | 問題 |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | 方法尚未編寫。 |
| `GRPC_STATUS_UNAVAILABLE` | 整個服務有問題。 |
| `GRPC_STATUS_UNKNOWN` | 無效回應。 |
| `GRPC_STATUS_INTERNAL` | 編碼/解碼問題。 |
| `GRPC_STATUS_UNAUTHENTICATED` | 驗證失敗。 |
| `GRPC_STATUS_PERMISSION_DENIED` | 授權失敗。 |
| `GRPC_STATUS_CANCELLED` | 呼叫已取消,通常由呼叫者取消。 |

## <a name="raise-errors-in-aspnet-core-grpc"></a>引發ASP.NET核心 gRPC 中的錯誤

ASP.NET Core gRPC 服務可以`RpcException`通過引發 一個 發送 錯誤回應來發送錯誤回應,用戶端可以捕獲該回應,就像它處於同一進程中一樣。 `RpcException`必須包括狀態代碼和說明,並且可以選擇包括元數據和較長的異常消息。 元數據可用於發送支援數據,類似於物件如何`FaultContract`為 WCF 錯誤攜帶其他數據。

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

## <a name="catch-errors-in-grpc-clients"></a>擷取 gRPC 用戶端的錯誤

就像 WCF<xref:System.ServiceModel.FaultException%601>用戶端可以捕獲錯誤一樣,gRPC 用戶端`RpcException`可以捕獲處理錯誤的。 因為`RpcException`不是泛型類型,因此無法捕獲不同塊中的不同錯誤類型。 但是,您可以使用 C# 的*例外篩選器*功能為不同的`catch`狀態代碼 聲明單獨的塊,如以下範例所示:

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
> 為錯誤提供其他元數據時,請確保在 API 文`.proto`檔中或 檔中的註釋中記錄相關鍵和值。

## <a name="grpc-richer-error-model"></a>gRPC 更豐富的錯誤模型

谷歌已經開發出一個更[豐富的錯誤模型](https://cloud.google.com/apis/design/errors#error_model),更像WCF的[故障合同](xref:System.ServiceModel.FaultContractAttribute),但這種模式在C#中還不受支援。 目前,它僅適用於 Go、JAva、Python 和C++。

>[!div class="step-by-step"]
>[前一個](metadata.md)
>[下一個](ws-protocols.md)
