---
title: "移轉到 .NET Core - 分析協力廠商相依性"
description: "移轉到 .NET Core - 分析協力廠商相依性"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="0c584-104">移轉到 .NET Core - 分析協力廠商相依性</span><span class="sxs-lookup"><span data-stu-id="0c584-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="0c584-105">移轉程序的第一個步驟是了解您的協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="0c584-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="0c584-106">您需要找出他們哪些尚未執行 .NET Core (如有)，並針對不執行 .NET Core 的開發應變計劃。</span><span class="sxs-lookup"><span data-stu-id="0c584-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c584-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="0c584-107">Prerequisites</span></span>

<span data-ttu-id="0c584-108">本文假設您使用 Windows 和 Visual Studio，並且目前有在 .NET Framework 上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c584-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="0c584-109">分析 NuGet 封裝</span><span class="sxs-lookup"><span data-stu-id="0c584-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="0c584-110">分析 NuGet 封裝的可攜性很簡單。</span><span class="sxs-lookup"><span data-stu-id="0c584-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="0c584-111">因為 NuGet 封裝本身是一組包含特定平台組件的資料夾，所以您只需要查看是否有包含 .NET Core 組件的資料夾即可。</span><span class="sxs-lookup"><span data-stu-id="0c584-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="0c584-112">使用 [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) 工具檢查 NuGet 封裝資料夾非常簡單。</span><span class="sxs-lookup"><span data-stu-id="0c584-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="0c584-113">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="0c584-113">Here's how to do it.</span></span>

1. <span data-ttu-id="0c584-114">下載並開啟 [NuGet Package Explorer] \(NuGet 封裝總管)。</span><span class="sxs-lookup"><span data-stu-id="0c584-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="0c584-115">按一下 「Open package from online feed」 (從線上摘要開啟封裝)。</span><span class="sxs-lookup"><span data-stu-id="0c584-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="0c584-116">搜尋封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c584-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="0c584-117">展開右手邊的 "lib" 資料夾，並查看資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="0c584-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="0c584-118">您也可以在 [nuget.org](https://www.nuget.org/) 該封裝頁面的 [相依性] 區段中查看封裝支援。</span><span class="sxs-lookup"><span data-stu-id="0c584-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="0c584-119">無論哪一種情況，您都需要在 [nuget.org](https://www.nuget.org/) 尋找有任何下列名稱的資料夾或項目︰</span><span class="sxs-lookup"><span data-stu-id="0c584-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="0c584-120">這些是對應 [.NET Standard](../../standard/net-standard.md) 版本的目標 Framework Moniker (TFM) 版本，以及與 .NET Core 相容的傳統可攜式類別庫 (PCL) 設定檔。</span><span class="sxs-lookup"><span data-stu-id="0c584-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="0c584-121">請注意，當 `netcoreapp1.0` 相容時，是用於應用程式，不是程式庫。</span><span class="sxs-lookup"><span data-stu-id="0c584-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="0c584-122">雖然使用 `netcoreapp1.0` 型的程式庫沒有錯，但該程式庫可能原本只打算提供其他 `netcoreapp1.0` 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="0c584-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="0c584-123">還有在 .NET Core 發行前版本中使用的一些舊版 TFM 也可能是相容的：</span><span class="sxs-lookup"><span data-stu-id="0c584-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="0c584-124">**雖然這些可能適合您的程式碼使用，但不保證相容性**。</span><span class="sxs-lookup"><span data-stu-id="0c584-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="0c584-125">有這些 TFM 的封裝過去是使用發行前版本的 .NET Core 封裝建置的。</span><span class="sxs-lookup"><span data-stu-id="0c584-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="0c584-126">這類封裝更新為 `netstandard`型時請記錄。</span><span class="sxs-lookup"><span data-stu-id="0c584-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="0c584-127">若要使用以傳統 PCL 或發行前版本 .NET Core 目標為目標的封裝，`project.json` 檔案中必須使用 `imports` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="0c584-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="0c584-128">NuGet 封裝相依性在 .NET Core 上不執行時該怎麼辦</span><span class="sxs-lookup"><span data-stu-id="0c584-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="0c584-129">如果您依賴的 NuGet 封裝在 .NET Core 上不執行，您可以做幾件事。</span><span class="sxs-lookup"><span data-stu-id="0c584-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="0c584-130">如果專案是開放原始碼並裝載在 GitHub 等位置，您可以直接連絡開發人員。</span><span class="sxs-lookup"><span data-stu-id="0c584-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="0c584-131">您可以搜尋封裝，然後按一下封裝頁面左手邊的 「Contact Owners」 (連絡擁有者)，在 [nuget.org](https://www.nuget.org/) 直接連絡作者。</span><span class="sxs-lookup"><span data-stu-id="0c584-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="0c584-132">您可以尋找另一個在 .NET Core 執行的封裝，與您所用封裝達成相同的工作。</span><span class="sxs-lookup"><span data-stu-id="0c584-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="0c584-133">您可以嘗試自行撰寫封裝執行工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c584-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="0c584-134">您可以變更應用程式的功能，消除封裝的相依性，至少等到有可用的相容版本封裝。</span><span class="sxs-lookup"><span data-stu-id="0c584-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="0c584-135">請記住，開放原始碼專案維護人員及 NuGet 封裝發行者通常是志願工作者，他們因為在乎指定的領域，所以無償付出，通常都有自己的正職工作。</span><span class="sxs-lookup"><span data-stu-id="0c584-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="0c584-136">如果連絡他們，請先提出對程式庫的正面評價，再要求 .NET Core 支援。</span><span class="sxs-lookup"><span data-stu-id="0c584-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="0c584-137">如果上述任何方法都無法解決您的問題，稍後可能必須移轉到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="0c584-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="0c584-138">.NET 小組希望知道哪些程式庫最重要，是 .NET Core 接下來要支援的對象。</span><span class="sxs-lookup"><span data-stu-id="0c584-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="0c584-139">您也可以傳送電子郵件至 dotnet@microsoft.com 討論您想使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="0c584-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="0c584-140">分析不是 NuGet 封裝的相依性</span><span class="sxs-lookup"><span data-stu-id="0c584-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="0c584-141">您可能有不是 NuGet 封裝的相依性，例如檔案系統中的 DLL。</span><span class="sxs-lookup"><span data-stu-id="0c584-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="0c584-142">判斷該相依性可攜性的唯一方法，是執行 [ApiPort 工具](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)。</span><span class="sxs-lookup"><span data-stu-id="0c584-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c584-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0c584-143">Next steps</span></span>

<span data-ttu-id="0c584-144">如要移轉程式庫，請參閱 [Porting to .NET Core - Libraries](libraries.md) (移轉至 .NET Core - 程式庫)。</span><span class="sxs-lookup"><span data-stu-id="0c584-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
