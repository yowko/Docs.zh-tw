---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416271"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="4152d-101">Blazor： NuGet 套件的目標 framework 已變更</span><span class="sxs-lookup"><span data-stu-id="4152d-101">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="4152d-102">Blazor 3.2 WebAssembly 專案已編譯為以 .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`) 為目標。</span><span class="sxs-lookup"><span data-stu-id="4152d-102">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="4152d-103">在 ASP.NET Core 5.0 中，Blazor 伺服器和 Blazor WebAssembly 專案都是以 .NET 5.0 () 為目標 `<TargetFramework>net5.0</TargetFramework>` 。</span><span class="sxs-lookup"><span data-stu-id="4152d-103">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="4152d-104">為了更加符合目標 framework 變更，下列 Blazor 套件不再以 .NET Standard 2.1 為目標：</span><span class="sxs-lookup"><span data-stu-id="4152d-104">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="4152d-105">AspNetCore 元件</span><span class="sxs-lookup"><span data-stu-id="4152d-105">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="4152d-106">AspNetCore。授權</span><span class="sxs-lookup"><span data-stu-id="4152d-106">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="4152d-107">AspNetCore. Forms</span><span class="sxs-lookup"><span data-stu-id="4152d-107">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="4152d-108">AspNetCore Web 元件</span><span class="sxs-lookup"><span data-stu-id="4152d-108">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="4152d-109">AspNetCore. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="4152d-109">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="4152d-110">AspNetCore. WebAssembly. 驗證</span><span class="sxs-lookup"><span data-stu-id="4152d-110">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="4152d-111">Microsoft.JSInterop</span><span class="sxs-lookup"><span data-stu-id="4152d-111">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="4152d-112">Microsoft.JSInterop. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="4152d-112">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="4152d-113">WebAssembly. Msal</span><span class="sxs-lookup"><span data-stu-id="4152d-113">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="4152d-114">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424)。</span><span class="sxs-lookup"><span data-stu-id="4152d-114">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4152d-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4152d-115">Version introduced</span></span>

<span data-ttu-id="4152d-116">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="4152d-116">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4152d-117">舊的行為</span><span class="sxs-lookup"><span data-stu-id="4152d-117">Old behavior</span></span>

<span data-ttu-id="4152d-118">在 Blazor 3.1 和3.2 中，封裝的目標 .NET Standard 2.1 和 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="4152d-118">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4152d-119">新的行為</span><span class="sxs-lookup"><span data-stu-id="4152d-119">New behavior</span></span>

<span data-ttu-id="4152d-120">在 ASP.NET Core 5.0 中，封裝的目標是 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="4152d-120">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4152d-121">變更的原因</span><span class="sxs-lookup"><span data-stu-id="4152d-121">Reason for change</span></span>

<span data-ttu-id="4152d-122">已進行變更，使其更符合 .NET 目標 framework 的需求。</span><span class="sxs-lookup"><span data-stu-id="4152d-122">The change was made to better align with .NET target framework requirements.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4152d-123">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4152d-123">Recommended action</span></span>

<span data-ttu-id="4152d-124">Blazor 3.2 WebAssembly 專案在將其套件參考更新為 5. x.x. 時，應以 .NET 5.0 為目標</span><span class="sxs-lookup"><span data-stu-id="4152d-124">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="4152d-125">參考其中一個套件的程式庫可以根據其需求，以 .NET 5.0 或多重目標為目標。</span><span class="sxs-lookup"><span data-stu-id="4152d-125">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

#### <a name="category"></a><span data-ttu-id="4152d-126">類別</span><span class="sxs-lookup"><span data-stu-id="4152d-126">Category</span></span>

<span data-ttu-id="4152d-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4152d-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4152d-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4152d-128">Affected APIs</span></span>

<span data-ttu-id="4152d-129">無</span><span class="sxs-lookup"><span data-stu-id="4152d-129">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
