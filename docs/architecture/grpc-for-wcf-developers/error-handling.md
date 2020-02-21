---
title: 錯誤處理-WCF 開發人員的 gRPC
description: GRPC 中錯誤處理的相關主題。 包含最常使用之狀態碼的表格。
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542789"
---
# <a name="error-handling"></a><span data-ttu-id="7d084-104">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="7d084-104">Error handling</span></span>

<span data-ttu-id="7d084-105">Windows Communication Foundation （WCF）會使用 <xref:System.ServiceModel.FaultException%601> 和[FaultContract](xref:System.ServiceModel.FaultContractAttribute)來提供詳細的錯誤資訊，包括支援 SOAP 錯誤標準。</span><span class="sxs-lookup"><span data-stu-id="7d084-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="7d084-106">可惜的是，目前版本的 gRPC 缺少 WCF 所發現的複雜，而且只有根據簡單狀態碼和中繼資料的內建錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="7d084-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="7d084-107">下表是最常使用的狀態碼快速指南：</span><span class="sxs-lookup"><span data-stu-id="7d084-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="7d084-108">狀態碼</span><span class="sxs-lookup"><span data-stu-id="7d084-108">Status code</span></span> | <span data-ttu-id="7d084-109">問題</span><span class="sxs-lookup"><span data-stu-id="7d084-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="7d084-110">尚未撰寫方法。</span><span class="sxs-lookup"><span data-stu-id="7d084-110">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="7d084-111">整個服務的問題。</span><span class="sxs-lookup"><span data-stu-id="7d084-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="7d084-112">不正確回應。</span><span class="sxs-lookup"><span data-stu-id="7d084-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="7d084-113">編碼/解碼的問題。</span><span class="sxs-lookup"><span data-stu-id="7d084-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="7d084-114">驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="7d084-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="7d084-115">授權失敗。</span><span class="sxs-lookup"><span data-stu-id="7d084-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="7d084-116">呼叫已取消，通常是由呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7d084-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="7d084-117">在 ASP.NET Core gRPC 中引發錯誤</span><span class="sxs-lookup"><span data-stu-id="7d084-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="7d084-118">ASP.NET Core gRPC 服務可以藉由擲回 `RpcException`來傳送錯誤回應，而用戶端可以攔截此訊息，如同在同一個進程中。</span><span class="sxs-lookup"><span data-stu-id="7d084-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="7d084-119">`RpcException` 必須包含狀態碼和描述，而且可以選擇性地包含中繼資料和較長的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="7d084-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="7d084-120">中繼資料可用來傳送支援的資料，類似于 `FaultContract` 物件如何針對 WCF 錯誤執行額外的資料。</span><span class="sxs-lookup"><span data-stu-id="7d084-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="7d084-121">GRPC 用戶端中的攔截錯誤</span><span class="sxs-lookup"><span data-stu-id="7d084-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="7d084-122">就像 WCF 用戶端可以攔截 <xref:System.ServiceModel.FaultException%601> 錯誤，gRPC 用戶端可以攔截 `RpcException` 來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d084-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="7d084-123">因為 `RpcException` 不是泛型型別，所以您無法在不同的區塊中攔截不同的錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="7d084-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="7d084-124">但是，您可以C#使用的*例外狀況篩選*功能，針對不同的狀態碼宣告個別的 `catch` 區塊，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7d084-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="7d084-125">當您提供錯誤的其他中繼資料時，請務必記錄 API 檔中的相關索引鍵和值，或 `.proto` 檔案中的批註。</span><span class="sxs-lookup"><span data-stu-id="7d084-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="7d084-126">gRPC 更豐富的錯誤模型</span><span class="sxs-lookup"><span data-stu-id="7d084-126">gRPC richer error model</span></span>

<span data-ttu-id="7d084-127">Google 開發出更[豐富的錯誤模型](https://cloud.google.com/apis/design/errors#error_model)，更像 WCF 的[FaultContract](xref:System.ServiceModel.FaultContractAttribute)，但C#尚不支援此模型。</span><span class="sxs-lookup"><span data-stu-id="7d084-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="7d084-128">目前僅適用于 Go、JAVA、Python 和C++。</span><span class="sxs-lookup"><span data-stu-id="7d084-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7d084-129">[上一頁](metadata.md)
>[下一頁](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="7d084-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
