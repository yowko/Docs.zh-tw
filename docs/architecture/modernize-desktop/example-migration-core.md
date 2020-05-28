---
title: 移轉至 .NET Core 3.1 的範例
description: 顯示如何將以 .NET Framework 為目標的範例應用程式遷移至 .NET Core 3.1。
ms.date: 05/12/2020
ms.openlocfilehash: 5e8b1219cf4bd89ada5b71a60ef27eaabb94997c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144267"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="b93a4-103">移轉至 .NET Core 3.1 的範例</span><span class="sxs-lookup"><span data-stu-id="b93a4-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="b93a4-104">在本章中，我們會提供實用的指導方針，協助您將現有的應用程式從 .NET Framework 遷移至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="b93a4-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="b93a4-105">我們提供了結構良好的程式，您可以遵循並在每個步驟上考慮最重要的事項。</span><span class="sxs-lookup"><span data-stu-id="b93a4-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="b93a4-106">接著，我們會記錄範例傳統型應用程式的逐步執行步驟，從 WinForms 和 WPF 版本皆適用。</span><span class="sxs-lookup"><span data-stu-id="b93a4-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="b93a4-107">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="b93a4-107">Migration process overview</span></span>

<span data-ttu-id="b93a4-108">遷移套裝程式含四個順序步驟：</span><span class="sxs-lookup"><span data-stu-id="b93a4-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="b93a4-109">**準備**：瞭解專案必須具備哪些相依性，才能掌握未來的概念。</span><span class="sxs-lookup"><span data-stu-id="b93a4-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="b93a4-110">在此步驟中，您會將目前的專案變成可簡化遷移啟動點的狀態。</span><span class="sxs-lookup"><span data-stu-id="b93a4-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="b93a4-111">**遷移專案檔案：** .net Core 專案使用新的 SDK 樣式專案格式。</span><span class="sxs-lookup"><span data-stu-id="b93a4-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="b93a4-112">請使用此格式建立新的專案檔，或更新您必須使用 SDK 樣式的專案檔。</span><span class="sxs-lookup"><span data-stu-id="b93a4-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="b93a4-113">**修正程式碼和組建：** 在 .NET Core 中建立程式碼，以解決 .NET Framework 和 .NET Core 之間的 API 層級差異。</span><span class="sxs-lookup"><span data-stu-id="b93a4-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="b93a4-114">如有需要，請將協力廠商套件更新為支援 .NET Core 的封裝。</span><span class="sxs-lookup"><span data-stu-id="b93a4-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="b93a4-115">**執行和測試：** 在執行時間之前，可能會有不會顯示的差異。</span><span class="sxs-lookup"><span data-stu-id="b93a4-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="b93a4-116">因此，別忘了執行應用程式，並測試所有專案是否如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="b93a4-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="b93a4-117">準備</span><span class="sxs-lookup"><span data-stu-id="b93a4-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="b93a4-118">遷移封裝 .config 檔案</span><span class="sxs-lookup"><span data-stu-id="b93a4-118">Migrate packages.config file</span></span>

