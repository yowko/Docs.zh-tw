---
title: NuGet 與 .NET 程式庫
description: 針對 .NET 程式庫搭配 NuGet 進行封裝的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 6c3c7feb95f0ebe6b348f42cdd243ce1d14b9c50
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333417"
---
# <a name="nuget"></a><span data-ttu-id="547c6-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="547c6-103">NuGet</span></span>

<span data-ttu-id="547c6-104">NuGet 是適用於 .NET 生態系統的套件管理員，也是開發人員探索並取得 .NET 開放原始碼程式庫的主要方式。</span><span class="sxs-lookup"><span data-stu-id="547c6-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="547c6-105">[NuGet.org](https://www.nuget.org/) \(英文\) 是 Microsoft 提供用來裝載 NuGet 套件的免費服務，它是公用 NuGet 套件的主要主機；但您也可以發佈至自訂的 NuGet 服務，例如 [MyGet](https://www.myget.org/) \(英文\) 與 [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/)。</span><span class="sxs-lookup"><span data-stu-id="547c6-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="547c6-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="547c6-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="547c6-107">建立 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="547c6-107">Create a NuGet package</span></span>

<span data-ttu-id="547c6-108">NuGet 套件 (`*.nupkg`) 是包含 .NET 組件與相關聯中繼資料的 Zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="547c6-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="547c6-109">有兩種主要的方式可用來建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="547c6-110">較新且建議的方式，是從 SDK 樣式專案 (內容以 `<Project Sdk="Microsoft.NET.Sdk">` 作為開頭的專案) 建立套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="547c6-111">系統會自動將組件與目標新增到套件中，並將剩餘的中繼資料新增到 MSBuild 檔案，例如套件名稱與版本號碼。</span><span class="sxs-lookup"><span data-stu-id="547c6-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="547c6-112">搭配 [`dotnet pack`](../../core/tools/dotnet-pack.md) 命令進行編譯將會輸出 `*.nupkg` 檔案，而非組件。</span><span class="sxs-lookup"><span data-stu-id="547c6-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="547c6-113">較舊的 NuGet 套件建立方式，是使用 `*.nuspec` 檔案與 `nuget.exe` 命令列工具來建立。</span><span class="sxs-lookup"><span data-stu-id="547c6-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="547c6-114">nuspec 檔案可讓您做出大幅度的控制，但您必須仔細地指定要在最終的 NuGet 套件中包含哪些組件與目標。</span><span class="sxs-lookup"><span data-stu-id="547c6-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="547c6-115">這是一件很容易出錯的工作，也很容易在未來做出變更後忘記更新 nuspec 檔案。</span><span class="sxs-lookup"><span data-stu-id="547c6-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="547c6-116">nuspec 的優點在於您可以用它來針對尚未支援 SDK 樣式專案檔的架構建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="547c6-117">**✔️ 請考慮**使用 SDK 樣式專案檔來建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="547c6-118">套件相依性</span><span class="sxs-lookup"><span data-stu-id="547c6-118">Package dependencies</span></span>

<span data-ttu-id="547c6-119">NuGet 套件相依性已詳述於[相依性](./dependencies.md)一文中。</span><span class="sxs-lookup"><span data-stu-id="547c6-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="547c6-120">重要的 NuGet 套件中繼資料</span><span class="sxs-lookup"><span data-stu-id="547c6-120">Important NuGet package metadata</span></span>

