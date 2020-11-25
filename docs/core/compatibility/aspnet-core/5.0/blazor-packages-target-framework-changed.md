---
title: 重大變更： Blazor： NuGet 套件的目標 framework 已變更
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： NuGet 套件的目標 framework 已變更
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5515edc66ff9786f0d8f7e24e5fc28c71502567b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760665"
---
# <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="9a616-103">Blazor： NuGet 套件的目標 framework 已變更</span><span class="sxs-lookup"><span data-stu-id="9a616-103">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="9a616-104">Blazor 3.2 WebAssembly 專案已編譯為以 .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`) 為目標。</span><span class="sxs-lookup"><span data-stu-id="9a616-104">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="9a616-105">在 ASP.NET Core 5.0 中，Blazor 伺服器和 Blazor WebAssembly 專案都是以 .NET 5.0 () 為目標 `<TargetFramework>net5.0</TargetFramework>` 。</span><span class="sxs-lookup"><span data-stu-id="9a616-105">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="9a616-106">為了更加符合目標 framework 變更，下列 Blazor 套件不再以 .NET Standard 2.1 為目標：</span><span class="sxs-lookup"><span data-stu-id="9a616-106">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="9a616-107">AspNetCore 元件</span><span class="sxs-lookup"><span data-stu-id="9a616-107">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="9a616-108">AspNetCore。授權</span><span class="sxs-lookup"><span data-stu-id="9a616-108">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="9a616-109">AspNetCore. Forms</span><span class="sxs-lookup"><span data-stu-id="9a616-109">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="9a616-110">AspNetCore Web 元件</span><span class="sxs-lookup"><span data-stu-id="9a616-110">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="9a616-111">AspNetCore. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="9a616-111">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="9a616-112">AspNetCore. WebAssembly. 驗證</span><span class="sxs-lookup"><span data-stu-id="9a616-112">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="9a616-113">Microsoft.JSInterop</span><span class="sxs-lookup"><span data-stu-id="9a616-113">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="9a616-114">Microsoft.JSInterop. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="9a616-114">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="9a616-115">WebAssembly. Msal</span><span class="sxs-lookup"><span data-stu-id="9a616-115">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="9a616-116">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424)。</span><span class="sxs-lookup"><span data-stu-id="9a616-116">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9a616-117">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9a616-117">Version introduced</span></span>

<span data-ttu-id="9a616-118">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="9a616-118">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="9a616-119">舊的行為</span><span class="sxs-lookup"><span data-stu-id="9a616-119">Old behavior</span></span>

<span data-ttu-id="9a616-120">在 Blazor 3.1 和3.2 中，封裝的目標 .NET Standard 2.1 和 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="9a616-120">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="9a616-121">新的行為</span><span class="sxs-lookup"><span data-stu-id="9a616-121">New behavior</span></span>

<span data-ttu-id="9a616-122">在 ASP.NET Core 5.0 中，封裝的目標是 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="9a616-122">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9a616-123">變更的原因</span><span class="sxs-lookup"><span data-stu-id="9a616-123">Reason for change</span></span>

<span data-ttu-id="9a616-124">已進行變更，使其更符合 .NET 目標 framework 的需求。</span><span class="sxs-lookup"><span data-stu-id="9a616-124">The change was made to better align with .NET target framework requirements.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9a616-125">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9a616-125">Recommended action</span></span>

<span data-ttu-id="9a616-126">Blazor 3.2 WebAssembly 專案在將其套件參考更新為 5. x.x. 時，應以 .NET 5.0 為目標</span><span class="sxs-lookup"><span data-stu-id="9a616-126">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="9a616-127">參考其中一個套件的程式庫可以根據其需求，以 .NET 5.0 或多重目標為目標。</span><span class="sxs-lookup"><span data-stu-id="9a616-127">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9a616-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9a616-128">Affected APIs</span></span>

<span data-ttu-id="9a616-129">None</span><span class="sxs-lookup"><span data-stu-id="9a616-129">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
