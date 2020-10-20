---
title: 分析相依性以將程式碼移植到 .NET Core
description: 了解如何分析外部相依性，以將您的專案從 .NET Framework 移植到 .NET Core。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 430da45052e3953ab49f182b1773fc6d74bd2221
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223599"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="0eabb-103">分析您的相依性以將程式碼移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="0eabb-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="0eabb-104">要將程式碼移植到 .NET Core 或 .NET Standard，您必須了解您的相依性。</span><span class="sxs-lookup"><span data-stu-id="0eabb-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="0eabb-105">外部相依性是 `.dll` 您在專案中參考的 NuGet 套件或檔案，但您不會自行建立。</span><span class="sxs-lookup"><span data-stu-id="0eabb-105">External dependencies are the NuGet packages or `.dll` files you reference in your project, but that you don't build yourself.</span></span>

## <a name="migrate-your-nuget-packages-to-packagereference"></a><span data-ttu-id="0eabb-106">將您的 NuGet 套件遷移至 `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="0eabb-106">Migrate your NuGet packages to `PackageReference`</span></span>

<span data-ttu-id="0eabb-107">.NET Core 使用 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 來指定套件相依性。</span><span class="sxs-lookup"><span data-stu-id="0eabb-107">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="0eabb-108">如果您要使用 [packages.config](/nuget/reference/packages-config) 在您的專案中指定套件，請將它轉換成 `PackageReference` 格式，因為 `packages.config` .net Core 不支援這些封裝。</span><span class="sxs-lookup"><span data-stu-id="0eabb-108">If you're using [packages.config](/nuget/reference/packages-config) to specify your packages in your project, convert it to the `PackageReference` format, because `packages.config` isn't supported in .NET Core.</span></span>

<span data-ttu-id="0eabb-109">若要瞭解如何遷移，請參閱 [從 packages.config 遷移至 PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) 文章。</span><span class="sxs-lookup"><span data-stu-id="0eabb-109">To learn how to migrate, see the [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) article.</span></span>

## <a name="upgrade-your-nuget-packages"></a><span data-ttu-id="0eabb-110">升級您的 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="0eabb-110">Upgrade your NuGet packages</span></span>

<span data-ttu-id="0eabb-111">將專案遷移至 `PackageReference` 格式之後，請確認您的套件是否與 .Net Core 相容。</span><span class="sxs-lookup"><span data-stu-id="0eabb-111">After you migrate your project to the `PackageReference` format, verify if your packages are compatible with .NET Core.</span></span>

<span data-ttu-id="0eabb-112">首先，將您的套件升級為您可以的最新版本。</span><span class="sxs-lookup"><span data-stu-id="0eabb-112">First, upgrade your packages to the latest version that you can.</span></span> <span data-ttu-id="0eabb-113">您可以使用 Visual Studio 中的 NuGet 封裝管理員 UI 來完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="0eabb-113">This can be done with the NuGet Package Manager UI in Visual Studio.</span></span> <span data-ttu-id="0eabb-114">較新版本的套件相依性可能已與 .NET Core 相容。</span><span class="sxs-lookup"><span data-stu-id="0eabb-114">It's likely that newer versions of your package dependencies are already compatible with .NET Core.</span></span>

## <a name="analyze-your-package-dependencies"></a><span data-ttu-id="0eabb-115">分析您的套件相依性</span><span class="sxs-lookup"><span data-stu-id="0eabb-115">Analyze your package dependencies</span></span>

