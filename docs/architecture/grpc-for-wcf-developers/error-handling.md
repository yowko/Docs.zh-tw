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
# <a name="error-handling"></a><span data-ttu-id="2608d-104">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="2608d-104">Error handling</span></span>

<span data-ttu-id="2608d-105">Windows 通訊基礎 (WCF) 使用<xref:System.ServiceModel.FaultException%601>和[故障合同](xref:System.ServiceModel.FaultContractAttribute)提供詳細的錯誤資訊,包括支援 SOAP 故障標準。</span><span class="sxs-lookup"><span data-stu-id="2608d-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="2608d-106">遺憾的是,gRPC 的當前版本缺乏 WCF 的成熟度,並且僅根據簡單的狀態代碼和元數據進行有限的內置錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="2608d-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="2608d-107">下表是最常用的狀態代碼的快速指南:</span><span class="sxs-lookup"><span data-stu-id="2608d-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="2608d-108">狀態碼</span><span class="sxs-lookup"><span data-stu-id="2608d-108">Status code</span></span> | <span data-ttu-id="2608d-109">問題</span><span class="sxs-lookup"><span data-stu-id="2608d-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="2608d-110">方法尚未編寫。</span><span class="sxs-lookup"><span data-stu-id="2608d-110">Method hasn't been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="2608d-111">整個服務有問題。</span><span class="sxs-lookup"><span data-stu-id="2608d-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="2608d-112">無效回應。</span><span class="sxs-lookup"><span data-stu-id="2608d-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="2608d-113">編碼/解碼問題。</span><span class="sxs-lookup"><span data-stu-id="2608d-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="2608d-114">驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="2608d-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="2608d-115">授權失敗。</span><span class="sxs-lookup"><span data-stu-id="2608d-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="2608d-116">呼叫已取消,通常由呼叫者取消。</span><span class="sxs-lookup"><span data-stu-id="2608d-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="2608d-117">引發ASP.NET核心 gRPC 中的錯誤</span><span class="sxs-lookup"><span data-stu-id="2608d-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="2608d-118">ASP.NET Core gRPC 服務可以`RpcException`通過引發 一個 發送 錯誤回應來發送錯誤回應,用戶端可以捕獲該回應,就像它處於同一進程中一樣。</span><span class="sxs-lookup"><span data-stu-id="2608d-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="2608d-119">`RpcException`必須包括狀態代碼和說明,並且可以選擇包括元數據和較長的異常消息。</span><span class="sxs-lookup"><span data-stu-id="2608d-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="2608d-120">元數據可用於發送支援數據,類似於物件如何`FaultContract`為 WCF 錯誤攜帶其他數據。</span><span class="sxs-lookup"><span data-stu-id="2608d-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="2608d-121">擷取 gRPC 用戶端的錯誤</span><span class="sxs-lookup"><span data-stu-id="2608d-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="2608d-122">就像 WCF<xref:System.ServiceModel.FaultException%601>用戶端可以捕獲錯誤一樣,gRPC 用戶端`RpcException`可以捕獲處理錯誤的。</span><span class="sxs-lookup"><span data-stu-id="2608d-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="2608d-123">因為`RpcException`不是泛型類型,因此無法捕獲不同塊中的不同錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="2608d-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="2608d-124">但是,您可以使用 C# 的*例外篩選器*功能為不同的`catch`狀態代碼 聲明單獨的塊,如以下範例所示:</span><span class="sxs-lookup"><span data-stu-id="2608d-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="2608d-125">為錯誤提供其他元數據時,請確保在 API 文`.proto`檔中或 檔中的註釋中記錄相關鍵和值。</span><span class="sxs-lookup"><span data-stu-id="2608d-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="2608d-126">gRPC 更豐富的錯誤模型</span><span class="sxs-lookup"><span data-stu-id="2608d-126">gRPC richer error model</span></span>

<span data-ttu-id="2608d-127">谷歌已經開發出一個更[豐富的錯誤模型](https://cloud.google.com/apis/design/errors#error_model),更像WCF的[故障合同](xref:System.ServiceModel.FaultContractAttribute),但這種模式在C#中還不受支援。</span><span class="sxs-lookup"><span data-stu-id="2608d-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="2608d-128">目前,它僅適用於 Go、JAva、Python 和C++。</span><span class="sxs-lookup"><span data-stu-id="2608d-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2608d-129">[前一個](metadata.md)
>[下一個](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="2608d-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
