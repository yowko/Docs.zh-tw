---
title: 移轉至 .NET 5 的範例
description: 顯示如何將以 .NET Framework 為目標的範例應用程式遷移至 .NET 5。
ms.date: 01/19/2021
ms.openlocfilehash: 39ecdfa639f4d68a4a8821da839f014c8de42ab0
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216261"
---
# <a name="example-of-migrating-to-net"></a><span data-ttu-id="ef2ea-103">遷移至 .NET 的範例</span><span class="sxs-lookup"><span data-stu-id="ef2ea-103">Example of migrating to .NET</span></span>

<span data-ttu-id="ef2ea-104">在本章中，我們會提供實用的指導方針，以協助您將現有的應用程式從 .NET Framework 遷移至 .NET。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET.</span></span>

<span data-ttu-id="ef2ea-105">我們會提供您可以遵循的結構完善程式，以及每個步驟應考慮的最重要事項。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="ef2ea-106">接著，我們會記載範例傳統型應用程式（從 WinForms 和 WPF 版本）的逐步遷移程式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="ef2ea-107">移轉處理序概觀</span><span class="sxs-lookup"><span data-stu-id="ef2ea-107">Migration process overview</span></span>

<span data-ttu-id="ef2ea-108">遷移套裝程式含四個順序步驟：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="ef2ea-109">**準備**：瞭解專案必須先瞭解的相依性。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="ef2ea-110">在此步驟中，您會將目前的專案納入可簡化遷移啟動點的狀態。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="ef2ea-111">**遷移專案檔：** .net 專案使用新的 SDK 樣式專案格式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-111">**Migrate Project File:** .NET projects use the new SDK-style project format.</span></span> <span data-ttu-id="ef2ea-112">以這種格式建立新的專案檔，或更新您必須使用 SDK 樣式的專案檔。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="ef2ea-113">**修正程式碼和組建：** 在 .NET 中建立程式碼，以解決 .NET Framework 與 .NET 之間的 API 層級差異。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-113">**Fix code and build:** Build the code in .NET addressing API-level differences between .NET Framework and .NET.</span></span> <span data-ttu-id="ef2ea-114">如有需要，請將協力廠商套件更新為支援 .NET 的封裝。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-114">If needed, update third-party packages to the ones that support .NET.</span></span>

4. <span data-ttu-id="ef2ea-115">**執行和測試：** 在執行時間之前可能不會顯示任何差異。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="ef2ea-116">因此，請別忘了執行應用程式，並測試所有專案是否都能如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="ef2ea-117">準備</span><span class="sxs-lookup"><span data-stu-id="ef2ea-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="ef2ea-118">遷移 packages.config 檔案</span><span class="sxs-lookup"><span data-stu-id="ef2ea-118">Migrate packages.config file</span></span>

<span data-ttu-id="ef2ea-119">在 .NET Framework 應用程式中，會在 *packages.config* 檔案中宣告外部封裝的所有參考。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="ef2ea-120">在 .NET 中，不再需要使用 *packages.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-120">In .NET, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="ef2ea-121">相反地，請使用專案檔內的 [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) 屬性來指定您應用程式的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="ef2ea-122">因此，您需要從一種格式轉換成另一種格式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="ef2ea-123">您可以手動進行更新，取得 *packages.config* 檔中所包含的相依性，並將其遷移至具有格式的專案檔 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="ef2ea-124">或者，您可以讓 Visual Studio 為您執行工作：以滑鼠右鍵按一下 *packages.config* 檔案，然後選取 [ **遷移 packages.config 至 PackageReference** 選項。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net"></a><span data-ttu-id="ef2ea-125">確認 .NET 中的每個相依性相容性</span><span class="sxs-lookup"><span data-stu-id="ef2ea-125">Verify every dependency compatibility in .NET</span></span>

