---
title: 分析相依性以將程式碼移植到 .NET Core
description: 了解如何分析外部相依性，以將您的專案從 .NET Framework 移植到 .NET Core。
author: cartermp
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: dce8e6cd4986b15cf926154b378964db4beef398
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170312"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="5d6b9-103">分析您的相依性以將程式碼移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="5d6b9-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="5d6b9-104">要將程式碼移植到 .NET Core 或 .NET Standard，您必須了解您的相依性。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="5d6b9-105">外部依賴項是您在專案中參考的 [NuGet 套件](#analyze-referenced-nuget-packages-on-your-project)或 [DLL](#analyze-dependencies-that-arent-nuget-packages)，但您不建置它們。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="5d6b9-106">評估每個相依性，並針對與 .NET Core 不相容的相依性開發應變計劃。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="5d6b9-107">以下是如何判斷相依性是否與 .NET Core 相容。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="5d6b9-108">分析專案中參考的 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="5d6b9-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="5d6b9-109">如果您在專案中參考 NuGet 套件，您需要確認其是否與 .NET Core 相容。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="5d6b9-110">有兩種方法可達成該目標：</span><span class="sxs-lookup"><span data-stu-id="5d6b9-110">There are two ways to accomplish that:</span></span>

* [<span data-ttu-id="5d6b9-111">使用 NuGet 套件總管應用程式</span><span class="sxs-lookup"><span data-stu-id="5d6b9-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
* [<span data-ttu-id="5d6b9-112">使用 nuget.org 網站</span><span class="sxs-lookup"><span data-stu-id="5d6b9-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="5d6b9-113">分析套件之後，如果這些套件與 .NET Core 不相容並只以 .NET Framework 為目標，您可以檢查 [.NET Framework 相容性模式](#net-framework-compatibility-mode)是否可以協助您的移植程序。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="5d6b9-114">使用 NuGet 套件總管分析 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="5d6b9-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="5d6b9-115">NuGet 套件本身是一組包含平台特定組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="5d6b9-116">因此，您需要檢查套件中是否有包含相容組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="5d6b9-117">使用 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)工具是檢查 NuGet 套件資料夾的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="5d6b9-118">安裝後，您可以使用下列步驟來查看資料夾名稱：</span><span class="sxs-lookup"><span data-stu-id="5d6b9-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="5d6b9-119">開啟 NuGet 套件總管。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="5d6b9-120">按一下 [Open package from online feed] (從線上摘要開啟套件)。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="5d6b9-121">搜尋封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="5d6b9-122">從搜尋結果選取套件名稱，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="5d6b9-123">展開右邊的 *lib* 資料夾，並查看資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="5d6b9-124">尋找具有下列任何名稱的資料夾：</span><span class="sxs-lookup"><span data-stu-id="5d6b9-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="5d6b9-125">這些值是對應至 [.NET Standard](../../standard/net-standard.md)、.NET Core 以及與 .NET Core 相容之傳統可攜式類別庫 (PCL) 設定檔版本的[目標 Framework Moniker (TFM)](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d6b9-126">查看套件支援的 TFM 時，請注意，`netcoreapp*` 雖然相容，但只適用於 .NET Core 專案而不適用於 .NET Standard 專案。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="5d6b9-127">其他 .NET Core 應用程式只可取用以 `netcoreapp*` (而不是 `netstandard*`) 為目標的程式庫。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="5d6b9-128">使用 nuget.org 分析 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="5d6b9-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="5d6b9-129">或者，您可以在 [nuget.org](https://www.nuget.org/) 上，於套件頁面的 [相依性] 區段下，查看每個套件支援的 TFM。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="5d6b9-130">雖然使用網站是確認相容性的較簡單方法，但網站上不會提供所有套件的**相依性**資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="5d6b9-131">.NET Framework 相容性模式</span><span class="sxs-lookup"><span data-stu-id="5d6b9-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="5d6b9-132">分析 NuGet 套件之後，您可能會發現這些套件只會以 .NET Framework 為目標，如同大多數 NuGet 套件一樣。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="5d6b9-133">從 .NET Standard 2.0 開始，引進了 .NET Framework 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="5d6b9-134">此相容性模式可讓 .NET Standard 和 .NET Core 專案參考 .NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="5d6b9-135">並非所有專案都適合參考 .NET Framework 程式庫 (例如，如果程式庫使用 Windows Presentation Foundation (WPF) API)，但它確實會解決許多移植案例。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="5d6b9-136">當您在專案中參考以 .NET Framework 為目標的 NuGet 套件時 (例如 [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections))，您會收到類似下列範例的套件後援警告 ([NU1701](/nuget/reference/errors-and-warnings#nu1701))：</span><span class="sxs-lookup"><span data-stu-id="5d6b9-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="5d6b9-137">當您新增套件及每次建置時，都會顯示該警告，以確定您會隨專案測試該套件。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="5d6b9-138">如果您的專案如預期般運作，您可以在 Visual Studio 中編輯套件屬性，或在您慣用的程式碼編輯器中以手動方式編輯專案檔，來隱藏該警告。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="5d6b9-139">若要透過編輯專案檔來隱藏警告，請尋找您要隱藏警告之套件的 `PackageReference` 項目，然後新增 `NoWarn` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="5d6b9-140">`NoWarn` 屬性接受所有警告識別碼的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="5d6b9-141">下列範例示範如何透過手動編輯專案檔，來隱藏 `Huitian.PowerCollections` 套件的 `NU1701` 警告：</span><span class="sxs-lookup"><span data-stu-id="5d6b9-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="5d6b9-142">如需如何在 Visual Studio 中隱藏編譯器警告的詳細資訊，請參閱[隱藏 NuGet 套件的警告](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages)。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="5d6b9-143">將您的套件移植到 `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="5d6b9-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="5d6b9-144">.NET Core 使用 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 來指定套件相依性。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="5d6b9-145">如果您使用 [packages.config](/nuget/reference/packages-config) 指定您的套件，則需要轉換成 `PackageReference`。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="5d6b9-146">您可以在[從 packages.config 移轉至 PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) 深入了解。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="5d6b9-147">NuGet 封裝相依性在 .NET Core 上不執行時該怎麼辦</span><span class="sxs-lookup"><span data-stu-id="5d6b9-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="5d6b9-148">如果您依賴的 NuGet 套件在 .NET Core 上不執行，您可以做幾件事：</span><span class="sxs-lookup"><span data-stu-id="5d6b9-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="5d6b9-149">如果專案是開放原始碼並裝載在 GitHub 等位置，您可以直接連絡開發人員。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="5d6b9-150">您可以在 [nuget.org](https://www.nuget.org/) 上直接連絡作者。搜尋套件，然後按一下套件頁面左邊的 [Contact Owners] (連絡擁有者)。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="5d6b9-151">您可以搜尋在 .NET Core 上執行並與您所用套件達成相同工作的其他套件。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="5d6b9-152">您可以嘗試自行撰寫封裝執行工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="5d6b9-153">您可以變更應用程式的功能，消除封裝的相依性，至少等到有可用的相容版本封裝。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="5d6b9-154">請記住，開放原始碼專案維護者和 NuGet 套件發行者通常是志工。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="5d6b9-155">他們因關心特定領域而參與並免費提供服務，而且通常會有不同的日間工作。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="5d6b9-156">因此連絡他們以取得 .NET Core 支援時請留意。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="5d6b9-157">如果上述任何方法都無法解決您的問題，稍後可能必須移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="5d6b9-158">.NET 小組希望知道哪些程式庫最重要，是 .NET Core 要支援的對象。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="5d6b9-159">您可以傳送電子郵件至 dotnet@microsoft.com 討論您想使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="5d6b9-160">分析不是 NuGet 套件的相依性</span><span class="sxs-lookup"><span data-stu-id="5d6b9-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="5d6b9-161">您可能有不是 NuGet 套件的相依性，例如檔案系統中的 DLL。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="5d6b9-162">判斷該相依性可攜性的唯一方法，是執行 [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) 工具。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="5d6b9-163">此工具可以分析以 .NET Framework 為目標的組件，並識別不可移植到其他 .NET 平台 (例如 .NET Core) 的 API。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="5d6b9-164">您可以將此工具當作主控台應用程式或 [Visual Studio 延伸模組](../../standard/analyzers/portability-analyzer.md)來執行。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5d6b9-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5d6b9-165">Next steps</span></span>

<span data-ttu-id="5d6b9-166">如要移轉程式庫，請參閱 [Porting to .NET Core - Libraries](libraries.md) (移轉至 .NET Core - 程式庫)。</span><span class="sxs-lookup"><span data-stu-id="5d6b9-166">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
