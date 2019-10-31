---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198386"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="fe9e1-101">HTTP： DefaultHttpCoNtext 擴充性已移除</span><span class="sxs-lookup"><span data-stu-id="fe9e1-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="fe9e1-102">在 ASP.NET Core 3.0 效能改進的過程中，已移除 `DefaultHttpContext` 的擴充性。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="fe9e1-103">類別現在 `sealed`。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-103">The class is now `sealed`.</span></span> <span data-ttu-id="fe9e1-104">如需詳細資訊，請參閱[aspnet/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504)。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="fe9e1-105">如果您的單元測試使用 `Mock<DefaultHttpContext>`，請改用 `Mock<HttpContext>`。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span>

<span data-ttu-id="fe9e1-106">如需討論，請參閱[aspnet/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534)。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fe9e1-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="fe9e1-107">Version introduced</span></span>

<span data-ttu-id="fe9e1-108">3.0</span><span class="sxs-lookup"><span data-stu-id="fe9e1-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fe9e1-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="fe9e1-109">Old behavior</span></span>

<span data-ttu-id="fe9e1-110">類別可以衍生自 `DefaultHttpContext`。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fe9e1-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="fe9e1-111">New behavior</span></span>

<span data-ttu-id="fe9e1-112">類別無法衍生自 `DefaultHttpContext`。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fe9e1-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="fe9e1-113">Reason for change</span></span>

<span data-ttu-id="fe9e1-114">最初提供的擴充性是為了允許 `HttpContext` 的集區，但它引進了不必要的複雜性並阻礙其他優化。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe9e1-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="fe9e1-115">Recommended action</span></span>

<span data-ttu-id="fe9e1-116">如果您是在單元測試中使用 `Mock<DefaultHttpContext>`，請改為開始使用 `Mock<HttpContext>`。</span><span class="sxs-lookup"><span data-stu-id="fe9e1-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="fe9e1-117">Category</span><span class="sxs-lookup"><span data-stu-id="fe9e1-117">Category</span></span>

<span data-ttu-id="fe9e1-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fe9e1-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fe9e1-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fe9e1-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
