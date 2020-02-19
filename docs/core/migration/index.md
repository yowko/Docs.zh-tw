---
title: 從 project.json 進行的 .NET Core 移轉
description: 了解如何使用 project.json 來移轉舊版 .NET Core 專案
ms.date: 07/19/2017
ms.openlocfilehash: 8a9dc05c82fd5476a70ee36a294a287abbfb68c4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450683"
---
# <a name="migrating-net-core-projects-from-projectjson"></a><span data-ttu-id="dc4fd-103">從 project.json 移轉 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="dc4fd-103">Migrating .NET Core projects from project.json</span></span>

<span data-ttu-id="dc4fd-104">本檔涵蓋下列三種 .NET Core 專案的遷移案例：</span><span class="sxs-lookup"><span data-stu-id="dc4fd-104">This document covers the following three migration scenarios for .NET Core projects:</span></span>

1. [<span data-ttu-id="dc4fd-105">從 *project.json* 的有效最新結構描述移轉至 *csproj*</span><span class="sxs-lookup"><span data-stu-id="dc4fd-105">Migration from a valid latest schema of *project.json* to *csproj*</span></span>](#migration-from-projectjson-to-csproj)
2. [<span data-ttu-id="dc4fd-106">從 DNX 移轉至 csproj</span><span class="sxs-lookup"><span data-stu-id="dc4fd-106">Migration from DNX to csproj</span></span>](#migration-from-dnx-to-csproj)
3. [<span data-ttu-id="dc4fd-107">從 RC3 和舊版 .NET Core csproj 專案移轉至最終格式</span><span class="sxs-lookup"><span data-stu-id="dc4fd-107">Migration from RC3 and previous .NET Core csproj projects to the final format</span></span>](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

<span data-ttu-id="dc4fd-108">本檔僅適用于使用 project. json 的舊版 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-108">This document is only applicable to older .NET Core projects that use project.json.</span></span> <span data-ttu-id="dc4fd-109">不適用從 .NET Framework 遷移至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-109">It does not apply to migrating from .NET Framework to .NET Core.</span></span>

## <a name="migration-from-projectjson-to-csproj"></a><span data-ttu-id="dc4fd-110">從 project.json 移轉至 csproj</span><span class="sxs-lookup"><span data-stu-id="dc4fd-110">Migration from project.json to csproj</span></span>

<span data-ttu-id="dc4fd-111">您可以使用下列其中一種方法從 *project.json* 移轉至 *.csproj*：</span><span class="sxs-lookup"><span data-stu-id="dc4fd-111">Migration from *project.json* to *.csproj* can be done using one of the following methods:</span></span>

- [<span data-ttu-id="dc4fd-112">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc4fd-112">Visual Studio</span></span>](#visual-studio)
- [<span data-ttu-id="dc4fd-113">dotnet migrate 命令列工具</span><span class="sxs-lookup"><span data-stu-id="dc4fd-113">dotnet migrate command-line tool</span></span>](#dotnet-migrate)

<span data-ttu-id="dc4fd-114">這兩種方法使用相同的基礎引擎來移轉專案，因此結果會相同。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-114">Both methods use the same underlying engine to migrate the projects, so the results will be the same for both.</span></span> <span data-ttu-id="dc4fd-115">在大部分情況下，使用這兩種方式之一來遷移*專案。 json*到 *.csproj*是唯一需要的專案，不需要進一步手動編輯專案檔。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-115">In most cases, using one of these two ways to migrate the *project.json* to *csproj* is the only thing that is needed, and no further manual editing of the project file is necessary.</span></span> <span data-ttu-id="dc4fd-116">所產生的 *.csproj* 檔案將會以包含目錄的相同名稱命名。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-116">The resulting *.csproj* file will be named the same as the containing directory name.</span></span>

### <a name="visual-studio"></a><span data-ttu-id="dc4fd-117">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc4fd-117">Visual Studio</span></span>

<span data-ttu-id="dc4fd-118">當您開啟*xproj*檔案或參考*xproj*檔案的方案檔（在 Visual Studio 2017 或 Visual Studio 2019 16.2 和更早版本中）時，會出現 [**單向升級**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-118">When you open an *.xproj* file or a solution file that references *.xproj* files in Visual Studio 2017 or Visual Studio 2019 version 16.2 and earlier, the **One-way upgrade** dialog appears.</span></span> <span data-ttu-id="dc4fd-119">此對話方塊會顯示要移轉的專案。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-119">The dialog displays the projects to be migrated.</span></span> <span data-ttu-id="dc4fd-120">如果您開啟方案檔，則會列出方案檔中指定的所有專案。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-120">If you open a solution file, all the projects specified in the solution file are listed.</span></span> <span data-ttu-id="dc4fd-121">檢閱要移轉的專案清單，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-121">Review the list of projects to be migrated and select **OK**.</span></span>

![[單向升級] 對話方塊顯示要移轉的專案清單](media/one-way-upgrade.jpg)

<span data-ttu-id="dc4fd-123">Visual Studio 會自動遷移選取的專案。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-123">Visual Studio migrates the selected projects automatically.</span></span> <span data-ttu-id="dc4fd-124">在遷移方案時，如果您未選擇 [所有專案]，則會出現相同的對話方塊，要求您從該方案升級其餘專案。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-124">When migrating a solution, if you don't choose all projects, the same dialog appears asking you to upgrade the remaining projects from that solution.</span></span> <span data-ttu-id="dc4fd-125">移轉專案之後，您可以用滑鼠右鍵按一下方案總管視窗中的專案，然後選取 [編輯**專案名稱>.csproj]\<** 來查看及修改其內容。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-125">After the project is migrated, you can see and modify its contents by right-clicking the project in the **Solution Explorer** window and selecting **Edit \<project name>.csproj**.</span></span>

<span data-ttu-id="dc4fd-126">已遷移的檔案（*專案. json*、 *global.asax*、 *xproj*和方案檔）會移至*備份*資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-126">Files that were migrated (*project.json*, *global.json*, *.xproj*, and solution file) are moved to a *Backup* folder.</span></span> <span data-ttu-id="dc4fd-127">遷移的方案檔會升級為 Visual Studio 2017 或 Visual Studio 2019，而且您將無法在 Visual Studio 2015 或更早版本中開啟該方案檔。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-127">The migrated solution file is upgraded to Visual Studio 2017 or Visual Studio 2019 and you won't be able to open that solution file in Visual Studio 2015 or earlier versions.</span></span> <span data-ttu-id="dc4fd-128">系統也會自動儲存並開啟名為*UpgradeLog*的檔案，其中包含遷移報表。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-128">A file named *UpgradeLog.htm* that contains a migration report is also saved and opened automatically.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc4fd-129">在 Visual Studio 2019 16.3 版和更新版本中，您無法載入或遷移*xproj*檔案。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-129">In Visual Studio 2019 version 16.3 and later, you cannot load or migrate an *.xproj* file.</span></span> <span data-ttu-id="dc4fd-130">此外，Visual Studio 2015 不提供遷移*xproj*檔案的功能。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-130">Additionally, Visual Studio 2015 doesn't provide the ability to migrate an *.xproj* file.</span></span> <span data-ttu-id="dc4fd-131">如果您使用其中一個 Visual Studio 版本，請安裝適當版本的 Visual Studio，或使用接下來所述的命令列遷移工具。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-131">If you're using one of these Visual Studio versions, either install a suitable version of Visual Studio, or use the command line migration tool that's described next.</span></span>

### <a name="dotnet-migrate"></a><span data-ttu-id="dc4fd-132">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="dc4fd-132">dotnet migrate</span></span>

<span data-ttu-id="dc4fd-133">在命令列案例中，您可以使用 [`dotnet migrate`](../tools/dotnet-migrate.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-133">In the command-line scenario, you can use the [`dotnet migrate`](../tools/dotnet-migrate.md) command.</span></span> <span data-ttu-id="dc4fd-134">它會根據找到的順序，遷移專案、方案或一組資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-134">It migrates a project, a solution, or a set of folders in that order, depending on which ones were found.</span></span> <span data-ttu-id="dc4fd-135">當您移轉專案時，會移轉專案及其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-135">When you migrate a project, the project and all its dependencies are migrated.</span></span>

<span data-ttu-id="dc4fd-136">已遷移的檔案（xproj）會移至*備份*資料夾中（*專案. json*、 *global.asax*和 *.* ）。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-136">Files that were migrated (*project.json*, *global.json*, and *.xproj*) are moved to a *backup* folder.</span></span>

> [!NOTE]
> <span data-ttu-id="dc4fd-137">如果您使用 Visual Studio Code，`dotnet migrate` 命令不會修改 Visual Studio Code 特定的檔案，例如*tasks。*</span><span class="sxs-lookup"><span data-stu-id="dc4fd-137">If you are using Visual Studio Code, the `dotnet migrate` command does not modify Visual Studio Code-specific files such as *tasks.json*.</span></span> <span data-ttu-id="dc4fd-138">這些檔案必須以手動方式變更。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-138">These files need to be changed manually.</span></span>
> <span data-ttu-id="dc4fd-139">如果您使用 Visual Studio 以外的編輯器或整合式開發環境（IDE），也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-139">This is also true if you are using an editor or Integrated Development Environment (IDE) other than Visual Studio.</span></span>

<span data-ttu-id="dc4fd-140">如需有關*專案. json*和 *.csproj*格式的比較，請參閱[project. json 與 .csproj 屬性之間的對應](../tools/project-json-to-csproj.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-140">See [A mapping between project.json and csproj properties](../tools/project-json-to-csproj.md) for a comparison of *project.json* and *.csproj* formats.</span></span>

<span data-ttu-id="dc4fd-141">如果您收到錯誤：</span><span class="sxs-lookup"><span data-stu-id="dc4fd-141">If you get an error:</span></span>

> <span data-ttu-id="dc4fd-142">找不到符合命令 dotnet 的可執行檔-遷移</span><span class="sxs-lookup"><span data-stu-id="dc4fd-142">No executable found matching command dotnet-migrate</span></span>

<span data-ttu-id="dc4fd-143">執行 `dotnet --version` 以查看您所使用的版本。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-143">Run `dotnet --version` to see which version you are using.</span></span> <span data-ttu-id="dc4fd-144">[`dotnet migrate`](../tools/dotnet-migrate.md)是在 .NET Core SDK 1.0.0 中引進，並已在版本3.0.100 中移除。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-144">[`dotnet migrate`](../tools/dotnet-migrate.md) was introduced in .NET Core SDK 1.0.0 and removed in version 3.0.100.</span></span>
<span data-ttu-id="dc4fd-145">如果目前或父目錄中有一個*global. json*檔案，而且其指定的 `sdk` 版本超出此範圍，您就會收到這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-145">You'll get this error if you have a *global.json* file in the current or parent directory, and the `sdk` version it specifies is outside this range.</span></span>

## <a name="migration-from-dnx-to-csproj"></a><span data-ttu-id="dc4fd-146">從 DNX 移轉至 csproj</span><span class="sxs-lookup"><span data-stu-id="dc4fd-146">Migration from DNX to csproj</span></span>

<span data-ttu-id="dc4fd-147">如果您仍使用 DNX 進行 .NET Core 程式開發，則應分兩階段完成您的移轉程序：</span><span class="sxs-lookup"><span data-stu-id="dc4fd-147">If you are still using DNX for .NET Core development, your migration process should be done in two stages:</span></span>

1. <span data-ttu-id="dc4fd-148">使用[現有的 DNX 移轉指引](from-dnx.md)，從 DNX 移轉至啟用 project-json 的 CLI。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-148">Use the [existing DNX migration guidance](from-dnx.md) to migrate from DNX to project-json enabled CLI.</span></span>
2. <span data-ttu-id="dc4fd-149">遵循上一節中的步驟，從 *project.json* 移轉至 *.csproj*。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-149">Follow the steps from the previous section to migrate from *project.json* to *.csproj*.</span></span>

> [!NOTE]
> <span data-ttu-id="dc4fd-150">DNX 已在 .NET Core CLI 的 Preview 1 版期間正式被取代。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-150">DNX has become officially deprecated during the Preview 1 release of the .NET Core CLI.</span></span>

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a><span data-ttu-id="dc4fd-151">從舊版 .NET Core csproj 格式移轉至 RTM csproj</span><span class="sxs-lookup"><span data-stu-id="dc4fd-151">Migration from earlier .NET Core csproj formats to RTM csproj</span></span>

<span data-ttu-id="dc4fd-152">每次工具有新的發行前版本，都會變更及改進 .NET Core csproj 格式。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-152">The .NET Core csproj format has been changing and evolving with each new pre-release version of the tooling.</span></span> <span data-ttu-id="dc4fd-153">目前沒有工具可將您的專案檔從舊版 csproj 移轉至最新版本，因此您必須手動編輯專案檔。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-153">There is no tool that will migrate your project file from earlier versions of csproj to the latest, so you need to manually edit the project file.</span></span> <span data-ttu-id="dc4fd-154">實際步驟取決於您要移轉的專案檔版本。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-154">The actual steps depend on the version of the project file you are migrating.</span></span> <span data-ttu-id="dc4fd-155">以下是根據版本間所發生之變更所要考量的一些指引：</span><span class="sxs-lookup"><span data-stu-id="dc4fd-155">The following is some guidance to consider based on the changes that happened between versions:</span></span>

- <span data-ttu-id="dc4fd-156">從 `<Project>` 項目移除工具版本屬性 (如果存在的話)。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-156">Remove the tools version property from the `<Project>` element, if it exists.</span></span>
- <span data-ttu-id="dc4fd-157">從 `xmlns` 項目移除 XML 命名空間 (`<Project>`)。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-157">Remove the XML namespace (`xmlns`) from the `<Project>` element.</span></span>
- <span data-ttu-id="dc4fd-158">如果不存在，則將 `Sdk` 屬性新增至 `<Project>` 項目，並將它設定為 `Microsoft.NET.Sdk` 或 `Microsoft.NET.Sdk.Web`。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-158">If it doesn't exist, add the `Sdk` attribute to the `<Project>` element and set it to `Microsoft.NET.Sdk` or `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="dc4fd-159">這個屬性會指定專案使用可用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-159">This attribute specifies that the project uses the SDK to be used.</span></span> <span data-ttu-id="dc4fd-160">`Microsoft.NET.Sdk.Web` 適用於 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-160">`Microsoft.NET.Sdk.Web` is used for web apps.</span></span>
- <span data-ttu-id="dc4fd-161">移除專案頂端和底部的 `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` 和 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-161">Remove the `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` and `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` statements from the top and bottom of the project.</span></span> <span data-ttu-id="dc4fd-162">這些 import 陳述式是由 SDK 所隱含，因此專案中不需要有這些陳述式。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-162">These import statements are implied by the SDK, so there is no need for them to be in the project.</span></span>
- <span data-ttu-id="dc4fd-163">如果您的專案中有 `Microsoft.NETCore.App` 或 `NETStandard.Library` `<PackageReference>` 專案，您應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-163">If you have `Microsoft.NETCore.App` or `NETStandard.Library` `<PackageReference>` items in your project, you should remove them.</span></span> <span data-ttu-id="dc4fd-164">這些套件參考是[由 SDK 所隱含](https://aka.ms/sdkimplicitrefs)。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-164">These package references are [implied by the SDK](https://aka.ms/sdkimplicitrefs).</span></span>
- <span data-ttu-id="dc4fd-165">移除 `Microsoft.NET.Sdk` `<PackageReference>` 元素（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-165">Remove the `Microsoft.NET.Sdk` `<PackageReference>` element, if it exists.</span></span> <span data-ttu-id="dc4fd-166">SDK 參考是來自 `Sdk` 項目上的 `<Project>` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-166">The SDK reference comes through the `Sdk` attribute on the `<Project>` element.</span></span>
- <span data-ttu-id="dc4fd-167">移除 [SDK 所隱含](https://en.wikipedia.org/wiki/Glob_(programming))的 [glob](../project-sdk/overview.md#default-compilation-includes)。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-167">Remove the [globs](https://en.wikipedia.org/wiki/Glob_(programming)) that are [implied by the SDK](../project-sdk/overview.md#default-compilation-includes).</span></span> <span data-ttu-id="dc4fd-168">在您的專案中留下這些 Glob 會在建置時造成錯誤，因為編譯項目將會重複。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-168">Leaving these globs in your project will cause an error on build because compile items will be duplicated.</span></span>

<span data-ttu-id="dc4fd-169">完成這些步驟之後，您的專案應該會與 RTM .NET Core csproj 格式完全相容。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-169">After these steps your project should be fully compatible with the RTM .NET Core csproj format.</span></span>

<span data-ttu-id="dc4fd-170">如需從舊的 csproj 格式移轉至新格式的前後範例，請參閱 .NET 部落格上的 [Updating Visual Studio 2017 RC - .NET Core Tooling improvements](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (更新 Visual Studio 2017 RC - .NET Core 工具改進) 文章。</span><span class="sxs-lookup"><span data-stu-id="dc4fd-170">For examples of before and after the migration from old csproj format to the new one, see the [Updating Visual Studio 2017 RC – .NET Core Tooling improvements](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) article on the .NET blog.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc4fd-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4fd-171">See also</span></span>

- [<span data-ttu-id="dc4fd-172">移植、移轉及升級 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="dc4fd-172">Port, Migrate, and Upgrade Visual Studio Projects</span></span>](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