<span data-ttu-id="b93a4-119">在 .NET Framework 應用程式中，所有對外部封裝的參考都會在*封裝 .config*檔案中宣告。</span><span class="sxs-lookup"><span data-stu-id="b93a4-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="b93a4-120">在 .NET Core 中，不再需要使用*封裝 .config*檔案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="b93a4-121">相反地，請使用專案檔中的[PackageReference](../../core/project-sdk/msbuild-props.md#packagereference)屬性，來指定應用程式的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="b93a4-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="b93a4-122">因此，您必須從一種格式轉換成另一種格式。</span><span class="sxs-lookup"><span data-stu-id="b93a4-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="b93a4-123">您可以手動進行更新，取得包含在*封裝 .config*檔案中的相依性，並將其遷移至具有格式的專案檔 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="b93a4-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="b93a4-124">或者，您可以讓 Visual Studio 為您執行工作：以滑鼠右鍵按一下*封裝 .config*檔案，然後選取 [將**PackageReference 遷移至**] 選項。</span><span class="sxs-lookup"><span data-stu-id="b93a4-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="b93a4-125">確認 .NET Core 中的每項相依性相容性</span><span class="sxs-lookup"><span data-stu-id="b93a4-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="b93a4-126">遷移套件參考之後，您必須檢查每個參考的相容性。</span><span class="sxs-lookup"><span data-stu-id="b93a4-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="b93a4-127">您可以探索應用程式在[nuget.org](https://www.nuget.org/)上使用的每個 NuGet 套件的相依性。如果封裝有 .NET Standard 相依性，則它會在 .NET Core 上使用，因為 .NET Core 3.1[支援](../../standard/net-standard.md#net-implementation-support)所有版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="b93a4-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="b93a4-128">下圖顯示封裝的相依性 `Castle.Windsor` ：</span><span class="sxs-lookup"><span data-stu-id="b93a4-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Castle Windsor 套件的 NuGet 相依性螢幕擷取畫面](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="b93a4-130">若要檢查套件相容性，您可以使用工具 <https://fuget.org> 來提供版本和相依性的更詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b93a4-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="b93a4-131">可能是因為專案參考了不支援 .NET Core 的舊版套件，但您可能會發現支援它的較新版本。</span><span class="sxs-lookup"><span data-stu-id="b93a4-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="b93a4-132">因此，將套件更新為較新版本通常是很好的建議。</span><span class="sxs-lookup"><span data-stu-id="b93a4-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="b93a4-133">不過，您應該考慮更新封裝版本可能會引進一些重大變更，強制您更新程式碼。</span><span class="sxs-lookup"><span data-stu-id="b93a4-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="b93a4-134">如果找不到相容的版本，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="b93a4-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="b93a4-135">如果您因為這些重大變更而不想更新套件的版本，該怎麼做？</span><span class="sxs-lookup"><span data-stu-id="b93a4-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="b93a4-136">別擔心，因為可能會相依于 .NET Core 應用程式中 .NET Framework 的封裝。</span><span class="sxs-lookup"><span data-stu-id="b93a4-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="b93a4-137">別忘了測試，因為如果外部封裝呼叫的 API 無法在 .NET Core 上使用，它可能會造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="b93a4-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="b93a4-138">當您使用的舊套件不會更新，而且您可以直接將其重新置放至 .NET Core 上的工作時，這非常適合。</span><span class="sxs-lookup"><span data-stu-id="b93a4-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="b93a4-139">檢查 API 相容性</span><span class="sxs-lookup"><span data-stu-id="b93a4-139">Check for API compatibility</span></span>

<span data-ttu-id="b93a4-140">由於 .NET Framework 和 .NET Core 中的 API 介面很類似，但並不完全相同，因此您必須檢查哪些 Api 可在 .NET Core 上使用，哪些則不是。</span><span class="sxs-lookup"><span data-stu-id="b93a4-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="b93a4-141">您可以使用 .NET 可攜性分析器工具來呈現 .NET Core 上不存在的 Api。</span><span class="sxs-lookup"><span data-stu-id="b93a4-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="b93a4-142">它會查看您應用程式的二進位層級、解壓縮所有呼叫的 Api，然後列出您的目標 framework 無法使用的 Api （在此案例中為 .NET Core 3.1）。</span><span class="sxs-lookup"><span data-stu-id="b93a4-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="b93a4-143">您可以在下列位置找到有關此工具的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="b93a4-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="b93a4-144">這項工具有一個有趣的地方，那就是它只會從您自己的程式碼中呈現差異，而不是從外部套件（無法變更）的程式碼來呈現。</span><span class="sxs-lookup"><span data-stu-id="b93a4-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="b93a4-145">請記住，您應該已更新大部分的封裝，使其可與 .NET Core 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b93a4-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="b93a4-146">遷移專案檔案</span><span class="sxs-lookup"><span data-stu-id="b93a4-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="b93a4-147">建立新的 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="b93a4-147">Create the new .NET Core project</span></span>