<span data-ttu-id="ef2ea-126">遷移封裝參考之後，您必須檢查每個參考的相容性。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="ef2ea-127">您可以探索應用程式在 [nuget.org](https://www.nuget.org/)上使用的每個 NuGet 套件的相依性。如果封裝有 .NET Standard 相依性，則會在 .NET 5.0 上運作，因為 .NET [支援](../../standard/net-standard.md#net-implementation-support) 所有版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET 5.0 because .NET [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="ef2ea-128">下圖顯示套件的相依性 `Castle.Windsor` ：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Castle. Windsor 套件之 NuGet 相依性的螢幕擷取畫面](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="ef2ea-130">若要檢查套件相容性，您可以使用 <https://fuget.org> 提供更詳細的版本和相依性相關資訊的工具。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="ef2ea-131">可能是專案參考了不支援 .NET 的較舊套件版本，但您可能會發現支援它的較新版本。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-131">Maybe the project is referencing older package versions that don't support .NET, but you might find newer versions that do support it.</span></span> <span data-ttu-id="ef2ea-132">因此，將套件更新為較新版本通常是很好的建議。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="ef2ea-133">不過，您應該考慮更新套件版本可能會導致某些可能會強制您更新程式碼的重大變更。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="ef2ea-134">如果找不到相容的版本，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="ef2ea-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="ef2ea-135">如果您因為這些重大變更而不想更新套件的版本，該怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="ef2ea-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="ef2ea-136">別擔心，因為可以依賴來自 .NET 應用程式的 .NET Framework 套件。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET application.</span></span> <span data-ttu-id="ef2ea-137">別忘了大量測試，因為如果外部封裝呼叫的 API 無法在 .NET 上使用，它可能會造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET.</span></span> <span data-ttu-id="ef2ea-138">當您使用的舊套件不會進行更新，而且您可以直接將它重定為在 .NET 上運作時，這就很好用。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="ef2ea-139">檢查是否有 API 相容性</span><span class="sxs-lookup"><span data-stu-id="ef2ea-139">Check for API compatibility</span></span>

<span data-ttu-id="ef2ea-140">由於 .NET Framework 和 .NET 中的 API 介面類別似但不完全相同，因此您必須檢查哪些 Api 可在 .NET 上使用，而不是。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-140">Since the API surface in .NET Framework and .NET is similar but not identical, you must check which APIs are available on .NET and which aren't.</span></span> <span data-ttu-id="ef2ea-141">您可以使用 .NET 可攜性分析器工具來呈現 .NET 上所使用的 Api。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET.</span></span> <span data-ttu-id="ef2ea-142">它會查看您應用程式的二進位層級、解壓縮所有呼叫的 Api，然後列出您的目標 framework 上無法使用的 Api ( .NET 5.0 （在此案例中) ）。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET 5.0 in this case).</span></span>

<span data-ttu-id="ef2ea-143">您可以在下列位置找到此工具的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="ef2ea-144">這項工具的有趣之處在于，它只會顯示來自您自己程式碼的差異，而不是來自外部套件的程式碼，您無法變更這些差異。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="ef2ea-145">請記住，您應該已更新大部分的封裝，才能讓它們與 .NET 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-145">Remember you should have updated most of these packages to make them work with .NET.</span></span>

### <a name="migrate-with-try-convert-tool"></a><span data-ttu-id="ef2ea-146">使用 Try Convert 工具進行遷移</span><span class="sxs-lookup"><span data-stu-id="ef2ea-146">Migrate with Try Convert tool</span></span>

<span data-ttu-id="ef2ea-147">[Try Convert](https://github.com/dotnet/try-convert/releases)工具是遷移專案的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-147">The [Try Convert](https://github.com/dotnet/try-convert/releases) tool is a great way to migrate a project.</span></span> <span data-ttu-id="ef2ea-148">它是一種全域工具，它會嘗試將您的專案檔從舊樣式升級為新的 SDK 樣式，並將適用的專案重定到 .NET 5。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-148">It's a global tool that attempts to upgrade your project file from the old style to the new SDK style, and retargets applicable projects to .NET 5.</span></span> <span data-ttu-id="ef2ea-149">安裝之後，您可以執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-149">Once installed, you can run the following commands:</span></span>

```dotnetcli
try-convert -p "<path to your project file>"
```

<span data-ttu-id="ef2ea-150">或：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-150">Or:</span></span>

```dotnetcli
try-convert -w "<path to your solution>"
```

<span data-ttu-id="ef2ea-151">工具嘗試進行轉換之後，請在 Visual Studio 中重載您的檔案，以執行和測試。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-151">After the tool attempts the conversion, reload your files in Visual Studio to run and test.</span></span> <span data-ttu-id="ef2ea-152">由於您的專案細節，嘗試轉換的可能性可能無法執行轉換。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-152">There's a possibility that Try Convert won't be able to perform the conversion due to the specifics of your project.</span></span> <span data-ttu-id="ef2ea-153">在此情況下，您可以參考下列步驟。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-153">In that case, you can refer the below steps.</span></span>

#### <a name="migrate-manually"></a><span data-ttu-id="ef2ea-154">手動遷移</span><span class="sxs-lookup"><span data-stu-id="ef2ea-154">Migrate manually</span></span>

1. <span data-ttu-id="ef2ea-155">建立新的 .NET 專案</span><span class="sxs-lookup"><span data-stu-id="ef2ea-155">Create the new .NET project</span></span>

<span data-ttu-id="ef2ea-156">在大部分情況下，您會想要將現有的專案更新為新的 .NET 格式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-156">In most cases, you'll want to update your existing project to the new .NET format.</span></span> <span data-ttu-id="ef2ea-157">不過，您也可以建立新的專案，同時保留舊專案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-157">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="ef2ea-158">更新舊專案的主要缺點是您失去了設計工具支援，這對您和開發小組來說可能很重要。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-158">The main drawback from updating the old project is that you lose designer support, which may be important to you and your development team.</span></span> <span data-ttu-id="ef2ea-159">如果您想要繼續使用設計工具，您必須建立與舊專案平行的新 .NET 專案，並共用資產。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-159">If you want to keep using the designer, you must create a new .NET project in parallel with the old one and share assets.</span></span> <span data-ttu-id="ef2ea-160">如果您需要修改設計工具中的 UI 元素，您可以切換到舊的專案來進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-160">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="ef2ea-161">而且，因為資產已連結，所以它們也會在 .NET 專案中更新。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-161">And since assets are linked, they'll be updated in the .NET project as well.</span></span>

<span data-ttu-id="ef2ea-162">適用于 .NET 的 [SDK 樣式專案](../../core/project-sdk/msbuild-props.md) 比 .NET Framework 的專案格式簡單許多。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-162">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="ef2ea-163">除了先前提及的 `PackageReference` 專案之外，您還不需要再做更多工作。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-163">Apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="ef2ea-164">新的專案格式 [預設包含具有特定副檔名](../../core/project-sdk/overview.md#default-includes-and-excludes)的檔案，例如 `.cs` 和檔案 `.xaml` ，而不需要將它們明確包含在專案檔中。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-164">The new project format [includes files with certain extensions by default](../../core/project-sdk/overview.md#default-includes-and-excludes), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="ef2ea-165">AssemblyInfo 考慮</span><span class="sxs-lookup"><span data-stu-id="ef2ea-165">AssemblyInfo considerations</span></span>

<span data-ttu-id="ef2ea-166">屬性會在 .NET 專案上自動產生。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-166">Attributes are autogenerated on .NET projects.</span></span> <span data-ttu-id="ef2ea-167">如果專案包含 *AssemblyInfo.cs* 檔案，將會複製定義，而這會導致編譯衝突。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-167">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="ef2ea-168">您可以將下列專案新增至 .NET 專案檔，以刪除較舊的 *AssemblyInfo.cs* 檔案或停用自動產生：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-168">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="ef2ea-169">資源</span><span class="sxs-lookup"><span data-stu-id="ef2ea-169">Resources</span></span>

<span data-ttu-id="ef2ea-170">內嵌的資源會自動包含，但是資源不是，因此您需要將資源遷移至新的專案檔。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-170">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="ef2ea-171">套件參考</span><span class="sxs-lookup"><span data-stu-id="ef2ea-171">Package references</span></span>

<span data-ttu-id="ef2ea-172">您可以使用 [將 **packages.config 遷移至 PackageReference** ] 選項，輕鬆地將外部套件參考移至新的格式，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-172">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="ef2ea-173">更新套件參考</span><span class="sxs-lookup"><span data-stu-id="ef2ea-173">Update package references</span></span>

<span data-ttu-id="ef2ea-174">將您找到的套件版本更新為相容，如上一節所示。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-174">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="ef2ea-175">修正程式碼和組建</span><span class="sxs-lookup"><span data-stu-id="ef2ea-175">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="ef2ea-176">Microsoft 的相容性</span><span class="sxs-lookup"><span data-stu-id="ef2ea-176">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="ef2ea-177">如果您的應用程式相依于 .NET 上無法使用的 Api （例如登錄、Acl 或 WCF），則您必須包含套件的參考， `Microsoft.Windows.Compatibility` 以新增這些 Windows 特定的 api。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-177">If your application depends on APIs that aren't available on .NET, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="ef2ea-178">它們可在 .NET 上運作，但未包含，因為它們不是跨平臺。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-178">They work on .NET but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="ef2ea-179">有一個稱為 API 分析器的工具 (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) ，可協助您識別與您的程式碼不相容的 api。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-179">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="ef2ea-180">使用 \# if 指示詞</span><span class="sxs-lookup"><span data-stu-id="ef2ea-180">Use \#if directives</span></span>

<span data-ttu-id="ef2ea-181">如果您在以 .NET Framework 和 .NET 為目標時需要不同的執行路徑，您應該使用編譯常數。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-181">If you need different execution paths when targeting .NET Framework and .NET, you should use compilation constants.</span></span> <span data-ttu-id="ef2ea-182">將某些 if 指示詞新增 \# 至您的程式碼，以保持兩個目標的相同程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-182">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net"></a><span data-ttu-id="ef2ea-183">.NET 上無法使用的技術</span><span class="sxs-lookup"><span data-stu-id="ef2ea-183">Technologies not available on .NET</span></span>

<span data-ttu-id="ef2ea-184">有些技術無法在 .NET 上使用，例如：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-184">Some technologies aren't available on .NET, such as:</span></span>

* <span data-ttu-id="ef2ea-185">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef2ea-185">AppDomains</span></span>
* <span data-ttu-id="ef2ea-186">遠端</span><span class="sxs-lookup"><span data-stu-id="ef2ea-186">Remoting</span></span>
* <span data-ttu-id="ef2ea-187">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="ef2ea-187">Code Access Security</span></span>
* <span data-ttu-id="ef2ea-188">WCF 伺服器</span><span class="sxs-lookup"><span data-stu-id="ef2ea-188">WCF Server</span></span>
* <span data-ttu-id="ef2ea-189">Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="ef2ea-189">Windows Workflow</span></span>

<span data-ttu-id="ef2ea-190">這就是為什麼當您在應用程式中使用這些技術時，需要找出這些技術的取代。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-190">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="ef2ea-191">如需詳細資訊，請參閱 [.Net Core 和 .net 5 + 上無法使用的 .NET Framework 技術](../../core/porting/net-framework-tech-unavailable.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-191">For more information, see the [.NET Framework technologies unavailable on .NET Core and .NET 5+](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="ef2ea-192">重新產生自動產生的用戶端</span><span class="sxs-lookup"><span data-stu-id="ef2ea-192">Regenerate autogenerated clients</span></span>

<span data-ttu-id="ef2ea-193">如果您的應用程式使用自動產生的程式碼（例如 WCF 用戶端），您可能需要重新產生此程式碼以將目標設為 .NET。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-193">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET.</span></span> <span data-ttu-id="ef2ea-194">有時候，您可以找到一些遺漏的參考，因為它們可能不會包含在預設 .NET 元件集的一部分。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-194">Sometimes, you can find some missing references since they may not be included as part of the default .NET assemblies set.</span></span> <span data-ttu-id="ef2ea-195">您可以使用類似的工具 <https://apisof.net/> ，輕鬆地找出遺漏參考所在的元件，並從 NuGet 新增該元件。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-195">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="ef2ea-196">正在回復套件版本</span><span class="sxs-lookup"><span data-stu-id="ef2ea-196">Rolling back package versions</span></span>

<span data-ttu-id="ef2ea-197">一般來說，我們之前說過，您可以更妥善地更新每個單一套件版本，使其與 .NET 相容。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-197">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET.</span></span> <span data-ttu-id="ef2ea-198">不過，您可以找到以更新版本與相容版本為目標的元件，而不需要支付任何費用。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-198">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="ef2ea-199">如果無法接受變更的成本，您可以考慮將封裝版本保留在 .NET Framework 上的版本。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-199">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="ef2ea-200">雖然它們可能不是以 .NET 為目標，但它們應該可以正常運作，除非它們呼叫一些不支援的 Api。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-200">Although they may not be targeting .NET, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="ef2ea-201">執行和測試</span><span class="sxs-lookup"><span data-stu-id="ef2ea-201">Run and test</span></span>

<span data-ttu-id="ef2ea-202">當您的應用程式在建立時沒有錯誤，您可以藉由測試每項功能來開始進行遷移的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-202">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="ef2ea-203">在最後一個步驟中，您可以根據應用程式的複雜度，以及您所使用的相依性和 Api，找到幾個不同的問題。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-203">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="ef2ea-204">例如，如果您使用設定檔 (*app.config*) ，您可能會在執行時間發現某些錯誤，例如不存在的設定區段。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-204">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="ef2ea-205">使用 `Microsoft.Extensions.Configuration` NuGet 套件應該可修正該錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-205">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="ef2ea-206">錯誤的另一個原因是使用 `BeginInvoke` 和方法， `EndInvoke` 因為它們在 .net 上不受支援。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-206">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET.</span></span> <span data-ttu-id="ef2ea-207">.NET 不支援它們，因為它們相依于不存在於 .NET 的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-207">They aren't supported on .NET because they have a dependency on Remoting, which doesn't exist on .NET.</span></span> <span data-ttu-id="ef2ea-208">若要解決此問題，請嘗試使用 `await` 關鍵字 (（如果有) 或 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法）。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-208">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ef2ea-209">您可以使用相容性分析器，來識別程式碼中的 Api 和程式碼模式，其可能會在執行時間使用 .NET 來產生問題。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-209">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET.</span></span> <span data-ttu-id="ef2ea-210">移至 <https://github.com/dotnet/platform-compat> 並在您的專案上使用 .NET API 分析器。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-210">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="ef2ea-211">遷移 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ef2ea-211">Migrating a Windows Forms application</span></span>

<span data-ttu-id="ef2ea-212">為了展示 Windows Forms 應用程式的完整遷移程式，我們選擇遷移中提供的 eShop 範例應用程式 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> 。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-212">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="ef2ea-213">您可以在中找到遷移的完整結果 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> 。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-213">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="ef2ea-214">此應用程式會顯示產品目錄，並可讓使用者流覽、篩選和搜尋產品。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-214">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="ef2ea-215">從架構的觀點來看，應用程式依賴作為後端資料庫外觀的外部 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-215">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="ef2ea-216">您可以在下圖中看到主要的應用程式視窗：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-216">You can see the main application window in the following picture:</span></span>

![主應用程式視窗](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="ef2ea-218">如果您開啟 *.csproj* 專案檔，則會看到如下的內容：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-218">If you open the *.csproj* project file, you can see something like this:</span></span>

![.Csproj 檔案內容的螢幕擷取畫面](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="ef2ea-220">如先前所述，.NET 專案有更精簡的樣式，而您需要將專案結構遷移至新的 .NET SDK 樣式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-220">As previously mentioned, .NET project has a more compact style and you need to migrate the project structure to the new .NET SDK style.</span></span>

<span data-ttu-id="ef2ea-221">在 [方案總管中，以滑鼠右鍵按一下 Windows Forms 專案，然後選取 **[卸載專案**  >  **編輯**]。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-221">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="ef2ea-222">現在您可以更新 .csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-222">Now you can update the .csproj file.</span></span> <span data-ttu-id="ef2ea-223">您將刪除整個內容，並將它取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-223">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="ef2ea-224">儲存並重載專案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-224">Save and reload the project.</span></span> <span data-ttu-id="ef2ea-225">您現在已完成更新專案檔案，且專案的目標為 .NET。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-225">You're now done updating the project file and the project is targeting the .NET.</span></span>

<span data-ttu-id="ef2ea-226">如果您在此時編譯專案，您會發現一些與 WCF 用戶端參考相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-226">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="ef2ea-227">因為此程式碼會自動產生，所以您必須將它重新產生成以 .NET 為目標。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-227">Since this code is autogenerated, you must regenerate it to target .NET.</span></span>

![Visual Studio 上編譯錯誤的螢幕擷取畫面](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="ef2ea-229">刪除 *Reference.cs* 檔案並產生新的服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-229">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="ef2ea-230">以滑鼠右鍵按一下 **已連線的服務** ，然後選取 [ **加入已連接服務** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-230">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![已選取 [加入已連接服務] 選項之 [已連線的服務] 功能表的螢幕擷取畫面](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="ef2ea-232">已連線的服務] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-232">The Connected Services window opens.</span></span> <span data-ttu-id="ef2ea-233">選取 [ **MICROSOFT WCF Web 服務** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-233">Select the **Microsoft WCF Web Service** option.</span></span>

![已連線的服務視窗的螢幕擷取畫面](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="ef2ea-235">如果您在此範例中的相同方案中有 WCF 服務，您可以選取 [ **探索** ] 選項，而不是指定服務 URL。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-235">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![[設定 WCF Web Service Reference] 視窗的螢幕擷取畫面](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="ef2ea-237">一旦找到服務之後，此工具就會反映服務所執行的 API 合約。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-237">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="ef2ea-238">將命名空間的名稱變更如下 `eShopServiceReference` 圖所示：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-238">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![API 合約和命名空間已變更的螢幕擷取畫面](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="ef2ea-240">選取 [ **完成]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-240">Select the **Finish** button.</span></span> <span data-ttu-id="ef2ea-241">經過一段時間之後，您會看到產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-241">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="ef2ea-242">您應該會看到三個自動產生的檔案：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-242">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="ef2ea-243">*開始使用*： GitHub 的連結，可提供 WCF 的一些資訊。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-243">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="ef2ea-244">*ConnectedService.json*：用來連接到服務的設定參數。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-244">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="ef2ea-245">*Reference.cs*：實際的 WCF 用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-245">*Reference.cs*: the actual WCF client code.</span></span>

![包含三個自動產生檔案之方案總管視窗的螢幕擷取畫面](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="ef2ea-247">如果您再次編譯，您將會看到來自協助 *程式資料夾內* *.cs* 檔案的許多錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-247">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="ef2ea-248">此資料夾存在於 .NET Framework 版本中，但不包含在舊的 *.csproj* 中。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-248">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="ef2ea-249">但在新的 SDK 樣式專案中，預設會包含專案檔位置底下的每個程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-249">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="ef2ea-250">也就是說，新的 .NET Core 專案會嘗試編譯 *Helper* 資料夾內的檔案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-250">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="ef2ea-251">因為不需要該資料夾，所以您可以安全地將其刪除。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-251">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="ef2ea-252">如果您重新編譯專案並加以執行，您將不會看到產品影像。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-252">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="ef2ea-253">問題在於現在檔案的路徑稍有變更。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-253">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="ef2ea-254">若要修正此問題，您必須在路徑中新增另一個深度層級，並在檔案中更新 `CatalogView.cs` ：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-254">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="ef2ea-255">to</span><span class="sxs-lookup"><span data-stu-id="ef2ea-255">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="ef2ea-256">在此變更之後，您可以檢查應用程式在 .NET Core 上啟動並如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-256">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="ef2ea-257">遷移 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="ef2ea-257">Migrating a WPF application</span></span>

<span data-ttu-id="ef2ea-258">我們將使用 `Shop.ClassicWPF` 範例應用程式來執行遷移。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-258">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="ef2ea-259">下圖顯示在遷移之前的應用程式螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-259">The following image shows a screenshot of the app before migration:</span></span>

![遷移之前的範例應用程式](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="ef2ea-261">此應用程式會使用本機 SQL Server Express 資料庫來保存產品目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-261">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="ef2ea-262">您可以直接從 WPF 應用程式存取此資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-262">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="ef2ea-263">首先，您必須將 *.csproj* 檔案更新為 .net Core 應用程式所使用的新 SDK 樣式。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-263">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="ef2ea-264">您將遵循 Windows Forms 遷移中所述的相同步驟：您將卸載專案、開啟 *.csproj* 檔案、更新其內容，然後重載專案。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-264">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="ef2ea-265">在此情況下，請刪除 *.csproj* 檔案的所有內容，並將它取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-265">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="ef2ea-266">如果您重載專案並加以編譯，您將會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-266">If you reload the project and compile it, you'll get the following error:</span></span>

![Visual Studio 上編譯錯誤的螢幕擷取畫面](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="ef2ea-268">由於您已刪除所有 *.csproj* 內容，因此您已遺失存在於舊專案中的專案參考規格。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-268">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="ef2ea-269">您只需要將這一行新增至 *.csproj* 檔案，就可以包含專案參考：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-269">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="ef2ea-270">您也可以在 [相依性] 節點上按一下滑鼠右鍵，然後選取 [**加入專案參考** **]** ，讓 Visual Studio 協助您。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-270">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="ef2ea-271">從方案中選取專案，然後按一下 **[確定]**：</span><span class="sxs-lookup"><span data-stu-id="ef2ea-271">Select the project from the solution and click **OK**:</span></span>

![已選取 eShop SqlProvider 專案的 [參考管理員] 對話方塊螢幕擷取畫面](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="ef2ea-273">一旦您加入遺漏的專案參考之後，應用程式就會在 .NET 上以預期的方式編譯和執行。</span><span class="sxs-lookup"><span data-stu-id="ef2ea-273">Once you add the missing project reference, the application compiles and runs as expected on .NET.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ef2ea-274">[上一個](windows-migration.md) 
>[下一步](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="ef2ea-274">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