<span data-ttu-id="547c6-121">NuGet 套件能支援許多[中繼資料屬性](/nuget/reference/nuspec)。</span><span class="sxs-lookup"><span data-stu-id="547c6-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="547c6-122">下表包含 NuGet.org 上所有套件都應提供的核心中繼資料：</span><span class="sxs-lookup"><span data-stu-id="547c6-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="547c6-123">MSBuild 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="547c6-123">MSBuild Property name</span></span>              | <span data-ttu-id="547c6-124">Nuspec 名稱</span><span class="sxs-lookup"><span data-stu-id="547c6-124">Nuspec name</span></span>              | <span data-ttu-id="547c6-125">說明</span><span class="sxs-lookup"><span data-stu-id="547c6-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="547c6-126">套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="547c6-126">The package identifier.</span></span> <span data-ttu-id="547c6-127">如果來自識別碼的前置詞符合[準則](/nuget/reference/id-prefix-reservation)，便可以對它進行保留。</span><span class="sxs-lookup"><span data-stu-id="547c6-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="547c6-128">NuGet 套件版本。</span><span class="sxs-lookup"><span data-stu-id="547c6-128">NuGet package version.</span></span> <span data-ttu-id="547c6-129">如需詳細資訊，請參閱 [NuGet 套件版本](./versioning.md#nuget-package-version)。</span><span class="sxs-lookup"><span data-stu-id="547c6-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="547c6-130">人類容易記住的套件標題。</span><span class="sxs-lookup"><span data-stu-id="547c6-130">A human-friendly title of the package.</span></span> <span data-ttu-id="547c6-131">預設值為 `PackageId`。</span><span class="sxs-lookup"><span data-stu-id="547c6-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="547c6-132">在 UI 中顯示的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="547c6-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="547c6-133">以逗號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。</span><span class="sxs-lookup"><span data-stu-id="547c6-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="547c6-134">以空格分隔的標記與關鍵字清單，能描述套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="547c6-135">標記會在搜尋套件時使用。</span><span class="sxs-lookup"><span data-stu-id="547c6-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="547c6-136">要作為套件圖示使用之影像的 URL。</span><span class="sxs-lookup"><span data-stu-id="547c6-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="547c6-137">URL 應為 HTTPS 且影像大小應為 64x64 並具有透明背景。</span><span class="sxs-lookup"><span data-stu-id="547c6-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="547c6-138">專案首頁或來源存放庫的 URL。</span><span class="sxs-lookup"><span data-stu-id="547c6-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="547c6-139">專案授權的 [SPDX 識別碼](https://spdx.org/licenses/)。</span><span class="sxs-lookup"><span data-stu-id="547c6-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="547c6-140">只有 OSI 和 FSF 核准的授權可以使用識別碼。</span><span class="sxs-lookup"><span data-stu-id="547c6-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="547c6-141">其他授權應該使用 `PackageLicenseFile`。</span><span class="sxs-lookup"><span data-stu-id="547c6-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="547c6-142">閱讀更多 [`license` 中繼資料](/nuget/reference/nuspec#license)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="547c6-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="547c6-143">沒有授權的專案預設會具有[專屬著作權](https://choosealicense.com/no-permission/)，這會使其他人無法合法使用它。</span><span class="sxs-lookup"><span data-stu-id="547c6-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="547c6-144">**✔️ 請考慮**選擇具有符合 NuGet 的前置詞保留[準則](/nuget/reference/id-prefix-reservation)之前置詞的 NuGet 套件名稱。</span><span class="sxs-lookup"><span data-stu-id="547c6-144">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="547c6-145">**✔️ 請務必**為您的套件圖示使用 HTTPS href。</span><span class="sxs-lookup"><span data-stu-id="547c6-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="547c6-146">NuGet.org 等網站會在啟用 HTTPS 的情況下執行，因此顯示非 HTTPS 影像將會產生混合內容警告。</span><span class="sxs-lookup"><span data-stu-id="547c6-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="547c6-147">**✔️ 請務必**使用大小為 64x64 且具有透明背景的套件圖示影像，以取得最佳檢視效果。</span><span class="sxs-lookup"><span data-stu-id="547c6-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="547c6-148">**✔️ 請考慮**設定 [SourceLink](./sourcelink.md) 以將原始程式碼控制中繼資料新增到您的組件與 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-148">**✔️ CONSIDER** setting up [SourceLink](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="547c6-149">SourceLink 會自動將 `RepositoryUrl` 和 `RepositoryType` 中繼資料新增到 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-149">SourceLink automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="547c6-150">SourceLink 也會新增套件建置所根據確切原始碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="547c6-150">SourceLink also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="547c6-151">例如，從 Git 存放庫建立的套件將會新增認可雜湊作為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="547c6-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="547c6-152">發行前套件</span><span class="sxs-lookup"><span data-stu-id="547c6-152">Pre-release packages</span></span>

<span data-ttu-id="547c6-153">具有版本尾碼的 NuGet 套件會被系統視為[發行前版本](/nuget/create-packages/prerelease-packages)。</span><span class="sxs-lookup"><span data-stu-id="547c6-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="547c6-154">根據預設，NuGet 套件管理員 UI 只會顯示穩定版本，除非使用者選擇加入發行前套件；這使得發行前套件很適合用來進行有限使用者測試。</span><span class="sxs-lookup"><span data-stu-id="547c6-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="547c6-155">穩定套件無法相依於發行前套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="547c6-156">您必須使自己的套件成為發行前版本，或是相依於較舊的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="547c6-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="547c6-157">![NuGet 發行前套件相依性](./media/nuget/nuget-prerelease-package.png "NuGet 發行前套件相依性")</span><span class="sxs-lookup"><span data-stu-id="547c6-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="547c6-158">**✔️ 請務必**在進行測試、預覽或實驗時發佈發行前套件。</span><span class="sxs-lookup"><span data-stu-id="547c6-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="547c6-159">**✔️ 請務必**在套件準備好時發佈穩定版本，使其他穩定套件可以參考它。</span><span class="sxs-lookup"><span data-stu-id="547c6-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="547c6-160">符號套件</span><span class="sxs-lookup"><span data-stu-id="547c6-160">Symbol packages</span></span>

<span data-ttu-id="547c6-161">符號檔 (`*.pdb`) 是由 .NET 編譯器連同組件一起產生。</span><span class="sxs-lookup"><span data-stu-id="547c6-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="547c6-162">符號檔會將執行位置對應至原始程式碼，使您可以在使用偵錯工具執行原始程式碼時逐步執行它。</span><span class="sxs-lookup"><span data-stu-id="547c6-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="547c6-163">NuGet 支援連同包含 .NET 組件的主要套件，一起[產生包含符號檔的個別符號套件 (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg)。</span><span class="sxs-lookup"><span data-stu-id="547c6-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="547c6-164">符號套件的概念在於它們會被裝載在符號伺服器上，而且只會由 Visual Studio 之類的工具依需求下載。</span><span class="sxs-lookup"><span data-stu-id="547c6-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="547c6-165">NuGet.org 裝載自己的[符號伺服器存放庫](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server)。</span><span class="sxs-lookup"><span data-stu-id="547c6-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="547c6-166">開發人員可以使用發佈至 NuGet.org 符號伺服器的符號，方法是將 `https://symbols.nuget.org/download/symbols` 新增至其[在 Visual Studio 中的符號來源](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)。</span><span class="sxs-lookup"><span data-stu-id="547c6-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="547c6-167">NuGet.org 符號伺服器只支援 SDK 樣式專案所建立的新[可攜式符號檔](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)(`*.pdb`)。</span><span class="sxs-lookup"><span data-stu-id="547c6-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="547c6-168">若要在偵錯 .NET 程式庫時使用 NuGet.org 符號伺服器，開發人員必須擁有 Visual Studio 2017 15.9 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="547c6-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 15.9 or later.</span></span>

<span data-ttu-id="547c6-169">建立符號套件的替代方案是在主要的 NuGet 套件中內嵌符號檔。</span><span class="sxs-lookup"><span data-stu-id="547c6-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="547c6-170">主要的 NuGet 套件會較大，但內嵌的符號檔表示開發人員不需要設定 NuGet.org 符號伺服器。</span><span class="sxs-lookup"><span data-stu-id="547c6-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="547c6-171">如果您正在使用 SDK 樣式專案建置 NuGet 套件，您可以透過設定 `AllowedOutputExtensionsInPackageBuildOutputFolder` 屬性來內嵌符號檔：</span><span class="sxs-lookup"><span data-stu-id="547c6-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="547c6-172">**✔️ 請考慮**將符號檔內嵌在主要 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="547c6-172">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

> <span data-ttu-id="547c6-173">在主要的 NuGet 套件內嵌符號檔讓開發人員有較佳的預設偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="547c6-173">Embedding symbol files in the main NuGet package gives developers a better debugging experience by default.</span></span> <span data-ttu-id="547c6-174">他們不需要在其 IDE 中尋找並設定 NuGet 符號伺服器即可取得符號檔。</span><span class="sxs-lookup"><span data-stu-id="547c6-174">They don't need to find and configure the NuGet symbol server in their IDE to get symbol files.</span></span>
>
> <span data-ttu-id="547c6-175">內嵌符號檔的缺點是它們會讓使用 SDK 樣式專案編譯的 .NET 程式庫套件大小增加約 30%。</span><span class="sxs-lookup"><span data-stu-id="547c6-175">The downside to embedded symbol files is they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="547c6-176">如果套件大小是個問題，您應該改為將符號發佈在符號套件中。</span><span class="sxs-lookup"><span data-stu-id="547c6-176">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="547c6-177">[上一頁](strong-naming.md)
>[下一頁](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="547c6-177">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