<span data-ttu-id="b93a4-148">在大部分的情況下，您會想要將現有的專案更新為新的 .NET Core 格式。</span><span class="sxs-lookup"><span data-stu-id="b93a4-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="b93a4-149">不過，您也可以建立新的專案，同時維護舊的專案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="b93a4-150">更新舊專案的主要缺點是您遺失了設計工具支援，這對您而言可能很重要。</span><span class="sxs-lookup"><span data-stu-id="b93a4-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="b93a4-151">如果您想要繼續使用設計工具，您必須同時建立新的 .NET Core 專案與舊的，並共用資產。</span><span class="sxs-lookup"><span data-stu-id="b93a4-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="b93a4-152">如果您需要修改設計工具中的 UI 專案，可以切換到舊的專案來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="b93a4-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="b93a4-153">而且，由於資產已連結，因此也會在 .NET Core 專案中更新。</span><span class="sxs-lookup"><span data-stu-id="b93a4-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="b93a4-154">.NET Core 的[SDK 樣式專案](../../core/project-sdk/msbuild-props.md)比 .NET Framework 的專案格式簡單許多。</span><span class="sxs-lookup"><span data-stu-id="b93a4-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="b93a4-155">除了先前提到的專案以外 `PackageReference` ，您不需要執行其他動作。</span><span class="sxs-lookup"><span data-stu-id="b93a4-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="b93a4-156">新的專案格式[預設](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects)會包含特定的副檔名（例如 `.cs` 和檔案 `.xaml` ），而不需要將它們明確包含在專案檔中。</span><span class="sxs-lookup"><span data-stu-id="b93a4-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="b93a4-157">Assembly.info 考慮</span><span class="sxs-lookup"><span data-stu-id="b93a4-157">Assembly.info considerations</span></span>

<span data-ttu-id="b93a4-158">屬性會在 .NET Core 專案上自動產生。</span><span class="sxs-lookup"><span data-stu-id="b93a4-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="b93a4-159">如果專案包含*AssemblyInfo.cs*檔案，定義將會重複，這會導致編譯衝突。</span><span class="sxs-lookup"><span data-stu-id="b93a4-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="b93a4-160">您可以將下列專案新增至 .NET Core 專案檔，以刪除較舊的*AssemblyInfo.cs*檔案或停用自動產生：</span><span class="sxs-lookup"><span data-stu-id="b93a4-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="b93a4-161">資源</span><span class="sxs-lookup"><span data-stu-id="b93a4-161">Resources</span></span>

<span data-ttu-id="b93a4-162">內嵌資源會自動包含，但資源並不會，因此您需要將資源遷移至新的專案檔。</span><span class="sxs-lookup"><span data-stu-id="b93a4-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="b93a4-163">套件參考</span><span class="sxs-lookup"><span data-stu-id="b93a4-163">Package references</span></span>

<span data-ttu-id="b93a4-164">使用 [將**PackageReference 遷移至**] 選項，您可以輕鬆地將外部套件參考移至先前所述的新格式。</span><span class="sxs-lookup"><span data-stu-id="b93a4-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="b93a4-165">更新套件參考</span><span class="sxs-lookup"><span data-stu-id="b93a4-165">Update package references</span></span>

<span data-ttu-id="b93a4-166">更新您發現相容的套件版本，如上一節所示。</span><span class="sxs-lookup"><span data-stu-id="b93a4-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="b93a4-167">修正程式碼和組建</span><span class="sxs-lookup"><span data-stu-id="b93a4-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="b93a4-168">Microsoft。相容性</span><span class="sxs-lookup"><span data-stu-id="b93a4-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="b93a4-169">如果您的應用程式相依于無法在 .NET Core 上使用的 Api （例如登錄、Acl 或 WCF），您就必須包含該套件的參考， `Microsoft.Windows.Compatibility` 才能新增這些 Windows 特定的 api。</span><span class="sxs-lookup"><span data-stu-id="b93a4-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="b93a4-170">它們適用于 .NET Core，但不包含在跨平臺的情況。</span><span class="sxs-lookup"><span data-stu-id="b93a4-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="b93a4-171">有一個稱為 API 分析器（）的工具 <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ，可協助您識別與您的程式碼不相容的 api。</span><span class="sxs-lookup"><span data-stu-id="b93a4-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="b93a4-172">使用 \# if 指示詞</span><span class="sxs-lookup"><span data-stu-id="b93a4-172">Use \#if directives</span></span>

<span data-ttu-id="b93a4-173">如果以 .NET Framework 和 .NET Core 為目標時，您需要不同的執行路徑，您應該使用編譯常數。</span><span class="sxs-lookup"><span data-stu-id="b93a4-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="b93a4-174">將一些 if 指示詞新增 \# 至您的程式碼，以針對兩個目標保留相同的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="b93a4-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="b93a4-175">無法在 .NET Core 上使用的技術</span><span class="sxs-lookup"><span data-stu-id="b93a4-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="b93a4-176">某些技術無法在 .NET Core 上使用，例如：</span><span class="sxs-lookup"><span data-stu-id="b93a4-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="b93a4-177">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b93a4-177">AppDomains</span></span>
* <span data-ttu-id="b93a4-178">遠端</span><span class="sxs-lookup"><span data-stu-id="b93a4-178">Remoting</span></span>
* <span data-ttu-id="b93a4-179">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="b93a4-179">Code Access Security</span></span>
* <span data-ttu-id="b93a4-180">WCF 伺服器</span><span class="sxs-lookup"><span data-stu-id="b93a4-180">WCF Server</span></span>
* <span data-ttu-id="b93a4-181">Windows 工作流程</span><span class="sxs-lookup"><span data-stu-id="b93a4-181">Windows Workflow</span></span>

