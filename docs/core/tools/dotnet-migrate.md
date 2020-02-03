---
title: dotnet migrate 命令
description: dotnet migrate 命令會移轉專案及其所有相依性。
ms.date: 01/07/2020
ms.openlocfilehash: b81669d3e4cffeaf10bea39639410d5f06579d84
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734149"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="2d915-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="2d915-103">dotnet migrate</span></span>

<span data-ttu-id="2d915-104">**本文適用于：** ✔️ .net CORE 1.x sdk ✔️ .net CORE 2.x sdk</span><span class="sxs-lookup"><span data-stu-id="2d915-104">**This article applies to:** ✔️ .NET Core 1.x SDK ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="2d915-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2d915-105">Name</span></span>

<span data-ttu-id="2d915-106">`dotnet migrate` - 將 Preview 2 .NET Core 專案移轉至 .NET Core SDK 型專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2d915-107">概要</span><span class="sxs-lookup"><span data-stu-id="2d915-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2d915-108">描述</span><span class="sxs-lookup"><span data-stu-id="2d915-108">Description</span></span>

<span data-ttu-id="2d915-109">此命令已被取代。</span><span class="sxs-lookup"><span data-stu-id="2d915-109">This command is deprecated.</span></span> <span data-ttu-id="2d915-110">從 .NET Core 3.0 SDK 開始，不再提供 `dotnet migrate` 命令。</span><span class="sxs-lookup"><span data-stu-id="2d915-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="2d915-111">它只能將 Preview 2 .NET Core 專案遷移至不支援的 1.x .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="2d915-112">根據預設，命令會移轉根專案和根專案包含的任何專案參考。</span><span class="sxs-lookup"><span data-stu-id="2d915-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="2d915-113">可以在執行階段使用 `--skip-project-references` 選項停用此行為。</span><span class="sxs-lookup"><span data-stu-id="2d915-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="2d915-114">可針對下列資產進行移轉：</span><span class="sxs-lookup"><span data-stu-id="2d915-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="2d915-115">指定要移轉之 *project.json* 檔案的單一專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="2d915-116">於 *global.json* 檔案中指定的所有目錄，方法是傳遞 *global.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d915-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="2d915-117">*solution.sln* 檔案，移轉方案參考的專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="2d915-118">指定之目錄的所有子目錄，以遞迴方式進行。</span><span class="sxs-lookup"><span data-stu-id="2d915-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="2d915-119">`dotnet migrate` 命令會在 *目錄 (若目錄不存在則會建立) 中保留移轉的*project.json`backup` 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d915-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="2d915-120">使用 `--skip-backup` 選項會覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="2d915-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="2d915-121">根據預設，移轉作業會將移轉程序的狀態輸出到標準輸出 (STDOUT)。</span><span class="sxs-lookup"><span data-stu-id="2d915-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="2d915-122">如果使用 `--report-file <REPORT_FILE>` 選項，則輸出會儲存到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="2d915-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="2d915-123">`dotnet migrate` 命令只支援有效的 Preview 2 *project.json* 型專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="2d915-124">這表示您無法使用它將 DNX 或 Preview 1 *project.json* 型專案直接移轉到 MSBuild/csproj 專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="2d915-125">您必須先手動將專案移轉到 Preview 2 *project.json* 型專案，然後再使用 `dotnet migrate` 命令移轉該專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="2d915-126">引數</span><span class="sxs-lookup"><span data-stu-id="2d915-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="2d915-127">下列其中一項的路徑：</span><span class="sxs-lookup"><span data-stu-id="2d915-127">The path to one of the following:</span></span>

* <span data-ttu-id="2d915-128">要移轉的 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d915-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="2d915-129">*global.json* 檔案：會移轉 *global.json* 中指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2d915-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="2d915-130">*solution.sln* 檔案：會移轉方案參考的專案。</span><span class="sxs-lookup"><span data-stu-id="2d915-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="2d915-131">要移轉的目錄：會在指定目錄內遞迴地搜尋要移轉的 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d915-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="2d915-132">如果未指定，則預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="2d915-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="2d915-133">選項</span><span class="sxs-lookup"><span data-stu-id="2d915-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="2d915-134">將移轉報告檔案輸出為 JSON，而非使用者訊息。</span><span class="sxs-lookup"><span data-stu-id="2d915-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="2d915-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2d915-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="2d915-136">除了主控台外，也將移轉報告輸出到檔案。</span><span class="sxs-lookup"><span data-stu-id="2d915-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="2d915-137">略過移轉專案參考。</span><span class="sxs-lookup"><span data-stu-id="2d915-137">Skip migrating project references.</span></span> <span data-ttu-id="2d915-138">根據預設，專案參考是以遞迴方式移轉。</span><span class="sxs-lookup"><span data-stu-id="2d915-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="2d915-139">成功移轉後，略過將 *project.json*、*global.json* 和 *\*.xproj* 移動至 `backup` 目錄。</span><span class="sxs-lookup"><span data-stu-id="2d915-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="2d915-140">要用於移轉的範本 csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d915-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="2d915-141">根據預設，會使用 `dotnet new console` 所置放的相同範本。</span><span class="sxs-lookup"><span data-stu-id="2d915-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="2d915-142">在已移轉之應用程式中參考的 SDK 套件版本。</span><span class="sxs-lookup"><span data-stu-id="2d915-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="2d915-143">預設為 `dotnet new` 中的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="2d915-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="2d915-144">要使用之 xproj 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d915-144">The path to the xproj file to use.</span></span> <span data-ttu-id="2d915-145">當專案目錄中有多個 xproj 時為必要。</span><span class="sxs-lookup"><span data-stu-id="2d915-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="2d915-146">範例</span><span class="sxs-lookup"><span data-stu-id="2d915-146">Examples</span></span>

<span data-ttu-id="2d915-147">移轉目前目錄中的專案和所有其專案對專案相依性：</span><span class="sxs-lookup"><span data-stu-id="2d915-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="2d915-148">移轉 *global.json* 檔案包含的所有專案：</span><span class="sxs-lookup"><span data-stu-id="2d915-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="2d915-149">只移轉目前的專案而不移轉專案對專案 (P2P) 相依性。</span><span class="sxs-lookup"><span data-stu-id="2d915-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="2d915-150">此外，使用特定的 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="2d915-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
