---
ms.openlocfilehash: 3f702febc78488b9413ec9303ded211493650f02
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198385"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="c97e9-101">MVC：先行編譯工具已被取代</span><span class="sxs-lookup"><span data-stu-id="c97e9-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="c97e9-102">在 ASP.NET Core 1.1 中，已引進 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` （MVC 先行編譯工具）封裝，以新增對 Razor 檔案（*cshtml*檔案）之發行時間編譯的支援。</span><span class="sxs-lookup"><span data-stu-id="c97e9-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="c97e9-103">在 ASP.NET Core 2.1 中，引進了[RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1)以擴充先行編譯工具的功能。</span><span class="sxs-lookup"><span data-stu-id="c97e9-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="c97e9-104">Razor SDK 新增了 Razor 檔案的組建和發行時間編譯支援。</span><span class="sxs-lookup"><span data-stu-id="c97e9-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="c97e9-105">SDK 會在組建期間驗證 *. cshtml*檔案的正確性，同時改善應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="c97e9-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="c97e9-106">Razor SDK 預設為開啟，而且不需要手勢就可以開始使用它。</span><span class="sxs-lookup"><span data-stu-id="c97e9-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="c97e9-107">在 ASP.NET Core 3.0 中，已移除 ASP.NET Core 1.1 年代 MVC 先行編譯工具。</span><span class="sxs-lookup"><span data-stu-id="c97e9-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="c97e9-108">較舊的套件版本會繼續在修補程式版本中收到重要的錯誤和安全性修正程式。</span><span class="sxs-lookup"><span data-stu-id="c97e9-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c97e9-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c97e9-109">Version introduced</span></span>

<span data-ttu-id="c97e9-110">3.0</span><span class="sxs-lookup"><span data-stu-id="c97e9-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c97e9-111">舊的行為</span><span class="sxs-lookup"><span data-stu-id="c97e9-111">Old behavior</span></span>

<span data-ttu-id="c97e9-112">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` 套件是用來預先編譯 MVC Razor views。</span><span class="sxs-lookup"><span data-stu-id="c97e9-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c97e9-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="c97e9-113">New behavior</span></span>

<span data-ttu-id="c97e9-114">Razor SDK 原本就支援這種功能。</span><span class="sxs-lookup"><span data-stu-id="c97e9-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="c97e9-115">已不再更新 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` 套件。</span><span class="sxs-lookup"><span data-stu-id="c97e9-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c97e9-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="c97e9-116">Reason for change</span></span>

<span data-ttu-id="c97e9-117">Razor SDK 會提供更多功能，並在組建時驗證 *. cshtml*檔案的正確性。</span><span class="sxs-lookup"><span data-stu-id="c97e9-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="c97e9-118">SDK 也會改善應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="c97e9-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c97e9-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c97e9-119">Recommended action</span></span>

<span data-ttu-id="c97e9-120">針對 ASP.NET Core 2.1 或更新版本的使用者，請更新以在[RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中使用先行編譯的原生支援。</span><span class="sxs-lookup"><span data-stu-id="c97e9-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="c97e9-121">如果 bug 或遺漏功能導致無法遷移至 Razor SDK，請在[aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues)開啟問題。</span><span class="sxs-lookup"><span data-stu-id="c97e9-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="c97e9-122">Category</span><span class="sxs-lookup"><span data-stu-id="c97e9-122">Category</span></span>

<span data-ttu-id="c97e9-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c97e9-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c97e9-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c97e9-124">Affected APIs</span></span>

<span data-ttu-id="c97e9-125">None</span><span class="sxs-lookup"><span data-stu-id="c97e9-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