<span data-ttu-id="b93a4-182">這就是為什麼當您在應用程式中使用這些技術時，您需要找出其更換的原因。</span><span class="sxs-lookup"><span data-stu-id="b93a4-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="b93a4-183">如需詳細資訊，請參閱[.Net Core 上無法使用的 .NET Framework 技術](../../core/porting/net-framework-tech-unavailable.md)文章。</span><span class="sxs-lookup"><span data-stu-id="b93a4-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="b93a4-184">重新產生自動產生的用戶端</span><span class="sxs-lookup"><span data-stu-id="b93a4-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="b93a4-185">如果您的應用程式使用自動產生的程式碼（例如 WCF 用戶端），您可能需要重新產生此程式碼，以 .NET Core 為目標。</span><span class="sxs-lookup"><span data-stu-id="b93a4-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="b93a4-186">有時候，您可以找到一些遺漏的參考，因為它們可能不會包含為預設 .NET Core 元件集的一部分。</span><span class="sxs-lookup"><span data-stu-id="b93a4-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="b93a4-187">使用之類的工具 <https://apisof.net/> ，您可以輕鬆地找出遺漏參考所在的元件，並從 NuGet 新增。</span><span class="sxs-lookup"><span data-stu-id="b93a4-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="b93a4-188">回復封裝版本</span><span class="sxs-lookup"><span data-stu-id="b93a4-188">Rolling back package versions</span></span>

<span data-ttu-id="b93a4-189">一般的規則是，我們先前已指出您會更有效地更新每個套件版本，以與 .NET Core 相容。</span><span class="sxs-lookup"><span data-stu-id="b93a4-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="b93a4-190">不過，您可以發現，目標為更新且相容的元件版本，只是不會付費。</span><span class="sxs-lookup"><span data-stu-id="b93a4-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="b93a4-191">如果無法接受變更的成本，您可以考慮將封裝版本保留在 .NET Framework 上。</span><span class="sxs-lookup"><span data-stu-id="b93a4-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="b93a4-192">雖然它們可能不是以 .NET Core 為目標，但除非呼叫一些不支援的 Api，否則它們應該會正常運作。</span><span class="sxs-lookup"><span data-stu-id="b93a4-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="b93a4-193">執行和測試</span><span class="sxs-lookup"><span data-stu-id="b93a4-193">Run and test</span></span>

<span data-ttu-id="b93a4-194">一旦您的應用程式建立時未發生任何錯誤，您可以藉由測試每項功能來開始進行遷移的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="b93a4-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="b93a4-195">在最後一個步驟中，您可以根據應用程式的複雜性和您所使用的相依性和 Api，找到幾個不同的問題。</span><span class="sxs-lookup"><span data-stu-id="b93a4-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="b93a4-196">例如，如果您使用設定檔（*app.config*），您可能會在執行時間發現一些錯誤，例如不存在的設定區段。</span><span class="sxs-lookup"><span data-stu-id="b93a4-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="b93a4-197">使用 `Microsoft.Extensions.Configuration` NuGet 套件應該會修正該錯誤。</span><span class="sxs-lookup"><span data-stu-id="b93a4-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="b93a4-198">錯誤的另一個原因是使用 `BeginInvoke` 和方法， `EndInvoke` 因為 .net Core 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="b93a4-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="b93a4-199">它們在 .NET Core 上不受支援，因為它們相依于不存在於 .NET Core 上的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="b93a4-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="b93a4-200">若要解決此問題，請嘗試使用 `await` 關鍵字（如果有的話）或 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b93a4-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b93a4-201">您可以使用相容性分析器，讓您識別程式碼中的 Api 和程式碼模式，這可能會在執行時間使用 .NET Core 造成問題。</span><span class="sxs-lookup"><span data-stu-id="b93a4-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="b93a4-202">移至 <https://github.com/dotnet/platform-compat> 並在您的專案上使用 .NET API 分析器。</span><span class="sxs-lookup"><span data-stu-id="b93a4-202">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="b93a4-203">遷移 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="b93a4-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="b93a4-204">為了展示 Windows Forms 應用程式的完整整合程式，我們選擇遷移提供的 eShop 範例應用程式 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> 。</span><span class="sxs-lookup"><span data-stu-id="b93a4-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="b93a4-205">您可以在找到完整的遷移結果 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> 。</span><span class="sxs-lookup"><span data-stu-id="b93a4-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="b93a4-206">此應用程式會顯示產品目錄，並可讓使用者流覽、篩選及搜尋產品。</span><span class="sxs-lookup"><span data-stu-id="b93a4-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="b93a4-207">從架構的觀點來看，應用程式依賴外部 WCF 服務，做為後端資料庫的外觀。</span><span class="sxs-lookup"><span data-stu-id="b93a4-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="b93a4-208">您可以在下圖中看到主要應用程式視窗：</span><span class="sxs-lookup"><span data-stu-id="b93a4-208">You can see the main application window in the following picture:</span></span>

