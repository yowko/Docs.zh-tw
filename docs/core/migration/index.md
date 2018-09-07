---
title: 將 .NET Core 移轉至 csproj 格式
description: 將 .NET Core project.json 移轉至 csproj
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.openlocfilehash: da1995ed3b77cb802d1f3d04e6d741809de20927
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872428"
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a><span data-ttu-id="ba461-103">將 .NET Core 專案移轉至 .csproj 格式</span><span class="sxs-lookup"><span data-stu-id="ba461-103">Migrating .NET Core projects to the .csproj format</span></span>

<span data-ttu-id="ba461-104">本文將討論 .NET Core 專案的移轉案例，並將介紹下列三種移轉案例：</span><span class="sxs-lookup"><span data-stu-id="ba461-104">This document will cover migration scenarios for .NET Core projects and will go over the following three migration scenarios:</span></span>

1. [<span data-ttu-id="ba461-105">從 *project.json* 的有效最新結構描述移轉至 *csproj*</span><span class="sxs-lookup"><span data-stu-id="ba461-105">Migration from a valid latest schema of *project.json* to *csproj*</span></span>](#migration-from-projectjson-to-csproj)
2. [<span data-ttu-id="ba461-106">從 DNX 移轉至 csproj</span><span class="sxs-lookup"><span data-stu-id="ba461-106">Migration from DNX to csproj</span></span>](#migration-from-dnx-to-csproj)
3. [<span data-ttu-id="ba461-107">從 RC3 和舊版 .NET Core csproj 專案移轉至最終格式</span><span class="sxs-lookup"><span data-stu-id="ba461-107">Migration from RC3 and previous .NET Core csproj projects to the final format</span></span>](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a><span data-ttu-id="ba461-108">從 project.json 移轉至 csproj</span><span class="sxs-lookup"><span data-stu-id="ba461-108">Migration from project.json to csproj</span></span>

<span data-ttu-id="ba461-109">您可以使用下列其中一種方法從 *project.json* 移轉至 *.csproj*：</span><span class="sxs-lookup"><span data-stu-id="ba461-109">Migration from *project.json* to *.csproj* can be done using one of the following methods:</span></span>

- [<span data-ttu-id="ba461-110">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ba461-110">Visual Studio 2017</span></span>](#visual-studio-2017)
- [<span data-ttu-id="ba461-111">dotnet migrate 命令列工具</span><span class="sxs-lookup"><span data-stu-id="ba461-111">dotnet migrate command-line tool</span></span>](#dotnet-migrate)

<span data-ttu-id="ba461-112">這兩種方法使用相同的基礎引擎來移轉專案，因此結果會相同。</span><span class="sxs-lookup"><span data-stu-id="ba461-112">Both methods use the same underlying engine to migrate the projects, so the results will be the same for both.</span></span> <span data-ttu-id="ba461-113">在大部分情況下，您只需要使用這兩種方式之一即可將 *project.json* 移轉至 *csproj*，而不需要進一步手動編輯專案檔。</span><span class="sxs-lookup"><span data-stu-id="ba461-113">In most cases, using one of these two ways to migrate the *project.json* to *csproj* is the only thing that is needed and no further manual editing of the project file is necessary.</span></span> <span data-ttu-id="ba461-114">所產生的 *.csproj* 檔案將會以包含目錄的相同名稱命名。</span><span class="sxs-lookup"><span data-stu-id="ba461-114">The resulting *.csproj* file will be named the same as the containing directory name.</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="ba461-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ba461-115">Visual Studio 2017</span></span>

<span data-ttu-id="ba461-116">當您開啟 *.xproj* 檔或參考 *.xproj* 檔的方案檔時，[單向升級] 對話方塊會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ba461-116">When you open a *.xproj* file or a solution file which references *.xproj* files, the **One-way upgrade** dialog appears.</span></span> <span data-ttu-id="ba461-117">此對話方塊會顯示要移轉的專案。</span><span class="sxs-lookup"><span data-stu-id="ba461-117">The dialog displays the projects to be migrated.</span></span>
<span data-ttu-id="ba461-118">如果您開啟方案檔，則會列出方案檔中指定的所有專案。</span><span class="sxs-lookup"><span data-stu-id="ba461-118">If you open a solution file, all the projects specified in the solution file will be listed.</span></span> <span data-ttu-id="ba461-119">檢閱要移轉的專案清單，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ba461-119">Review the list of projects to be migrated and select **OK**.</span></span>

![[單向升級] 對話方塊顯示要移轉的專案清單](media/one-way-upgrade.jpg)

<span data-ttu-id="ba461-121">Visual Studio 會自動移轉所選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="ba461-121">Visual Studio will migrate the projects chosen automatically.</span></span> <span data-ttu-id="ba461-122">移轉方案時，如果您未選擇所有專案，則會出現相同的對話方塊，請您升級該方案中的其餘專案。</span><span class="sxs-lookup"><span data-stu-id="ba461-122">When migrating a solution, if you don't choose all projects, the same dialog will appear asking you to upgrade the remaining projects from that solution.</span></span> <span data-ttu-id="ba461-123">移轉專案之後，您可以用滑鼠右鍵按一下方案總管視窗中的專案，然後選取 [編輯\<專案名稱>.csproj] 來查看及修改其內容。</span><span class="sxs-lookup"><span data-stu-id="ba461-123">After the project is migrated, you can see and modify its contents by right-clicking the project in the **Solution Explorer** window and selecting **Edit \<project name>.csproj**.</span></span>

<span data-ttu-id="ba461-124">已移轉的檔案 (*project.json*、*global.json*、*.xproj* 和方案檔) 將會移至「備份」資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba461-124">Files that were migrated (*project.json*, *global.json*, *.xproj* and solution file) will be moved to a *Backup* folder.</span></span> <span data-ttu-id="ba461-125">移轉的方案檔將會升級為 Visual Studio 2017，您將無法在舊版 Visual Studio 中開啟該方案檔。</span><span class="sxs-lookup"><span data-stu-id="ba461-125">The solution file that is migrated will be upgraded to Visual Studio 2017 and you won't be able to open that solution file in previous versions of Visual Studio.</span></span>
<span data-ttu-id="ba461-126">此外，也會儲存並自動開啟名為 *UpgradeLog.htm* 的檔案，其中包含移轉報告。</span><span class="sxs-lookup"><span data-stu-id="ba461-126">A file named *UpgradeLog.htm* is also saved and automatically opened that contains a migration report.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba461-127">Visual Studio 2015 中未提供此新工具，因此您無法使用該版 Visual Studio 來移轉專案。</span><span class="sxs-lookup"><span data-stu-id="ba461-127">The new tooling is not available in Visual Studio 2015, so you cannot migrate your projects using that version of Visual Studio.</span></span>

### <a name="dotnet-migrate"></a><span data-ttu-id="ba461-128">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="ba461-128">dotnet migrate</span></span>

<span data-ttu-id="ba461-129">在命令列案例中，您可以使用 [`dotnet migrate`](../tools/dotnet-migrate.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="ba461-129">In the command-line scenario, you can use the [`dotnet migrate`](../tools/dotnet-migrate.md) command.</span></span> <span data-ttu-id="ba461-130">它將會根據找到的先後順序，依序移轉專案、方案或一組資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba461-130">It will migrate a project, a solution or a set of folders in that order, depending on which ones were found.</span></span>
<span data-ttu-id="ba461-131">當您移轉專案時，會移轉專案及其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="ba461-131">When you migrate a project, the project and all its dependencies are migrated.</span></span>

<span data-ttu-id="ba461-132">已移轉的檔案 (*project.json*、*global.json* 和 *.xproj*) 將會移至「備份」資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba461-132">Files that were migrated (*project.json*, *global.json* and *.xproj*) will be moved to a *backup* folder.</span></span>

> [!NOTE]
> <span data-ttu-id="ba461-133">如果您使用 Visual Studio Code，`dotnet migrate` 命令不會修改 Visual Studio Code 特定的檔案，例如 `tasks.json`。</span><span class="sxs-lookup"><span data-stu-id="ba461-133">If you are using Visual Studio Code, the `dotnet migrate` command will not modify Visual Studio Code-specific files such as `tasks.json`.</span></span> <span data-ttu-id="ba461-134">這些檔案必須以手動方式變更。</span><span class="sxs-lookup"><span data-stu-id="ba461-134">These files need to be changed manually.</span></span>
> <span data-ttu-id="ba461-135">這也適用於使用 Project Ryder 或是 Visual Studio 以外的任何編輯器或整合式開發環境 (IDE) 的情況。</span><span class="sxs-lookup"><span data-stu-id="ba461-135">This is also true if you are using Project Ryder or any editor or Integrated Development Environment (IDE) other than Visual Studio.</span></span>

<span data-ttu-id="ba461-136">如需 project.json 和 csproj 格式的比較，請參閱 [project.json 與 csproj 屬性的對應](../tools/project-json-to-csproj.md)。</span><span class="sxs-lookup"><span data-stu-id="ba461-136">See [A mapping between project.json and csproj properties](../tools/project-json-to-csproj.md) for a comparison of project.json and csproj formats.</span></span>

### <a name="common-issues"></a><span data-ttu-id="ba461-137">常見問題</span><span class="sxs-lookup"><span data-stu-id="ba461-137">Common issues</span></span>

- <span data-ttu-id="ba461-138">若您收到錯誤：「找不到符合命令 dotnet-migrate 的可執行檔」：</span><span class="sxs-lookup"><span data-stu-id="ba461-138">If you get an error: "No executable found matching command dotnet-migrate":</span></span>

<span data-ttu-id="ba461-139">執行 `dotnet --version` 以查看您所使用的版本。</span><span class="sxs-lookup"><span data-stu-id="ba461-139">Run `dotnet --version` to see which version you are using.</span></span> <span data-ttu-id="ba461-140">[`dotnet migrate`](../tools/dotnet-migrate.md) 需要 .NET Core CLI RC3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ba461-140">[`dotnet migrate`](../tools/dotnet-migrate.md) requires .NET Core CLI RC3 or higher.</span></span>
<span data-ttu-id="ba461-141">如果您目前的目錄或父目錄中有 *global.json* 檔案且 `sdk` 版本設定為舊版，則會收到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba461-141">You’ll get this error if you have a *global.json* file in the current or parent directory and the `sdk` version is set to an older version.</span></span>

## <a name="migration-from-dnx-to-csproj"></a><span data-ttu-id="ba461-142">從 DNX 移轉至 csproj</span><span class="sxs-lookup"><span data-stu-id="ba461-142">Migration from DNX to csproj</span></span>

<span data-ttu-id="ba461-143">如果您仍使用 DNX 進行 .NET Core 程式開發，則應分兩階段完成您的移轉程序：</span><span class="sxs-lookup"><span data-stu-id="ba461-143">If you are still using DNX for .NET Core development, your migration process should be done in two stages:</span></span>

1. <span data-ttu-id="ba461-144">使用[現有的 DNX 移轉指引](from-dnx.md)，從 DNX 移轉至啟用 project-json 的 CLI。</span><span class="sxs-lookup"><span data-stu-id="ba461-144">Use the [existing DNX migration guidance](from-dnx.md) to migrate from DNX to project-json enabled CLI.</span></span>
2. <span data-ttu-id="ba461-145">遵循上一節中的步驟，從 *project.json* 移轉至 *.csproj*。</span><span class="sxs-lookup"><span data-stu-id="ba461-145">Follow the steps from the previous section to migrate from *project.json* to *.csproj*.</span></span>  

> [!NOTE]
> <span data-ttu-id="ba461-146">DNX 已在 .NET Core CLI 的 Preview 1 版期間正式被取代。</span><span class="sxs-lookup"><span data-stu-id="ba461-146">DNX has become officially deprecated during the Preview 1 release of the .NET Core CLI.</span></span>

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a><span data-ttu-id="ba461-147">從舊版 .NET Core csproj 格式移轉至 RTM csproj</span><span class="sxs-lookup"><span data-stu-id="ba461-147">Migration from earlier .NET Core csproj formats to RTM csproj</span></span>

<span data-ttu-id="ba461-148">每次工具有新的發行前版本，都會變更及改進 .NET Core csproj 格式。</span><span class="sxs-lookup"><span data-stu-id="ba461-148">The .NET Core csproj format has been changing and evolving with each new pre-release version of the tooling.</span></span> <span data-ttu-id="ba461-149">目前沒有工具可將您的專案檔從舊版 csproj 移轉至最新版本，因此您必須手動編輯專案檔。</span><span class="sxs-lookup"><span data-stu-id="ba461-149">There is no tool that will migrate your project file from earlier versions of csproj to the latest, so you need to manually edit the project file.</span></span> <span data-ttu-id="ba461-150">實際步驟取決於您要移轉的專案檔版本。</span><span class="sxs-lookup"><span data-stu-id="ba461-150">The actual steps depend on the version of the project file you are migrating.</span></span> <span data-ttu-id="ba461-151">以下是根據版本間所發生之變更所要考量的一些指引：</span><span class="sxs-lookup"><span data-stu-id="ba461-151">The following is some guidance to consider based on the changes that happened between versions:</span></span>

* <span data-ttu-id="ba461-152">從 `<Project>` 項目移除工具版本屬性 (如果存在的話)。</span><span class="sxs-lookup"><span data-stu-id="ba461-152">Remove the tools version property from the `<Project>` element, if it exists.</span></span>
* <span data-ttu-id="ba461-153">從 `<Project>` 項目移除 XML 命名空間 (`xmlns`)。</span><span class="sxs-lookup"><span data-stu-id="ba461-153">Remove the XML namespace (`xmlns`) from the `<Project>` element.</span></span>
* <span data-ttu-id="ba461-154">如果不存在，則將 `Sdk` 屬性新增至 `<Project>` 項目，並將它設定為 `Microsoft.NET.Sdk` 或 `Microsoft.NET.Sdk.Web`。</span><span class="sxs-lookup"><span data-stu-id="ba461-154">If it doesn't exist, add the `Sdk` attribute to the `<Project>` element and set it to `Microsoft.NET.Sdk` or `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="ba461-155">這個屬性會指定專案使用可用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="ba461-155">This attribute specifies that the project uses the SDK to be used.</span></span> <span data-ttu-id="ba461-156">`Microsoft.NET.Sdk.Web` 適用於 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba461-156">`Microsoft.NET.Sdk.Web` is used for web apps.</span></span>
* <span data-ttu-id="ba461-157">移除專案頂端和底部的 `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` 和 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ba461-157">Remove the `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` and `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` statements from the top and bottom of the project.</span></span> <span data-ttu-id="ba461-158">這些 import 陳述式是由 SDK 所隱含，因此專案中不需要有這些陳述式。</span><span class="sxs-lookup"><span data-stu-id="ba461-158">These import statements are implied by the SDK, so there is no need for them to be in the project.</span></span>
* <span data-ttu-id="ba461-159">如果您的專案中有 `Microsoft.NETCore.App` 或 `NETStandard.Library` `<PackageReference>` 項目，則應該加以移除。</span><span class="sxs-lookup"><span data-stu-id="ba461-159">If you have `Microsoft.NETCore.App` or `NETStandard.Library` `<PackageReference>` items in your project, you should remove them.</span></span> <span data-ttu-id="ba461-160">這些套件參考是[由 SDK 所隱含](https://aka.ms/sdkimplicitrefs)。</span><span class="sxs-lookup"><span data-stu-id="ba461-160">These package references are [implied by the SDK](https://aka.ms/sdkimplicitrefs).</span></span>
* <span data-ttu-id="ba461-161">移除 `Microsoft.NET.Sdk` `<PackageReference>` 項目 (如果存在的話)。</span><span class="sxs-lookup"><span data-stu-id="ba461-161">Remove the `Microsoft.NET.Sdk` `<PackageReference>` element, if it exists.</span></span> <span data-ttu-id="ba461-162">SDK 參考是來自 `<Project>` 項目上的 `Sdk` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba461-162">The SDK reference comes through the `Sdk` attribute on the `<Project>` element.</span></span>
* <span data-ttu-id="ba461-163">移除 [SDK 所隱含](../tools/csproj.md#default-compilation-includes-in-net-core-projects)的 [glob](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="ba461-163">Remove the [globs](https://en.wikipedia.org/wiki/Glob_(programming)) that are [implied by the SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects).</span></span> <span data-ttu-id="ba461-164">在您的專案中留下這些 Glob 會在建置時造成錯誤，因為編譯項目將會重複。</span><span class="sxs-lookup"><span data-stu-id="ba461-164">Leaving these globs in your project will cause an error on build because compile items will be duplicated.</span></span>

<span data-ttu-id="ba461-165">完成這些步驟之後，您的專案應該會與 RTM .NET Core csproj 格式完全相容。</span><span class="sxs-lookup"><span data-stu-id="ba461-165">After these steps your project should be fully compatible with the RTM .NET Core csproj format.</span></span>

<span data-ttu-id="ba461-166">如需從舊的 csproj 格式移轉至新格式的前後範例，請參閱 .NET 部落格上的 [Updating Visual Studio 2017 RC - .NET Core Tooling improvements](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (更新 Visual Studio 2017 RC - .NET Core 工具改進) 文章。</span><span class="sxs-lookup"><span data-stu-id="ba461-166">For examples of before and after the migration from old csproj format to the new one, see the [Updating Visual Studio 2017 RC – .NET Core Tooling improvements](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) article on the .NET blog.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba461-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba461-167">See also</span></span>

- [<span data-ttu-id="ba461-168">移植、移轉及升級 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="ba461-168">Port, Migrate, and Upgrade Visual Studio Projects</span></span>](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
