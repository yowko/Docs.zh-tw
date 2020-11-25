---
ms.openlocfilehash: 8395428e1729a00fc1af72cf53fe689ee95b5fdf
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032392"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="bb837-101">MVC：先行編譯工具已淘汰</span><span class="sxs-lookup"><span data-stu-id="bb837-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="bb837-102">在 ASP.NET Core 1.1 中，導入了 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC 預先編譯工具) 封裝，以將 (Razor 檔案的發行時間編譯支援新增至) 的 *cshtml* 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb837-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="bb837-103">在 ASP.NET Core 2.1 中引進了 [RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) ，以在先行編譯工具的功能上擴充。</span><span class="sxs-lookup"><span data-stu-id="bb837-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="bb837-104">Razor SDK 新增了 Razor 檔案的組建和發行時間編譯支援。</span><span class="sxs-lookup"><span data-stu-id="bb837-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="bb837-105">SDK 會在組建階段驗證 *cshtml* 檔案的正確性，同時改善應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="bb837-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="bb837-106">Razor SDK 預設為開啟，且不需要手勢即可開始使用。</span><span class="sxs-lookup"><span data-stu-id="bb837-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="bb837-107">在 ASP.NET Core 3.0 中，已移除 ASP.NET Core 1.1-紀元 MVC 先行編譯工具。</span><span class="sxs-lookup"><span data-stu-id="bb837-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="bb837-108">較舊的套件版本將繼續收到修補程式版本中的重要 bug 和安全性修正程式。</span><span class="sxs-lookup"><span data-stu-id="bb837-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb837-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bb837-109">Version introduced</span></span>

<span data-ttu-id="bb837-110">3.0</span><span class="sxs-lookup"><span data-stu-id="bb837-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bb837-111">舊的行為</span><span class="sxs-lookup"><span data-stu-id="bb837-111">Old behavior</span></span>

<span data-ttu-id="bb837-112">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`封裝是用來預先編譯 MVC Razor views。</span><span class="sxs-lookup"><span data-stu-id="bb837-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bb837-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="bb837-113">New behavior</span></span>

<span data-ttu-id="bb837-114">Razor SDK 原本就支援此功能。</span><span class="sxs-lookup"><span data-stu-id="bb837-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="bb837-115">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`套件不再更新。</span><span class="sxs-lookup"><span data-stu-id="bb837-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bb837-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="bb837-116">Reason for change</span></span>

<span data-ttu-id="bb837-117">Razor SDK 提供更多功能，並在組建時驗證 *cshtml* 檔案的正確性。</span><span class="sxs-lookup"><span data-stu-id="bb837-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="bb837-118">SDK 也可改善應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="bb837-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb837-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bb837-119">Recommended action</span></span>

<span data-ttu-id="bb837-120">針對 ASP.NET Core 2.1 或更新版本的使用者，請更新以在 [RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中使用先行編譯的原生支援。</span><span class="sxs-lookup"><span data-stu-id="bb837-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="bb837-121">如果 bug 或遺失的功能無法遷移至 Razor SDK，請在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)開啟問題。</span><span class="sxs-lookup"><span data-stu-id="bb837-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="bb837-122">類別</span><span class="sxs-lookup"><span data-stu-id="bb837-122">Category</span></span>

<span data-ttu-id="bb837-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bb837-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb837-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bb837-124">Affected APIs</span></span>

<span data-ttu-id="bb837-125">None</span><span class="sxs-lookup"><span data-stu-id="bb837-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
