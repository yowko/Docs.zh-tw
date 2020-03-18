---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290767"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="d9957-101">HTTP： 預設 HttpCoNtext 擴充性已被刪除</span><span class="sxs-lookup"><span data-stu-id="d9957-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="d9957-102">作為 ASP.NET Core 3.0 性能改進的一部分，`DefaultHttpContext`已刪除 的擴充性。</span><span class="sxs-lookup"><span data-stu-id="d9957-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="d9957-103">該類現在是`sealed`。</span><span class="sxs-lookup"><span data-stu-id="d9957-103">The class is now `sealed`.</span></span> <span data-ttu-id="d9957-104">有關詳細資訊，請參閱[點網/阿斯平核心#6504](https://github.com/dotnet/aspnetcore/pull/6504)。</span><span class="sxs-lookup"><span data-stu-id="d9957-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="d9957-105">如果您的單元測試使用`Mock<DefaultHttpContext>`、使用`Mock<HttpContext>`或`new DefaultHttpContext()`代替。</span><span class="sxs-lookup"><span data-stu-id="d9957-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="d9957-106">有關討論，請參閱[點網/阿斯平核心#6534](https://github.com/dotnet/aspnetcore/issues/6534)。</span><span class="sxs-lookup"><span data-stu-id="d9957-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d9957-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d9957-107">Version introduced</span></span>

<span data-ttu-id="d9957-108">3.0</span><span class="sxs-lookup"><span data-stu-id="d9957-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d9957-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d9957-109">Old behavior</span></span>

<span data-ttu-id="d9957-110">類可以從`DefaultHttpContext`派生。</span><span class="sxs-lookup"><span data-stu-id="d9957-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d9957-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="d9957-111">New behavior</span></span>

<span data-ttu-id="d9957-112">類無法派生自`DefaultHttpContext`。</span><span class="sxs-lookup"><span data-stu-id="d9957-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d9957-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="d9957-113">Reason for change</span></span>

<span data-ttu-id="d9957-114">擴充性最初是為了允許池化，`HttpContext`但它引入了不必要的複雜性並阻礙了其他優化。</span><span class="sxs-lookup"><span data-stu-id="d9957-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d9957-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d9957-115">Recommended action</span></span>

<span data-ttu-id="d9957-116">如果您在單元測試中使用`Mock<DefaultHttpContext>`，`Mock<HttpContext>`請改用。</span><span class="sxs-lookup"><span data-stu-id="d9957-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="d9957-117">類別</span><span class="sxs-lookup"><span data-stu-id="d9957-117">Category</span></span>

<span data-ttu-id="d9957-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d9957-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d9957-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d9957-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
