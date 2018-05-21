---
title: .NET Core CLI 擴充性模型
description: 了解如何擴充命令列介面 (CLI) 工具。
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: 6cabd3959a29878788916ae26589be408c12e0ca
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="2301c-103">.NET Core CLI 工具擴充性模型</span><span class="sxs-lookup"><span data-stu-id="2301c-103">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="2301c-104">本文件涵蓋不同的方式可擴充 .NET Core 命令列介面 (CLI) 工具，並說明可驅動其中所有項目的案例。</span><span class="sxs-lookup"><span data-stu-id="2301c-104">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="2301c-105">您會看到如何使用這些工具，以及如何建置不同類型的工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="2301c-106">如何擴充 CLI 工具</span><span class="sxs-lookup"><span data-stu-id="2301c-106">How to extend CLI tools</span></span>
<span data-ttu-id="2301c-107">CLI 工具可以透過三種主要方式進行擴充：</span><span class="sxs-lookup"><span data-stu-id="2301c-107">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="2301c-108">透過個別專案的 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="2301c-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="2301c-109">個別專案工具都包含在專案內容內，但允許透過還原輕鬆地進行安裝。</span><span class="sxs-lookup"><span data-stu-id="2301c-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="2301c-110">透過具有自訂目標的 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="2301c-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="2301c-111">自訂目標可讓您輕鬆地透過自訂工作擴充建置程序。</span><span class="sxs-lookup"><span data-stu-id="2301c-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="2301c-112">透過系統的 PATH</span><span class="sxs-lookup"><span data-stu-id="2301c-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="2301c-113">PATH 工具適用於可在單一電腦上使用的一般跨專案工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="2301c-114">上述這三種擴充性機制都不是專用的。</span><span class="sxs-lookup"><span data-stu-id="2301c-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="2301c-115">您可以使用其中一個、全部或其組合。</span><span class="sxs-lookup"><span data-stu-id="2301c-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="2301c-116">選擇哪一個主要取決於您嘗試使用延伸模組達成的目標。</span><span class="sxs-lookup"><span data-stu-id="2301c-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="2301c-117">個別專案擴充性</span><span class="sxs-lookup"><span data-stu-id="2301c-117">Per-project based extensibility</span></span>
<span data-ttu-id="2301c-118">個別專案工具是以 NuGet 套件形式散發的[架構相依部署](../deploying/index.md#framework-dependent-deployments-fdd)。</span><span class="sxs-lookup"><span data-stu-id="2301c-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="2301c-119">工具只可用於參考它們以及還原它們之專案的內容中。</span><span class="sxs-lookup"><span data-stu-id="2301c-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="2301c-120">因為找不到命令，所以專案內容外部 (例如，包含專案的目錄外部) 的引動過程會失敗。</span><span class="sxs-lookup"><span data-stu-id="2301c-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="2301c-121">這些工具非常適合做為組建伺服器，因為不需要專案檔以外的任何項目。</span><span class="sxs-lookup"><span data-stu-id="2301c-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="2301c-122">建置流程會執行所建置專案的還原，並且可以使用這些工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="2301c-123">因為每個專案都只能以一種特定語言撰寫，所以語言專案 (例如 F#) 也在這個分類中。</span><span class="sxs-lookup"><span data-stu-id="2301c-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="2301c-124">最後，這個擴充性模型支援建立存取專案的已建置輸出所需的工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="2301c-125">例如，[ASP.NET](https://www.asp.net/) MVC 應用程式中的各種 Razor 檢視工具都會落入這個分類。</span><span class="sxs-lookup"><span data-stu-id="2301c-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="2301c-126">使用個別專案工具</span><span class="sxs-lookup"><span data-stu-id="2301c-126">Consuming per-project tools</span></span>
<span data-ttu-id="2301c-127">使用這些工具，需要您針對要使用的每個工具在專案檔中新增 `<DotNetCliToolReference>` 項目。</span><span class="sxs-lookup"><span data-stu-id="2301c-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="2301c-128">在 `<DotNetCliToolReference>` 項目內部，您會參考工具所在的套件，並指定您需要的版本。</span><span class="sxs-lookup"><span data-stu-id="2301c-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="2301c-129">執行 [`dotnet restore`](dotnet-restore.md) 之後，會還原工具和其相依性。</span><span class="sxs-lookup"><span data-stu-id="2301c-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="2301c-130">針對需要載入專案建置輸出來執行的工具，通常在專案檔中的一般相依性下方會列出另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="2301c-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="2301c-131">因為 CLI 使用 MSBuild 作為其建置引擎，所以建議您將工具的這些部分撰寫為自訂 MSBuild [目標](/visualstudio/msbuild/msbuild-targets)及[工作](/visualstudio/msbuild/msbuild-tasks)，這樣它們就可以參與整體建置程序。</span><span class="sxs-lookup"><span data-stu-id="2301c-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="2301c-132">此外，它們可以輕鬆取得透過建置所產生的任何與全部資料，例如輸出檔的位置、目前正在建置的組態等。這項資訊全部會變成一組可從任何目標讀取的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="2301c-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="2301c-133">您稍後會在此文件中看到如何使用 NuGet 新增自訂目標。</span><span class="sxs-lookup"><span data-stu-id="2301c-133">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="2301c-134">讓我們檢閱在簡單專案中新增僅限簡單工具的工具的範例。</span><span class="sxs-lookup"><span data-stu-id="2301c-134">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="2301c-135">假設有一個稱為 `dotnet-api-search` 的範例命令可讓您搜尋 NuGet 套件以尋找指定的 API，則以下是使用該工具的主控台應用程式專案檔：</span><span class="sxs-lookup"><span data-stu-id="2301c-135">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="2301c-136">`<DotNetCliToolReference>` 元素會以類似於 `<PackageReference>` 元素的方式結構化。</span><span class="sxs-lookup"><span data-stu-id="2301c-136">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="2301c-137">它需要包含可還原之工具及其版本之套件的套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="2301c-137">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="2301c-138">建置工具</span><span class="sxs-lookup"><span data-stu-id="2301c-138">Building tools</span></span>
<span data-ttu-id="2301c-139">如前所述，工具只是可攜式主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="2301c-139">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="2301c-140">建置工具的方式與建置任何其他主控台應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="2301c-140">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="2301c-141">在您建置它之後，請使用 [`dotnet pack`](dotnet-pack.md) 命令來建立包含您程式碼、其相依性相關資訊等的 NuGet 套件 (.nupkg 檔案)。</span><span class="sxs-lookup"><span data-stu-id="2301c-141">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="2301c-142">您可以提供任何套件名稱，但在應用程式內，實際工具二進位檔必須符合 `dotnet-<command>` 的慣例，`dotnet` 才能叫用它。</span><span class="sxs-lookup"><span data-stu-id="2301c-142">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="2301c-143">在 RC3 之前版本的 .NET Core 命令列工具中，`dotnet pack` 命令中的 Bug 導致無法使用該工具來將 `runtime.config.json` 封裝。</span><span class="sxs-lookup"><span data-stu-id="2301c-143">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="2301c-144">缺少該檔案會導致在執行階段發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2301c-144">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="2301c-145">如果您遇到這個問題，請務必更新至最新的工具，並再次嘗試 `dotnet pack`。</span><span class="sxs-lookup"><span data-stu-id="2301c-145">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="2301c-146">因為工具是可攜式應用程式，所以使用工具的使用者必須具有用來建置工具的 .NET Core 程式庫版本，才能執行工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-146">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="2301c-147">工具所使用以及 .NET Core 程式庫內未包含的任何其他相依性都會進行還原並放到 NuGet 快取中。</span><span class="sxs-lookup"><span data-stu-id="2301c-147">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="2301c-148">因此，會使用 .NET Core 程式庫中的組件以及 NuGet 快取中的組件來執行整個工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-148">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="2301c-149">這類工具的相依性圖形必須與使用這些工具之專案的相依性圖形完全分開。</span><span class="sxs-lookup"><span data-stu-id="2301c-149">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="2301c-150">還原程序會先還原專案的相依性，接著還原每個工具及其相依性。</span><span class="sxs-lookup"><span data-stu-id="2301c-150">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="2301c-151">您可以在 [.NET Core CLI 存放庫](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)中找到更多範例和這類不同的組合。</span><span class="sxs-lookup"><span data-stu-id="2301c-151">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="2301c-152">您也可以在相同的存放庫中查看[所使用工具的實作](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages)。</span><span class="sxs-lookup"><span data-stu-id="2301c-152">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="2301c-153">自訂目標</span><span class="sxs-lookup"><span data-stu-id="2301c-153">Custom targets</span></span>
<span data-ttu-id="2301c-154">NuGet 可以[封裝自訂 MSBuild 目標及屬性檔案](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package)。</span><span class="sxs-lookup"><span data-stu-id="2301c-154">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="2301c-155">隨著 .NET Core CLI 改為使用 MSBuild，相同的擴充機制現在也適用於 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="2301c-155">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="2301c-156">如果您想要擴充建置程序，或想要在建置程序中存取任何成品 (例如產生的檔案或檢查叫用建置的組態等)，可以使用這種類型的擴充性。</span><span class="sxs-lookup"><span data-stu-id="2301c-156">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="2301c-157">在下列範例中，您可以使用 `csproj` 語法看到目標的專案檔。</span><span class="sxs-lookup"><span data-stu-id="2301c-157">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="2301c-158">這會指示 [`dotnet pack`](dotnet-pack.md) 命令要封裝的內容，並將目標檔案及組件放入套件內的 *build* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2301c-158">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="2301c-159">請注意，`<ItemGroup>` 項目的 `Label` 屬性設定為 `dotnet pack instructions`，並具有其下定義的 [目標]。</span><span class="sxs-lookup"><span data-stu-id="2301c-159">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="2301c-160">取用自訂目標的方式是提供 `<PackageReference>`，它必須指向套件以及其在要擴充之專案中的版本。</span><span class="sxs-lookup"><span data-stu-id="2301c-160">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="2301c-161">與其他工具不同，自訂目標套件會被包含到取用自訂目標之專案的相依性閉包 (Closure) 中。</span><span class="sxs-lookup"><span data-stu-id="2301c-161">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="2301c-162">使用自訂目標取決於您的設定方式。</span><span class="sxs-lookup"><span data-stu-id="2301c-162">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="2301c-163">因為它是 MSBuild 目標，所以可以依存在給定的目標上、在另一個目標之後執行，也可以使用 `dotnet msbuild /t:<target-name>` 命令手動叫用。</span><span class="sxs-lookup"><span data-stu-id="2301c-163">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild /t:<target-name>` command.</span></span>

<span data-ttu-id="2301c-164">不過，如果您要為使用者提供更好的使用者體驗，則可以結合個別專案工具和自訂目標。</span><span class="sxs-lookup"><span data-stu-id="2301c-164">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="2301c-165">在此案例中，個別專案工具基本上會只接受任何需要的參數，且會將參數轉譯為將執行目標的必要 [`dotnet msbuild`](dotnet-msbuild.md) 引動過程。</span><span class="sxs-lookup"><span data-stu-id="2301c-165">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="2301c-166">您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。</span><span class="sxs-lookup"><span data-stu-id="2301c-166">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="2301c-167">PATH 擴充性</span><span class="sxs-lookup"><span data-stu-id="2301c-167">PATH-based extensibility</span></span>
<span data-ttu-id="2301c-168">PATH 擴充性通常用於開發電腦，而在開發電腦中，您需要有概念上涵蓋多個單一專案的工具。</span><span class="sxs-lookup"><span data-stu-id="2301c-168">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="2301c-169">這個延伸模組機制的主要缺點是繫結至工具所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="2301c-169">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="2301c-170">如果您需要在另一部電腦上使用它，則必須部署它。</span><span class="sxs-lookup"><span data-stu-id="2301c-170">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="2301c-171">這種模式的 CLI 工具組擴充性十分簡單。</span><span class="sxs-lookup"><span data-stu-id="2301c-171">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="2301c-172">如 [.NET Core CLI 概觀](index.md)中所涵蓋，`dotnet` 驅動程式可以執行任何在 `dotnet-<command>` 慣例後面命名的命令。</span><span class="sxs-lookup"><span data-stu-id="2301c-172">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="2301c-173">預設解析邏輯會先探查數個位置，最後回復到系統路徑。</span><span class="sxs-lookup"><span data-stu-id="2301c-173">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="2301c-174">如果要求的命令存在於系統 PATH 中，而且是可叫用的二進位檔，`dotnet` 驅動程式將會叫用它。</span><span class="sxs-lookup"><span data-stu-id="2301c-174">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="2301c-175">檔案必須是可執行檔。</span><span class="sxs-lookup"><span data-stu-id="2301c-175">The file must be executable.</span></span> <span data-ttu-id="2301c-176">在 Unix 系統上，這表示任何透過 `chmod +x` 設定執行位元的項目。</span><span class="sxs-lookup"><span data-stu-id="2301c-176">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="2301c-177">在 Windows 中，您可以使用 *cmd* 檔案。</span><span class="sxs-lookup"><span data-stu-id="2301c-177">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="2301c-178">讓我們查看十分簡單的 "Hello World" 工具的實作。</span><span class="sxs-lookup"><span data-stu-id="2301c-178">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="2301c-179">我們將在 Windows 上使用 `bash` 及 `cmd`。</span><span class="sxs-lookup"><span data-stu-id="2301c-179">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="2301c-180">下列命令只會將 "Hello World" 回應到主控台。</span><span class="sxs-lookup"><span data-stu-id="2301c-180">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="2301c-181">在 macOS 上，我們可以將這個指令碼儲存為 `dotnet-hello`，並使用 `chmod +x dotnet-hello` 設定其可執行位元。</span><span class="sxs-lookup"><span data-stu-id="2301c-181">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="2301c-182">我們接著可以使用 `ln -s <full_path>/dotnet-hello /usr/local/bin/` 命令，以在 `/usr/local/bin` 中建立其符號連結。</span><span class="sxs-lookup"><span data-stu-id="2301c-182">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="2301c-183">這可能會使用 `dotnet hello` 語法來叫用此命令。</span><span class="sxs-lookup"><span data-stu-id="2301c-183">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="2301c-184">在 Windows 中，可以將這個指令碼儲存為 `dotnet-hello.cmd`，並將它放在系統路徑中的位置 (也可以將它新增至已在路徑中的資料夾)。</span><span class="sxs-lookup"><span data-stu-id="2301c-184">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="2301c-185">在此之後，您只要使用 `dotnet hello`，就能執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="2301c-185">After this, you can just use `dotnet hello` to run this example.</span></span>
