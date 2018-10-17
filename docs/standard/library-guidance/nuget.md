---
title: NuGet 和.NET 程式庫
description: 最佳作法建議封裝使用 NuGet 的.NET 程式庫。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: d0ea462a7f52dd9a6b2f14be9ed5770160bf66b1
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374485"
---
# <a name="nuget"></a><span data-ttu-id="89be6-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="89be6-103">NuGet</span></span>

<span data-ttu-id="89be6-104">NuGet 是.NET 生態系統的套件管理員，而且是主要的方式開發人員探索，並取得.NET 開放原始碼程式庫。</span><span class="sxs-lookup"><span data-stu-id="89be6-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="89be6-105">[NuGet.org](https://www.nuget.org/)，針對裝載 NuGet 套件，Microsoft 所提供的免費服務是公用的 NuGet 套件的主要主機，但您可以發行至自訂的 NuGet 服務，例如[MyGet](https://www.myget.org/)和[Azure 構件](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="89be6-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="89be6-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="89be6-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="89be6-107">建立 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="89be6-107">Create a NuGet package</span></span>

<span data-ttu-id="89be6-108">NuGet 套件 (`*.nupkg`) 是包含.NET 組件和相關聯的中繼資料的 zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="89be6-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="89be6-109">有兩種主要的方式，來建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="89be6-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="89be6-110">更新與建議方式是建立封裝從 SDK 樣式專案 (專案檔，其內容開頭`<Project Sdk="Microsoft.NET.Sdk">`)。</span><span class="sxs-lookup"><span data-stu-id="89be6-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="89be6-111">組件和目標會自動加入至封裝和剩餘的中繼資料新增至 MSBuild 檔案，例如封裝名稱和版本號碼。</span><span class="sxs-lookup"><span data-stu-id="89be6-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="89be6-112">在以編譯[ `dotnet pack` ](../../core/tools/dotnet-pack.md)命令輸出`*.nupkg`檔案而不是組件。</span><span class="sxs-lookup"><span data-stu-id="89be6-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="89be6-113">建立 NuGet 套件的較舊的方法是使用`*.nuspec`檔案和`nuget.exe`命令列工具。</span><span class="sxs-lookup"><span data-stu-id="89be6-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="89be6-114">Nuspec 檔案可讓您全權掌控，但您必須仔細地指定要包含在最終的 NuGet 套件中哪些組件和目標。</span><span class="sxs-lookup"><span data-stu-id="89be6-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="89be6-115">很容易發生錯誤或其他人進行變更時更新 nuspec 忘了。</span><span class="sxs-lookup"><span data-stu-id="89be6-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="89be6-116">Nuspec 的優點是您可以使用它建立 NuGet 套件不支援的 SDK 樣式專案檔案的架構。</span><span class="sxs-lookup"><span data-stu-id="89be6-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="89be6-117">**請考慮 ✔️**建立 NuGet 套件使用 SDK 樣式專案檔。</span><span class="sxs-lookup"><span data-stu-id="89be6-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="89be6-118">**請考慮 ✔️**設定 SourceLink 將原始檔控制中繼資料新增至您的組件和 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="89be6-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="89be6-119">封裝相依性</span><span class="sxs-lookup"><span data-stu-id="89be6-119">Package dependencies</span></span>

<span data-ttu-id="89be6-120">NuGet 套件相依性會詳細說明[相依性](./dependencies.md)文章。</span><span class="sxs-lookup"><span data-stu-id="89be6-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="89be6-121">重要的 NuGet 套件中繼資料</span><span class="sxs-lookup"><span data-stu-id="89be6-121">Important NuGet package metadata</span></span>

