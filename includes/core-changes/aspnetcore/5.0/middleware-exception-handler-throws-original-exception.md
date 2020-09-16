---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022959"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="50396-101">中介軟體：如果找不到處理程式，中介軟體會擲回原始例外狀況</span><span class="sxs-lookup"><span data-stu-id="50396-101">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="50396-102">在 ASP.NET Core 5.0 之前， [例外狀況處理常式中介軟體](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) 會在發生例外狀況時，執行已設定的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="50396-102">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="50396-103">如果找不到透過設定的例外狀況處理常式， <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> 則會產生 HTTP 404 回應。</span><span class="sxs-lookup"><span data-stu-id="50396-103">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="50396-104">回應會誤導它：</span><span class="sxs-lookup"><span data-stu-id="50396-104">The response is misleading in that it:</span></span>

* <span data-ttu-id="50396-105">似乎是使用者錯誤。</span><span class="sxs-lookup"><span data-stu-id="50396-105">Seems to be a user error.</span></span>
* <span data-ttu-id="50396-106">模糊伺服器上發生例外狀況的事實。</span><span class="sxs-lookup"><span data-stu-id="50396-106">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="50396-107">為了解決 ASP.NET Core 5.0 中誤導的錯誤，如果找不到例外狀況處理常式，則會擲回 `ExceptionHandlerMiddleware` 原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50396-107">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="50396-108">因此，伺服器會產生 HTTP 500 回應。</span><span class="sxs-lookup"><span data-stu-id="50396-108">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="50396-109">當偵測到發生的錯誤時，回應將會比較容易在伺服器記錄檔中進行檢查。</span><span class="sxs-lookup"><span data-stu-id="50396-109">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="50396-110">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288)。</span><span class="sxs-lookup"><span data-stu-id="50396-110">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="50396-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="50396-111">Version introduced</span></span>

<span data-ttu-id="50396-112">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="50396-112">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="50396-113">舊的行為</span><span class="sxs-lookup"><span data-stu-id="50396-113">Old behavior</span></span>

<span data-ttu-id="50396-114">如果找不到設定的例外狀況處理常式，例外狀況處理常式中介軟體會產生 HTTP 404 回應。</span><span class="sxs-lookup"><span data-stu-id="50396-114">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="50396-115">新的行為</span><span class="sxs-lookup"><span data-stu-id="50396-115">New behavior</span></span>

<span data-ttu-id="50396-116">如果找不到設定的例外狀況處理常式，例外狀況處理常式中介軟體會擲回原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50396-116">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="50396-117">變更的原因</span><span class="sxs-lookup"><span data-stu-id="50396-117">Reason for change</span></span>

<span data-ttu-id="50396-118">HTTP 404 錯誤無法明確指出伺服器上發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50396-118">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="50396-119">這種變更會產生 HTTP 500 錯誤，讓它顯而易見：</span><span class="sxs-lookup"><span data-stu-id="50396-119">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="50396-120">問題不是由使用者錯誤所造成。</span><span class="sxs-lookup"><span data-stu-id="50396-120">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="50396-121">在伺服器上發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50396-121">An exception was encountered on the server.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="50396-122">建議的動作</span><span class="sxs-lookup"><span data-stu-id="50396-122">Recommended action</span></span>

<span data-ttu-id="50396-123">沒有任何 API 變更。</span><span class="sxs-lookup"><span data-stu-id="50396-123">There are no API changes.</span></span> <span data-ttu-id="50396-124">所有現有的應用程式都會繼續編譯和執行。</span><span class="sxs-lookup"><span data-stu-id="50396-124">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="50396-125">擲回的例外狀況是由伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="50396-125">The exception thrown is handled by the server.</span></span> <span data-ttu-id="50396-126">例如，例外狀況會透過 [Kestrel](/aspnet/core/fundamentals/servers/kestrel) 或 [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)轉換成 HTTP 500 錯誤回應。</span><span class="sxs-lookup"><span data-stu-id="50396-126">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

#### <a name="category"></a><span data-ttu-id="50396-127">類別</span><span class="sxs-lookup"><span data-stu-id="50396-127">Category</span></span>

<span data-ttu-id="50396-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="50396-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="50396-129">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="50396-129">Affected APIs</span></span>

<span data-ttu-id="50396-130">無</span><span class="sxs-lookup"><span data-stu-id="50396-130">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
