---
title: NuGet 與 .NET 程式庫
description: 針對 .NET 程式庫搭配 NuGet 進行封裝的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 479d1786c232ef1f843877169954e847453681c9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185614"
---
# <a name="nuget"></a><span data-ttu-id="6053c-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="6053c-103">NuGet</span></span>

<span data-ttu-id="6053c-104">NuGet 是適用於 .NET 生態系統的套件管理員，也是開發人員探索並取得 .NET 開放原始碼程式庫的主要方式。</span><span class="sxs-lookup"><span data-stu-id="6053c-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="6053c-105">[NuGet.org](https://www.nuget.org/) \(英文\) 是 Microsoft 提供用來裝載 NuGet 套件的免費服務，它是公用 NuGet 套件的主要主機；但您也可以發佈至自訂的 NuGet 服務，例如 [MyGet](https://www.myget.org/) \(英文\) 與 [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/)。</span><span class="sxs-lookup"><span data-stu-id="6053c-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="6053c-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="6053c-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="6053c-107">建立 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="6053c-107">Create a NuGet package</span></span>

<span data-ttu-id="6053c-108">NuGet 套件 (`*.nupkg`) 是包含 .NET 組件與相關聯中繼資料的 Zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="6053c-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="6053c-109">有兩種主要的方式可用來建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="6053c-110">較新且建議的方式，是從 SDK 樣式專案 (內容以 `<Project Sdk="Microsoft.NET.Sdk">` 作為開頭的專案) 建立套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="6053c-111">系統會自動將組件與目標新增到套件中，並將剩餘的中繼資料新增到 MSBuild 檔案，例如套件名稱與版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6053c-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="6053c-112">搭配 [`dotnet pack`](../../core/tools/dotnet-pack.md) 命令進行編譯將會輸出 `*.nupkg` 檔案，而非組件。</span><span class="sxs-lookup"><span data-stu-id="6053c-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6053c-113">較舊的 NuGet 套件建立方式，是使用 `*.nuspec` 檔案與 `nuget.exe` 命令列工具來建立。</span><span class="sxs-lookup"><span data-stu-id="6053c-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="6053c-114">nuspec 檔案可讓您做出大幅度的控制，但您必須仔細地指定要在最終的 NuGet 套件中包含哪些組件與目標。</span><span class="sxs-lookup"><span data-stu-id="6053c-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="6053c-115">這是一件很容易出錯的工作，也很容易在未來做出變更後忘記更新 nuspec 檔案。</span><span class="sxs-lookup"><span data-stu-id="6053c-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="6053c-116">nuspec 的優點在於您可以用它來針對尚未支援 SDK 樣式專案檔的架構建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="6053c-117">**✔️ 請考慮**使用 SDK 樣式專案檔來建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="6053c-118">**✔️ 請考慮**設定 SourceLink 以將來源控制中繼資料新增到您的組件與 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="6053c-119">套件相依性</span><span class="sxs-lookup"><span data-stu-id="6053c-119">Package dependencies</span></span>

<span data-ttu-id="6053c-120">NuGet 套件相依性已詳述於[相依性](./dependencies.md)一文中。</span><span class="sxs-lookup"><span data-stu-id="6053c-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="6053c-121">重要的 NuGet 套件中繼資料</span><span class="sxs-lookup"><span data-stu-id="6053c-121">Important NuGet package metadata</span></span>