<span data-ttu-id="0eabb-116">如果您尚未確認已轉換和升級的套件相依性可在 .NET Core 上運作，您有幾種方式可以達成此目的：</span><span class="sxs-lookup"><span data-stu-id="0eabb-116">If you haven't already verified that your converted and upgraded package dependencies work on .NET Core, there are a few ways that you can achieve that:</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="0eabb-117">使用 nuget.org 分析 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="0eabb-117">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="0eabb-118">您可以在 [封裝] 頁面的 [相依性 **]** 區段下，查看每個封裝在[nuget.org](https://www.nuget.org/)上所支援的目標 Framework 名字 (tfm) 。</span><span class="sxs-lookup"><span data-stu-id="0eabb-118">You can see the Target Framework Monikers (TFMs) that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="0eabb-119">雖然使用網站是驗證相容性的較簡單 **方法，但** 所有套件的網站上都無法使用相依性資訊。</span><span class="sxs-lookup"><span data-stu-id="0eabb-119">Although using the site is an easier method to verify the compatibility, **Dependencies** information isn't available on the site for all packages.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="0eabb-120">使用 NuGet 套件總管分析 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="0eabb-120">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="0eabb-121">NuGet 套件本身是一組包含平台特定組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0eabb-121">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="0eabb-122">檢查封裝內是否有包含相容元件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0eabb-122">Check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="0eabb-123">檢查 NuGet 套件資料夾最簡單的方式是使用 [Nuget 套件瀏覽器](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) 工具。</span><span class="sxs-lookup"><span data-stu-id="0eabb-123">The easiest way to inspect NuGet package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="0eabb-124">安裝後，您可以使用下列步驟來查看資料夾名稱：</span><span class="sxs-lookup"><span data-stu-id="0eabb-124">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="0eabb-125">開啟 NuGet 套件總管。</span><span class="sxs-lookup"><span data-stu-id="0eabb-125">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="0eabb-126">按一下 [Open package from online feed] (從線上摘要開啟套件)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0eabb-126">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="0eabb-127">搜尋封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="0eabb-127">Search for the name of the package.</span></span>
4. <span data-ttu-id="0eabb-128">從搜尋結果選取套件名稱，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0eabb-128">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="0eabb-129">展開右邊的 *lib* 資料夾，並查看資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="0eabb-129">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="0eabb-130">使用下列模式尋找具有名稱的資料夾： `netstandardX.Y` 或 `netcoreappX.Y` 。</span><span class="sxs-lookup"><span data-stu-id="0eabb-130">Look for a folder with names using one the following patterns: `netstandardX.Y` or `netcoreappX.Y`.</span></span>

<span data-ttu-id="0eabb-131">這些值是 [ (tfm) 的目標 Framework ](../../standard/frameworks.md) 標記，對應至與 .net core 相容的 [.NET Standard](../../standard/net-standard.md)、.net Core 和傳統的可移植類別庫 (PCL) 設定檔的版本。</span><span class="sxs-lookup"><span data-stu-id="0eabb-131">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0eabb-132">查看套件支援的 TFM 時，請注意，`netcoreapp*` 雖然相容，但只適用於 .NET Core 專案而不適用於 .NET Standard 專案。</span><span class="sxs-lookup"><span data-stu-id="0eabb-132">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="0eabb-133">其他 .NET Core 應用程式只可取用以 `netcoreapp*` (而不是 `netstandard*`) 為目標的程式庫。</span><span class="sxs-lookup"><span data-stu-id="0eabb-133">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

## <a name="net-framework-compatibility-mode"></a><span data-ttu-id="0eabb-134">.NET Framework 相容性模式</span><span class="sxs-lookup"><span data-stu-id="0eabb-134">.NET Framework compatibility mode</span></span>

<span data-ttu-id="0eabb-135">分析 NuGet 套件之後，您可能會發現它們只以 .NET Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="0eabb-135">After analyzing the NuGet packages, you might find that they only target the .NET Framework.</span></span>

<span data-ttu-id="0eabb-136">從 .NET Standard 2.0 開始，引進了 .NET Framework 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="0eabb-136">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="0eabb-137">此相容性模式可讓 .NET Standard 和 .NET Core 專案參考 .NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="0eabb-137">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="0eabb-138">並非所有專案都適合參考 .NET Framework 程式庫 (例如，如果程式庫使用 Windows Presentation Foundation (WPF) API)，但它確實會解決許多移植案例。</span><span class="sxs-lookup"><span data-stu-id="0eabb-138">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="0eabb-139">當您在專案中參考以 .NET Framework 為目標的 NuGet 套件時（例如 [Huitian. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections)），您會收到套件回復警告 ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) 類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="0eabb-139">When you reference NuGet packages that target .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="0eabb-140">當您新增套件及每次建置時，都會顯示該警告，以確定您會隨專案測試該套件。</span><span class="sxs-lookup"><span data-stu-id="0eabb-140">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="0eabb-141">如果您的專案如預期般運作，您可以在 Visual Studio 中編輯封裝屬性，或在您慣用的程式碼編輯器中手動編輯專案檔，藉此隱藏該警告。</span><span class="sxs-lookup"><span data-stu-id="0eabb-141">If your project works as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="0eabb-142">若要透過編輯專案檔來隱藏警告，請尋找您要隱藏警告之套件的 `PackageReference` 項目，然後新增 `NoWarn` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0eabb-142">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="0eabb-143">`NoWarn` 屬性接受所有警告識別碼的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="0eabb-143">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="0eabb-144">下列範例示範如何透過手動編輯專案檔，來隱藏 `Huitian.PowerCollections` 套件的 `NU1701` 警告：</span><span class="sxs-lookup"><span data-stu-id="0eabb-144">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="0eabb-145">如需如何在 Visual Studio 中隱藏編譯器警告的詳細資訊，請參閱[隱藏 NuGet 套件的警告](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages)。</span><span class="sxs-lookup"><span data-stu-id="0eabb-145">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span></span>

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="0eabb-146">NuGet 封裝相依性在 .NET Core 上不執行時該怎麼辦</span><span class="sxs-lookup"><span data-stu-id="0eabb-146">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="0eabb-147">如果您依賴的 NuGet 套件在 .NET Core 上不執行，您可以做幾件事：</span><span class="sxs-lookup"><span data-stu-id="0eabb-147">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

