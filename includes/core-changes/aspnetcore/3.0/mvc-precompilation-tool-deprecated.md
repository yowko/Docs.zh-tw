---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901784"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="818eb-101">MVC：預編譯工具已棄用</span><span class="sxs-lookup"><span data-stu-id="818eb-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="818eb-102">在 ASP.NET Core 1.1 中，引入了`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`（MVC 預編譯工具）包，以添加對 Razor 檔 *（.cshtml*檔） 發佈時間編譯的支援。</span><span class="sxs-lookup"><span data-stu-id="818eb-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="818eb-103">在ASP.NET核心 2.1 中，引入了[Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1)來擴展預編譯工具的功能。</span><span class="sxs-lookup"><span data-stu-id="818eb-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="818eb-104">Razor SDK 增加了對 Razor 檔的生成和發佈時間編譯的支援。</span><span class="sxs-lookup"><span data-stu-id="818eb-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="818eb-105">SDK 驗證 *.cshtml*檔在生成時間的正確性，同時提高應用啟動時間。</span><span class="sxs-lookup"><span data-stu-id="818eb-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="818eb-106">預設情況下，Razor SDK 處於打開狀態，無需手勢即可開始使用它。</span><span class="sxs-lookup"><span data-stu-id="818eb-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="818eb-107">在 ASP.NET Core 3.0 中，ASP.NET核心 1.1 時代 MVC 預編譯工具被刪除。</span><span class="sxs-lookup"><span data-stu-id="818eb-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="818eb-108">早期包版本將繼續在修補程式版本中接收重要的 Bug 和安全修補程式。</span><span class="sxs-lookup"><span data-stu-id="818eb-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="818eb-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="818eb-109">Version introduced</span></span>

<span data-ttu-id="818eb-110">3.0</span><span class="sxs-lookup"><span data-stu-id="818eb-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="818eb-111">舊的行為</span><span class="sxs-lookup"><span data-stu-id="818eb-111">Old behavior</span></span>

<span data-ttu-id="818eb-112">該`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`包用於預編譯 MVC Razor 視圖。</span><span class="sxs-lookup"><span data-stu-id="818eb-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="818eb-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="818eb-113">New behavior</span></span>

<span data-ttu-id="818eb-114">Razor SDK 本機支援此功能。</span><span class="sxs-lookup"><span data-stu-id="818eb-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="818eb-115">程式`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`包不再更新。</span><span class="sxs-lookup"><span data-stu-id="818eb-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="818eb-116">更改原因</span><span class="sxs-lookup"><span data-stu-id="818eb-116">Reason for change</span></span>

<span data-ttu-id="818eb-117">Razor SDK 提供了更多功能，並在生成時驗證 *.cshtml*檔的正確性。</span><span class="sxs-lookup"><span data-stu-id="818eb-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="818eb-118">SDK 還提高了應用啟動時間。</span><span class="sxs-lookup"><span data-stu-id="818eb-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="818eb-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="818eb-119">Recommended action</span></span>

<span data-ttu-id="818eb-120">對於ASP.NET Core 2.1 或更高版本的使用者，請更新以使用本機支援在[Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中預編譯。</span><span class="sxs-lookup"><span data-stu-id="818eb-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="818eb-121">如果 Bug 或缺少功能阻止遷移到 Razor SDK，請在[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)上打開問題。</span><span class="sxs-lookup"><span data-stu-id="818eb-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="818eb-122">類別</span><span class="sxs-lookup"><span data-stu-id="818eb-122">Category</span></span>

<span data-ttu-id="818eb-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="818eb-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="818eb-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="818eb-124">Affected APIs</span></span>

<span data-ttu-id="818eb-125">None</span><span class="sxs-lookup"><span data-stu-id="818eb-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