<span data-ttu-id="6053c-122">NuGet 套件能支援許多[中繼資料屬性](/nuget/reference/nuspec)。</span><span class="sxs-lookup"><span data-stu-id="6053c-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="6053c-123">下表包含所有開放原始碼專案都應提供的核心中繼資料：</span><span class="sxs-lookup"><span data-stu-id="6053c-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="6053c-124">MSBuild 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="6053c-124">MSBuild Property name</span></span>              | <span data-ttu-id="6053c-125">Nuspec 名稱</span><span class="sxs-lookup"><span data-stu-id="6053c-125">Nuspec name</span></span>              | <span data-ttu-id="6053c-126">描述</span><span class="sxs-lookup"><span data-stu-id="6053c-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="6053c-127">套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="6053c-127">The package identifier.</span></span> <span data-ttu-id="6053c-128">如果來自識別碼的前置詞符合[準則](/nuget/reference/id-prefix-reservation)，便可以對它進行保留。</span><span class="sxs-lookup"><span data-stu-id="6053c-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="6053c-129">NuGet 套件版本。</span><span class="sxs-lookup"><span data-stu-id="6053c-129">NuGet package version.</span></span> <span data-ttu-id="6053c-130">如需詳細資訊，請參閱 [NuGet 套件版本](./versioning.md#nuget-package-version)。</span><span class="sxs-lookup"><span data-stu-id="6053c-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="6053c-131">人類容易記住的套件標題。</span><span class="sxs-lookup"><span data-stu-id="6053c-131">A human-friendly title of the package.</span></span> <span data-ttu-id="6053c-132">預設值為 `PackageId`。</span><span class="sxs-lookup"><span data-stu-id="6053c-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="6053c-133">在 UI 中顯示的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="6053c-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="6053c-134">以逗號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6053c-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="6053c-135">以空格分隔的標記與關鍵字清單，能描述套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="6053c-136">標記會在搜尋套件時使用。</span><span class="sxs-lookup"><span data-stu-id="6053c-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="6053c-137">要作為套件圖示使用之影像的 URL。</span><span class="sxs-lookup"><span data-stu-id="6053c-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="6053c-138">URL 應為 HTTPS 且影像大小應為 64x64 並具有透明背景。</span><span class="sxs-lookup"><span data-stu-id="6053c-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="6053c-139">專案首頁或來源存放庫的 URL。</span><span class="sxs-lookup"><span data-stu-id="6053c-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="6053c-140">專案授權的 URL。</span><span class="sxs-lookup"><span data-stu-id="6053c-140">A URL to the project license.</span></span> <span data-ttu-id="6053c-141">可以是原始檔控制中 `LICENSE` 檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="6053c-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="6053c-142">**✔️ 請考慮**選擇具有符合 NuGet 的前置詞保留[準則](/nuget/reference/id-prefix-reservation)之前置詞的 NuGet 套件名稱。</span><span class="sxs-lookup"><span data-stu-id="6053c-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="6053c-143">**✔️ 請考慮**使用原始檔控制中的 `LICENSE` 檔案作為 `LicenseUrl`。</span><span class="sxs-lookup"><span data-stu-id="6053c-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="6053c-144">例如 [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="6053c-144">For example, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6053c-145">沒有授權的專案預設會具有[專屬著作權](https://choosealicense.com/no-permission/) \(英文\)，這會使其他人無法使用它。</span><span class="sxs-lookup"><span data-stu-id="6053c-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="6053c-146">**✔️ 請務必**為您的套件圖示使用 HTTPS href。</span><span class="sxs-lookup"><span data-stu-id="6053c-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="6053c-147">NuGet.org 等網站會在啟用 HTTPS 的情況下執行，因此顯示非 HTTPS 影像將會產生混合內容警告。</span><span class="sxs-lookup"><span data-stu-id="6053c-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="6053c-148">**✔️ 請務必**使用大小為 64x64 且具有透明背景的套件圖示影像，以取得最佳檢視效果。</span><span class="sxs-lookup"><span data-stu-id="6053c-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="6053c-149">發行前套件</span><span class="sxs-lookup"><span data-stu-id="6053c-149">Pre-release packages</span></span>

<span data-ttu-id="6053c-150">具有版本尾碼的 NuGet 套件會被系統視為[發行前版本](/nuget/create-packages/prerelease-packages)。</span><span class="sxs-lookup"><span data-stu-id="6053c-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="6053c-151">根據預設，NuGet 套件管理員 UI 只會顯示穩定版本，除非使用者選擇加入發行前套件；這使得發行前套件很適合用來進行有限使用者測試。</span><span class="sxs-lookup"><span data-stu-id="6053c-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="6053c-152">穩定套件無法相依於發行前套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="6053c-153">您必須使自己的套件成為發行前版本，或是相依於較舊的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="6053c-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="6053c-154">![NuGet 發行前套件相依性](./media/nuget/nuget-prerelease-package.png "NuGet 發行前套件相依性")</span><span class="sxs-lookup"><span data-stu-id="6053c-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="6053c-155">**✔️ 請務必**在進行測試、預覽或實驗時發佈發行前套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="6053c-156">**✔️ 請務必**在套件準備好時發佈穩定版本，使其他穩定套件可以參考它。</span><span class="sxs-lookup"><span data-stu-id="6053c-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="6053c-157">符號套件</span><span class="sxs-lookup"><span data-stu-id="6053c-157">Symbol packages</span></span>

<span data-ttu-id="6053c-158">符號檔 (`*.pdb`) 是由 .NET 編譯器連同組件一起產生。</span><span class="sxs-lookup"><span data-stu-id="6053c-158">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="6053c-159">符號檔會將執行位置對應至原始程式碼，使您可以在使用偵錯工具執行原始程式碼時逐步執行它。</span><span class="sxs-lookup"><span data-stu-id="6053c-159">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="6053c-160">NuGet 支援連同包含 .NET 組件的主要套件，一起產生包含符號檔的[個別符號套件](/nuget/create-packages/symbol-packages)。</span><span class="sxs-lookup"><span data-stu-id="6053c-160">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="6053c-161">符號套件的概念在於它們會被裝載在符號伺服器上，而且只會由 Visual Studio 之類的工具依需求下載。</span><span class="sxs-lookup"><span data-stu-id="6053c-161">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="6053c-162">目前適用於符號的主要公用主機 ([SymbolSource](http://www.symbolsource.org/) )並不支援由 SDK 樣式專案所建立的新[可攜式符號檔](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) \(英文\) (`*.pdb`)，因此符號套件的用處並不大。</span><span class="sxs-lookup"><span data-stu-id="6053c-162">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects, and symbol packages aren't useful.</span></span> <span data-ttu-id="6053c-163">在有適用於符號套件的建議主機之前，可以先將符號檔內嵌在主要 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="6053c-163">Until there is a recommended host for symbol packages, symbol files can be embedded in the main NuGet package.</span></span> <span data-ttu-id="6053c-164">如果您正在使用 SDK 樣式專案建置 NuGet 套件，您可以透過設定 `AllowedOutputExtensionsInPackageBuildOutputFolder` 屬性來內嵌符號檔：</span><span class="sxs-lookup"><span data-stu-id="6053c-164">If you are building your NuGet package using an SDK-style project you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span> 

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6053c-165">**✔️ 請考慮**將符號檔內嵌在主要 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="6053c-165">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

<span data-ttu-id="6053c-166">**❌ 請避免**建立包含符號檔的符號套件。</span><span class="sxs-lookup"><span data-stu-id="6053c-166">**❌ AVOID** creating a symbols package containing symbol files.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="6053c-167">[上一頁](./strong-naming.md)
[下一頁](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6053c-167">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