![主應用程式視窗](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="b93a4-210">如果您開啟 *.csproj*專案檔，您會看到類似如下的內容：</span><span class="sxs-lookup"><span data-stu-id="b93a4-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![.Csproj 檔案內容的螢幕擷取畫面](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="b93a4-212">如先前所述，.NET Core 專案有更精簡的樣式，而且您需要將專案結構遷移至新的 .NET Core SDK 樣式。</span><span class="sxs-lookup"><span data-stu-id="b93a4-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="b93a4-213">在 [方案總管中，以滑鼠右鍵按一下 [Windows Forms] 專案，然後選取 **[卸載專案**  >  **編輯**]。</span><span class="sxs-lookup"><span data-stu-id="b93a4-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="b93a4-214">現在您可以更新 .csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="b93a4-215">您將刪除整個內容，並將它取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b93a4-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="b93a4-216">儲存並重載專案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-216">Save and reload the project.</span></span> <span data-ttu-id="b93a4-217">您現在已完成更新專案檔，且專案是以 .NET Core 為目標。</span><span class="sxs-lookup"><span data-stu-id="b93a4-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="b93a4-218">如果您在此時編譯專案，您會發現一些與 WCF 用戶端參考相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b93a4-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="b93a4-219">由於這段程式碼會自動產生，因此您必須將它重新產生為目標 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="b93a4-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Visual Studio 上編譯錯誤的螢幕擷取畫面](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="b93a4-221">刪除*Reference.cs*檔案，並產生新的服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="b93a4-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="b93a4-222">在**已連線的服務**上按一下滑鼠右鍵，然後選取 [**加入已連接服務**] 選項。</span><span class="sxs-lookup"><span data-stu-id="b93a4-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![已選取 [加入已連接服務] 選項之 [已連線的服務] 功能表的螢幕擷取畫面](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="b93a4-224">[已連線的服務] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="b93a4-224">The Connected Services window opens.</span></span> <span data-ttu-id="b93a4-225">選取 [ **MICROSOFT WCF Web 服務**] 選項。</span><span class="sxs-lookup"><span data-stu-id="b93a4-225">Select the **Microsoft WCF Web Service** option.</span></span>

![[已連線的服務] 視窗的螢幕擷取畫面](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="b93a4-227">如果您的 WCF 服務與本範例中的相同，則您可以選取 [**探索**] 選項，而不是指定 [服務 URL]。</span><span class="sxs-lookup"><span data-stu-id="b93a4-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![[設定 WCF Web 服務參考] 視窗的螢幕擷取畫面](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="b93a4-229">一旦找到服務，此工具就會反映服務所執行的 API 合約。</span><span class="sxs-lookup"><span data-stu-id="b93a4-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="b93a4-230">將命名空間的名稱變更為，如下 `eShopServiceReference` 圖所示：</span><span class="sxs-lookup"><span data-stu-id="b93a4-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![螢幕擷取畫面 API 合約和命名空間已變更](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="b93a4-232">選取 [**完成]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b93a4-232">Select the **Finish** button.</span></span> <span data-ttu-id="b93a4-233">一段時間後，您會看到產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b93a4-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="b93a4-234">您應該會看到三個自動產生的檔案：</span><span class="sxs-lookup"><span data-stu-id="b93a4-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="b93a4-235">*消費者入門*： GitHub 的連結，可提供 WCF 的一些相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b93a4-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="b93a4-236">*ConnectedService*：用來連接到服務的設定參數。</span><span class="sxs-lookup"><span data-stu-id="b93a4-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="b93a4-237">*Reference.cs*：實際的 WCF 用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="b93a4-237">*Reference.cs*: the actual WCF client code.</span></span>

![[方案總管] 視窗的螢幕擷取畫面，其中包含三個自動產生的檔案](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="b93a4-239">如果您重新編譯，您會在*Helper*資料夾內看到許多來自 *.cs*檔案的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b93a4-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="b93a4-240">此資料夾存在於 .NET Framework 版本中，但不包含在舊的 *.csproj*中。</span><span class="sxs-lookup"><span data-stu-id="b93a4-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="b93a4-241">但使用新的 SDK 樣式專案時，預設會包含專案檔位置底下的每個程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="b93a4-242">也就是說，新的 .NET Core 專案會嘗試編譯*Helper*資料夾內的檔案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="b93a4-243">因為不需要該資料夾，所以您可以放心地將它刪除。</span><span class="sxs-lookup"><span data-stu-id="b93a4-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="b93a4-244">如果您再次編譯專案並加以執行，您就不會看到產品映射。</span><span class="sxs-lookup"><span data-stu-id="b93a4-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="b93a4-245">問題在於，檔案的路徑已稍微變更。</span><span class="sxs-lookup"><span data-stu-id="b93a4-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="b93a4-246">若要修正此問題，您需要在路徑中新增另一個深度層級，並在檔案中更新 `CatalogView.cs` 該行：</span><span class="sxs-lookup"><span data-stu-id="b93a4-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="b93a4-247">to</span><span class="sxs-lookup"><span data-stu-id="b93a4-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="b93a4-248">在這種變更之後，您可以檢查應用程式是否會如預期般在 .NET Core 上啟動並執行。</span><span class="sxs-lookup"><span data-stu-id="b93a4-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="b93a4-249">遷移 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="b93a4-249">Migrating a WPF application</span></span>

<span data-ttu-id="b93a4-250">我們將使用 `Shop.ClassicWPF` 範例應用程式來執行遷移。</span><span class="sxs-lookup"><span data-stu-id="b93a4-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="b93a4-251">下圖顯示應用程式在遷移前的螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="b93a4-251">The following image shows a screenshot of the app before migration:</span></span>

![遷移前的範例應用程式](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="b93a4-253">此應用程式會使用本機 SQL Server Express 資料庫來保存產品目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="b93a4-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="b93a4-254">這個資料庫是直接從 WPF 應用程式存取。</span><span class="sxs-lookup"><span data-stu-id="b93a4-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="b93a4-255">首先，您必須將 *.csproj*檔案更新為 .net Core 應用程式所使用的新 SDK 樣式。</span><span class="sxs-lookup"><span data-stu-id="b93a4-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="b93a4-256">您將遵循 Windows Forms 遷移中所述的相同步驟：您將會卸載專案、開啟 *.csproj*檔案、更新其內容，然後重載專案。</span><span class="sxs-lookup"><span data-stu-id="b93a4-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="b93a4-257">在此情況下，請刪除 *.csproj*檔案的所有內容，並取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b93a4-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="b93a4-258">如果您重載專案並加以編譯，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="b93a4-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Visual Studio 上編譯錯誤的螢幕擷取畫面](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="b93a4-260">由於您已刪除所有 *.csproj*內容，因此您遺失了舊專案中的專案參考規格。</span><span class="sxs-lookup"><span data-stu-id="b93a4-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="b93a4-261">您只需要將這一行新增到 *.csproj*檔案，就可以包含專案參考回來：</span><span class="sxs-lookup"><span data-stu-id="b93a4-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="b93a4-262">您也可以在 [相依性] 節點上按一下滑鼠右鍵，然後選取 [**加入專案參考** **]** ，讓 Visual Studio 協助您。</span><span class="sxs-lookup"><span data-stu-id="b93a4-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="b93a4-263">選取方案中的專案，然後按一下 **[確定]**：</span><span class="sxs-lookup"><span data-stu-id="b93a4-263">Select the project from the solution and click **OK**:</span></span>

![[參考管理員] 對話方塊的螢幕擷取畫面，其中已選取 eShop SqlProvider 專案](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="b93a4-265">一旦您加入遺漏的專案參考，應用程式就會如預期般在 .NET Core 上進行編譯和執行。</span><span class="sxs-lookup"><span data-stu-id="b93a4-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b93a4-266">[上一個](windows-migration.md) 
>[下一步](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="b93a4-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
