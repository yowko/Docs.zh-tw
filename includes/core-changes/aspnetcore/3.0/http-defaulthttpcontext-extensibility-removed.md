---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290767"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="0a43a-101">HTTP：已移除 DefaultHttpCoNtext 擴充性</span><span class="sxs-lookup"><span data-stu-id="0a43a-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="0a43a-102">在 ASP.NET Core 3.0 效能改進的過程中，已移除的擴充性 `DefaultHttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="0a43a-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="0a43a-103">類別現在是 `sealed` 。</span><span class="sxs-lookup"><span data-stu-id="0a43a-103">The class is now `sealed`.</span></span> <span data-ttu-id="0a43a-104">如需詳細資訊，請參閱 [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)。</span><span class="sxs-lookup"><span data-stu-id="0a43a-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="0a43a-105">如果您的單元測試使用 `Mock<DefaultHttpContext>` ，請改用 `Mock<HttpContext>` 或 `new DefaultHttpContext()` 。</span><span class="sxs-lookup"><span data-stu-id="0a43a-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="0a43a-106">如需討論，請參閱 [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534)。</span><span class="sxs-lookup"><span data-stu-id="0a43a-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0a43a-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0a43a-107">Version introduced</span></span>

<span data-ttu-id="0a43a-108">3.0</span><span class="sxs-lookup"><span data-stu-id="0a43a-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0a43a-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="0a43a-109">Old behavior</span></span>

<span data-ttu-id="0a43a-110">類別可以衍生自 `DefaultHttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="0a43a-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0a43a-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="0a43a-111">New behavior</span></span>

<span data-ttu-id="0a43a-112">類別無法衍生自 `DefaultHttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="0a43a-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0a43a-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="0a43a-113">Reason for change</span></span>

<span data-ttu-id="0a43a-114">最初提供的擴充性是為了允許共用 `HttpContext` ，但它引進了不必要的複雜度，並阻礙其他優化。</span><span class="sxs-lookup"><span data-stu-id="0a43a-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0a43a-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0a43a-115">Recommended action</span></span>

<span data-ttu-id="0a43a-116">如果您要 `Mock<DefaultHttpContext>` 在單元測試中使用，請改為開始使用 `Mock<HttpContext>` 。</span><span class="sxs-lookup"><span data-stu-id="0a43a-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="0a43a-117">類別</span><span class="sxs-lookup"><span data-stu-id="0a43a-117">Category</span></span>

<span data-ttu-id="0a43a-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0a43a-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a43a-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0a43a-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