- <span data-ttu-id="0eabb-148">如果專案是開放原始碼並裝載在 GitHub 等位置，您可以直接連絡開發人員。</span><span class="sxs-lookup"><span data-stu-id="0eabb-148">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
- <span data-ttu-id="0eabb-149">您可以直接在 [nuget.org](https://www.nuget.org/)上聯絡作者。搜尋套件，然後按一下套件頁面左側的 [ **連絡人擁有** 者]。</span><span class="sxs-lookup"><span data-stu-id="0eabb-149">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
- <span data-ttu-id="0eabb-150">您可以搜尋在 .NET Core 上執行並與您所用套件達成相同工作的其他套件。</span><span class="sxs-lookup"><span data-stu-id="0eabb-150">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
- <span data-ttu-id="0eabb-151">您可以嘗試自行撰寫封裝執行工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0eabb-151">You can attempt to write the code the package was doing yourself.</span></span>
- <span data-ttu-id="0eabb-152">您可以變更應用程式的功能，消除封裝的相依性，至少等到有可用的相容版本封裝。</span><span class="sxs-lookup"><span data-stu-id="0eabb-152">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="0eabb-153">請記住，開放原始碼專案維護者和 NuGet 套件發行者通常是志工。</span><span class="sxs-lookup"><span data-stu-id="0eabb-153">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="0eabb-154">他們因關心特定領域而參與並免費提供服務，而且通常會有不同的日間工作。</span><span class="sxs-lookup"><span data-stu-id="0eabb-154">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="0eabb-155">請注意，當您聯絡它們以要求提供 .NET Core 支援時。</span><span class="sxs-lookup"><span data-stu-id="0eabb-155">Be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="0eabb-156">如果您無法使用上述任何選項來解決問題，您可能必須稍後再移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="0eabb-156">If you can't resolve your issue with any of these options, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="0eabb-157">.NET 小組希望知道哪些程式庫最重要，是 .NET Core 要支援的對象。</span><span class="sxs-lookup"><span data-stu-id="0eabb-157">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="0eabb-158">您可以傳送電子郵件至 dotnet@microsoft.com 討論您想使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="0eabb-158">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="0eabb-159">分析不是 NuGet 套件的相依性</span><span class="sxs-lookup"><span data-stu-id="0eabb-159">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="0eabb-160">您可能有不是 NuGet 套件的相依性，例如檔案系統中的 DLL。</span><span class="sxs-lookup"><span data-stu-id="0eabb-160">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="0eabb-161">判斷該相依性可攜性的唯一方法，是執行 [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) 工具。</span><span class="sxs-lookup"><span data-stu-id="0eabb-161">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="0eabb-162">此工具會分析以 .NET Framework 為目標的元件，並識別無法移植到其他 .NET 平臺（例如 .NET Core）的 Api。</span><span class="sxs-lookup"><span data-stu-id="0eabb-162">The tool analyzes assemblies that target the .NET Framework and identifies APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="0eabb-163">您可以將此工具當作主控台應用程式或 [Visual Studio 延伸模組](../../standard/analyzers/portability-analyzer.md)來執行。</span><span class="sxs-lookup"><span data-stu-id="0eabb-163">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0eabb-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0eabb-164">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="0eabb-165">移植程式庫</span><span class="sxs-lookup"><span data-stu-id="0eabb-165">Port libraries</span></span>](libraries.md)
