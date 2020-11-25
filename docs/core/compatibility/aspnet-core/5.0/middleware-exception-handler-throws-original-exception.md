---
title: 重大變更：中介軟體：如果找不到處理程式，中介軟體會擲回原始例外狀況
description: 瞭解 ASP.NET Core 5.0 中標題為中介軟體的重大變更：例外狀況處理常式中介軟體擲回原始例外狀況（如果找不到處理程式）
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8801d3e6950d66fd9f24e051fd8729c50eb0b282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760770"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="b2487-103">中介軟體：如果找不到處理程式，中介軟體會擲回原始例外狀況</span><span class="sxs-lookup"><span data-stu-id="b2487-103">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="b2487-104">在 ASP.NET Core 5.0 之前， [例外狀況處理常式中介軟體](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) 會在發生例外狀況時，執行已設定的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="b2487-104">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="b2487-105">如果找不到透過設定的例外狀況處理常式， <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> 則會產生 HTTP 404 回應。</span><span class="sxs-lookup"><span data-stu-id="b2487-105">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="b2487-106">回應會誤導它：</span><span class="sxs-lookup"><span data-stu-id="b2487-106">The response is misleading in that it:</span></span>

* <span data-ttu-id="b2487-107">似乎是使用者錯誤。</span><span class="sxs-lookup"><span data-stu-id="b2487-107">Seems to be a user error.</span></span>
* <span data-ttu-id="b2487-108">模糊伺服器上發生例外狀況的事實。</span><span class="sxs-lookup"><span data-stu-id="b2487-108">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="b2487-109">為了解決 ASP.NET Core 5.0 中誤導的錯誤，如果找不到例外狀況處理常式，則會擲回 `ExceptionHandlerMiddleware` 原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b2487-109">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="b2487-110">因此，伺服器會產生 HTTP 500 回應。</span><span class="sxs-lookup"><span data-stu-id="b2487-110">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="b2487-111">當偵測到發生的錯誤時，回應將會比較容易在伺服器記錄檔中進行檢查。</span><span class="sxs-lookup"><span data-stu-id="b2487-111">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="b2487-112">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288)。</span><span class="sxs-lookup"><span data-stu-id="b2487-112">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b2487-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b2487-113">Version introduced</span></span>

<span data-ttu-id="b2487-114">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="b2487-114">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b2487-115">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b2487-115">Old behavior</span></span>

<span data-ttu-id="b2487-116">如果找不到設定的例外狀況處理常式，例外狀況處理常式中介軟體會產生 HTTP 404 回應。</span><span class="sxs-lookup"><span data-stu-id="b2487-116">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b2487-117">新的行為</span><span class="sxs-lookup"><span data-stu-id="b2487-117">New behavior</span></span>

<span data-ttu-id="b2487-118">如果找不到設定的例外狀況處理常式，例外狀況處理常式中介軟體會擲回原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b2487-118">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b2487-119">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b2487-119">Reason for change</span></span>

<span data-ttu-id="b2487-120">HTTP 404 錯誤無法明確指出伺服器上發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b2487-120">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="b2487-121">這種變更會產生 HTTP 500 錯誤，讓它顯而易見：</span><span class="sxs-lookup"><span data-stu-id="b2487-121">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="b2487-122">問題不是由使用者錯誤所造成。</span><span class="sxs-lookup"><span data-stu-id="b2487-122">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="b2487-123">在伺服器上發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b2487-123">An exception was encountered on the server.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b2487-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b2487-124">Recommended action</span></span>

<span data-ttu-id="b2487-125">沒有任何 API 變更。</span><span class="sxs-lookup"><span data-stu-id="b2487-125">There are no API changes.</span></span> <span data-ttu-id="b2487-126">所有現有的應用程式都會繼續編譯和執行。</span><span class="sxs-lookup"><span data-stu-id="b2487-126">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="b2487-127">擲回的例外狀況是由伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="b2487-127">The exception thrown is handled by the server.</span></span> <span data-ttu-id="b2487-128">例如，例外狀況會透過 [Kestrel](/aspnet/core/fundamentals/servers/kestrel) 或 [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)轉換成 HTTP 500 錯誤回應。</span><span class="sxs-lookup"><span data-stu-id="b2487-128">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b2487-129">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b2487-129">Affected APIs</span></span>

<span data-ttu-id="b2487-130">None</span><span class="sxs-lookup"><span data-stu-id="b2487-130">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