<span data-ttu-id="89be6-122">NuGet 套件支援許多[中繼資料屬性](/nuget/reference/nuspec)。</span><span class="sxs-lookup"><span data-stu-id="89be6-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="89be6-123">下表包含每個開放原始碼專案應該提供的核心中繼資料：</span><span class="sxs-lookup"><span data-stu-id="89be6-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="89be6-124">MSBuild 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="89be6-124">MSBuild Property name</span></span>              | <span data-ttu-id="89be6-125">Nuspec 名稱</span><span class="sxs-lookup"><span data-stu-id="89be6-125">Nuspec name</span></span>              | <span data-ttu-id="89be6-126">描述</span><span class="sxs-lookup"><span data-stu-id="89be6-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="89be6-127">封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="89be6-127">The package identifier.</span></span> <span data-ttu-id="89be6-128">可以保留與識別項的前置詞，符合時才[準則](/nuget/reference/id-prefix-reservation)。</span><span class="sxs-lookup"><span data-stu-id="89be6-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="89be6-129">NuGet 封裝版本。</span><span class="sxs-lookup"><span data-stu-id="89be6-129">NuGet package version.</span></span> <span data-ttu-id="89be6-130">如需詳細資訊，請參閱 < [NuGet 套件版本](./versioning.md#nuget-package-version)。</span><span class="sxs-lookup"><span data-stu-id="89be6-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="89be6-131">封裝的易記標題。</span><span class="sxs-lookup"><span data-stu-id="89be6-131">A human-friendly title of the package.</span></span> <span data-ttu-id="89be6-132">它會預設為`PackageId`。</span><span class="sxs-lookup"><span data-stu-id="89be6-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="89be6-133">UI 中顯示套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="89be6-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="89be6-134">套件作者，比對與 nuget.org 上的設定檔名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="89be6-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="89be6-135">以空格分隔的標記和描述套件的關鍵字清單。</span><span class="sxs-lookup"><span data-stu-id="89be6-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="89be6-136">搜尋套件時，會使用標記。</span><span class="sxs-lookup"><span data-stu-id="89be6-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="89be6-137">做為封裝圖示影像 URL。</span><span class="sxs-lookup"><span data-stu-id="89be6-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="89be6-138">URL 應為 HTTPS 和映像應該是 64 x 64，而且有透明背景。</span><span class="sxs-lookup"><span data-stu-id="89be6-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="89be6-139">專案首頁或來源存放庫 URL。</span><span class="sxs-lookup"><span data-stu-id="89be6-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="89be6-140">專案的授權 URL。</span><span class="sxs-lookup"><span data-stu-id="89be6-140">A URL to the project license.</span></span> <span data-ttu-id="89be6-141">可以是 URL`LICENSE`原始檔控制中的檔案。</span><span class="sxs-lookup"><span data-stu-id="89be6-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="89be6-142">**請考慮 ✔️**選擇 NuGet 套件名稱以符合 NuGet 的前置詞保留的前置詞[準則](/nuget/reference/id-prefix-reservation)。</span><span class="sxs-lookup"><span data-stu-id="89be6-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="89be6-143">**請考慮 ✔️**使用`LICENSE`做為原始檔控制中的檔案`LicenseUrl`。</span><span class="sxs-lookup"><span data-stu-id="89be6-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="89be6-144">例如， [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md)。</span><span class="sxs-lookup"><span data-stu-id="89be6-144">For example, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89be6-145">專案沒有授權的預設值為[獨佔 copyright](https://choosealicense.com/no-permission/)，導致其他人使用。</span><span class="sxs-lookup"><span data-stu-id="89be6-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="89be6-146">**請勿 ✔️**使用 HTTPS href 套件圖示。</span><span class="sxs-lookup"><span data-stu-id="89be6-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="89be6-147">NuGet.org 這類的站台都執行以啟用 HTTPS，並顯示非 HTTPS 映像將會建立混合內容警告。</span><span class="sxs-lookup"><span data-stu-id="89be6-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="89be6-148">**請勿 ✔️**使用封裝圖示映像，且會 64 x 64 個獲得最佳的結果是透明的背景。</span><span class="sxs-lookup"><span data-stu-id="89be6-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="89be6-149">發行前套件</span><span class="sxs-lookup"><span data-stu-id="89be6-149">Pre-release packages</span></span>

<span data-ttu-id="89be6-150">NuGet 套件版本尾碼會被視為[發行前版本](/nuget/create-packages/prerelease-packages)。</span><span class="sxs-lookup"><span data-stu-id="89be6-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="89be6-151">根據預設，NuGet 套件管理員 UI 會顯示穩定版本，除非使用者選擇單元來發行前套件，讓發行前版本套件適用於有限的使用者測試。</span><span class="sxs-lookup"><span data-stu-id="89be6-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="89be6-152">穩定的套件無法取決於發行前版本套件中。</span><span class="sxs-lookup"><span data-stu-id="89be6-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="89be6-153">您必須讓您自己的套件發行前版本或較舊的穩定版本而定。</span><span class="sxs-lookup"><span data-stu-id="89be6-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="89be6-154">![NuGet 發行前版本套件相依性](./media/nuget/nuget-prerelease-package.png "NuGet 發行前版本套件相依性")</span><span class="sxs-lookup"><span data-stu-id="89be6-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="89be6-155">**請勿 ✔️**發行的發行前版本套件時測試、 預覽或實驗。</span><span class="sxs-lookup"><span data-stu-id="89be6-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="89be6-156">**請勿 ✔️**發佈為穩定套件，其已準備好讓其他的穩定套件可以參考它時。</span><span class="sxs-lookup"><span data-stu-id="89be6-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="89be6-157">符號套件</span><span class="sxs-lookup"><span data-stu-id="89be6-157">Symbol packages</span></span>

<span data-ttu-id="89be6-158">NuGet 支援[產生不同的符號套件](/nuget/create-packages/symbol-packages)包含偵錯以及包含.NET 組件的主要封裝的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="89be6-158">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing debug PDB files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="89be6-159">它們裝載在符號伺服器和，才會隨 Visual Studio 等工具下載符號套件的概念。</span><span class="sxs-lookup"><span data-stu-id="89be6-159">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="89be6-160">目前的主要公用主機符號- [SymbolSource](http://www.symbolsource.org/) -不支援建立可攜式 Pdb 的 SDK 樣式專案和符號套件不適用。</span><span class="sxs-lookup"><span data-stu-id="89be6-160">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the portable PDBs created by SDK-style projects and symbol packages aren't useful.</span></span>

<span data-ttu-id="89be6-161">**請考慮 ✔️**將 Pdb 內嵌於主要的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="89be6-161">**✔️ CONSIDER** embedding PDBs in the main NuGet package.</span></span>

<span data-ttu-id="89be6-162">**請避免 ❌**建立包含 Pdb 符號套件。</span><span class="sxs-lookup"><span data-stu-id="89be6-162">**❌ AVOID** creating a symbols package containing PDBs.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="89be6-163">[上一頁](./strong-naming.md)
[下一頁](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="89be6-163">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
