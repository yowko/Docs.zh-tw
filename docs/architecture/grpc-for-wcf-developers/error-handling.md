---
title: 錯誤處理-WCF 開發人員的 gRPC
description: 要寫入的
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3535a00aad49f532eb5f5f778116454a12bfd639
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184453"
---
# <a name="error-handling"></a><span data-ttu-id="093a4-103">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="093a4-103">Error handling</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="093a4-104">WCF 會`FaultException<T>`使用`FaultContract`和來提供詳細的錯誤資訊，包括支援 SOAP 錯誤標準。</span><span class="sxs-lookup"><span data-stu-id="093a4-104">WCF uses `FaultException<T>` and `FaultContract` to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="093a4-105">可惜的是，目前版本的 gRPC 缺少 WCF 所發現的複雜，而且只有以簡單狀態碼和中繼資料為基礎的內建錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="093a4-105">Unfortunately, the current version of gRPC lacks the sophistication found with WCF and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="093a4-106">下表是最常使用的狀態碼快速指南：</span><span class="sxs-lookup"><span data-stu-id="093a4-106">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="093a4-107">狀態碼</span><span class="sxs-lookup"><span data-stu-id="093a4-107">Status Code</span></span> | <span data-ttu-id="093a4-108">問題</span><span class="sxs-lookup"><span data-stu-id="093a4-108">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="093a4-109">尚未撰寫方法。</span><span class="sxs-lookup"><span data-stu-id="093a4-109">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="093a4-110">整個服務的問題。</span><span class="sxs-lookup"><span data-stu-id="093a4-110">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="093a4-111">不正確回應。</span><span class="sxs-lookup"><span data-stu-id="093a4-111">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="093a4-112">編碼/解碼的問題。</span><span class="sxs-lookup"><span data-stu-id="093a4-112">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="093a4-113">驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="093a4-113">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="093a4-114">授權失敗。</span><span class="sxs-lookup"><span data-stu-id="093a4-114">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="093a4-115">呼叫已取消，通常是由呼叫端。</span><span class="sxs-lookup"><span data-stu-id="093a4-115">Call was canceled, usually by the caller.</span></span> |

## <a name="raising-errors-in-aspnet-core-grpc"></a><span data-ttu-id="093a4-116">在 ASP.NET Core gRPC 中引發錯誤</span><span class="sxs-lookup"><span data-stu-id="093a4-116">Raising errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="093a4-117">ASP.NET Core gRPC 服務可以藉由`RpcException`擲回來傳送錯誤回應，而用戶端可以攔截此訊息，如同在同一個進程中。</span><span class="sxs-lookup"><span data-stu-id="093a4-117">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="093a4-118">`RpcException`必須包含狀態碼和描述，而且可以選擇性地包含中繼資料和較長的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="093a4-118">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="093a4-119">中繼資料可用來傳送支援的資料，類似于物件如何`FaultContract`針對 WCF 錯誤包含額外的資料。</span><span class="sxs-lookup"><span data-stu-id="093a4-119">The metadata can be used to send supporting data, similar to how `FaultContract` objects could carry additional data for WCF errors.</span></span>

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

## <a name="catching-errors-in-grpc-clients"></a><span data-ttu-id="093a4-120">攔截 gRPC 用戶端中的錯誤</span><span class="sxs-lookup"><span data-stu-id="093a4-120">Catching errors in gRPC clients</span></span>

<span data-ttu-id="093a4-121">就像 WCF 用戶端可以<xref:System.ServiceModel.FaultException%601>攔截錯誤，gRPC 用戶端可以`RpcException`攔截來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="093a4-121">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="093a4-122">因為`RpcException`不是泛型型別，所以您無法在不同的區塊中攔截不同的錯誤類型C#，但是您可以使用的例外`catch`狀況*篩選*功能，針對不同的狀態碼宣告個別的區塊，如下所示：實例</span><span class="sxs-lookup"><span data-stu-id="093a4-122">Since `RpcException` isn't a generic type, you can't catch different error types in different blocks, but you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="093a4-123">當您提供錯誤的其他中繼資料時，請務必記錄 API 檔中的相關金鑰和值，或`.proto`檔中的批註。</span><span class="sxs-lookup"><span data-stu-id="093a4-123">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="093a4-124">gRPC 更豐富的錯誤模型</span><span class="sxs-lookup"><span data-stu-id="093a4-124">gRPC Richer Error Model</span></span>

<span data-ttu-id="093a4-125">在C#未來，Google 已開發出更[豐富的錯誤模型](https://cloud.google.com/apis/design/errors#error_model)，更像 WCF 的[FaultContract](xref:System.ServiceModel.FaultContractAttribute)，但尚不支援。</span><span class="sxs-lookup"><span data-stu-id="093a4-125">Looking ahead, Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that is more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but isn't supported in C# yet.</span></span> <span data-ttu-id="093a4-126">目前僅適用于 Go、JAVA、Python 和C++，但的C#支援預計會在下一年推出。</span><span class="sxs-lookup"><span data-stu-id="093a4-126">Currently, it's only available for Go, Java, Python and C++, but support for C# is expected to come next year.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="093a4-127">[上一頁](metadata.md)
>[下一頁](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="093a4-127">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
