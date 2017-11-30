---
title: "dotnet migrate 命令 - .NET Core CLI"
description: "dotnet migrate 命令會移轉專案及其所有相依性。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: d2c99df730d90e0a6b69197cf036c62073cf8749
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="dotnet-migrate"></a><span data-ttu-id="0d6ee-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0d6ee-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0d6ee-104">name</span><span class="sxs-lookup"><span data-stu-id="0d6ee-104">Name</span></span>

<span data-ttu-id="0d6ee-105">`dotnet migrate` - 將 Preview 2 .NET Core 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d6ee-106">概要</span><span class="sxs-lookup"><span data-stu-id="0d6ee-106">Synopsis</span></span>

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a><span data-ttu-id="0d6ee-107">描述</span><span class="sxs-lookup"><span data-stu-id="0d6ee-107">Description</span></span>

<span data-ttu-id="0d6ee-108">`dotnet migrate` 命令會將有效的 Preview 2 *project.json* 型專案移轉至有效的 .NET Core SDK 1.0 *csproj* 專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span> 

<span data-ttu-id="0d6ee-109">根據預設，命令會移轉根專案和根專案包含的任何專案參考。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="0d6ee-110">可以在執行階段使用 `--skip-project-references` 選項停用此行為。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span> 

<span data-ttu-id="0d6ee-111">會針對下列項目進行移轉：</span><span class="sxs-lookup"><span data-stu-id="0d6ee-111">Migration is performed on the following:</span></span>

* <span data-ttu-id="0d6ee-112">指定要移轉之 *project.json* 檔案的單一專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="0d6ee-113">於 *global.json* 檔案中指定的所有目錄，方法是傳遞 *global.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="0d6ee-114">*solution.sln* 檔案，移轉方案參考的專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="0d6ee-115">指定之目錄的所有子目錄，以遞迴方式進行。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-115">On all sub-directories of the given directory recursively.</span></span>

<span data-ttu-id="0d6ee-116">`dotnet migrate` 命令會在 `backup` 目錄 (若目錄不存在則會建立) 中保留移轉的 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="0d6ee-117">使用覆寫這個行為`--skip-backup`選項。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="0d6ee-118">根據預設，移轉作業會將移轉程序的狀態輸出到標準輸出 (STDOUT)。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="0d6ee-119">如果使用 `--report-file <REPORT_FILE>` 選項，則輸出會儲存到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span> 

<span data-ttu-id="0d6ee-120">`dotnet migrate` 命令只支援有效的 Preview 2 *project.json* 型專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="0d6ee-121">這表示您無法使用它將 DNX 或 Preview 1 *project.json* 型專案直接移轉到 MSBuild/csproj 專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="0d6ee-122">您必須先手動將專案移轉到 Preview 2 *project.json* 型專案，然後再使用 `dotnet migrate` 命令移轉該專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="0d6ee-123">引數</span><span class="sxs-lookup"><span data-stu-id="0d6ee-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="0d6ee-124">下列其中一項的路徑：</span><span class="sxs-lookup"><span data-stu-id="0d6ee-124">The path to one of the following:</span></span>

* <span data-ttu-id="0d6ee-125">要移轉的 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="0d6ee-126">*global.json* 檔案，它會移轉 *global.json* 中指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-126">a *global.json* file, it will migrate the folders specified in *global.json*.</span></span>
* <span data-ttu-id="0d6ee-127">*solution.sln* 檔案，它會移轉方案參考的專案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-127">a *solution.sln* file, it will migrate the projects referenced in the solution.</span></span>
* <span data-ttu-id="0d6ee-128">要移轉的目錄，它會遞迴地搜尋要移轉的 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-128">a directory to migrate, it will recursively search for *project.json* files to migrate.</span></span>

<span data-ttu-id="0d6ee-129">如果未指定，則預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="0d6ee-130">選項</span><span class="sxs-lookup"><span data-stu-id="0d6ee-130">Options</span></span>

`-h|--help`

<span data-ttu-id="0d6ee-131">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-131">Prints out a short help for the command.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="0d6ee-132">要用於移轉的範本 csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-132">Template csproj file to use for migration.</span></span> <span data-ttu-id="0d6ee-133">根據預設，會使用 `dotnet new console` 所置放的相同範本。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-133">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="0d6ee-134">在已移轉之應用程式中參考的 SDK 套件版本。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-134">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="0d6ee-135">預設為 `dotnet new` 中的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-135">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="0d6ee-136">要使用之 xproj 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-136">The path to the xproj file to use.</span></span> <span data-ttu-id="0d6ee-137">當專案目錄中有多個 xproj 時為必要。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-137">Required when there is more than one xproj in a project directory.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="0d6ee-138">略過移轉專案參考。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-138">Skip migrating project references.</span></span> <span data-ttu-id="0d6ee-139">根據預設，專案參考是以遞迴方式移轉。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-139">By default, project references are migrated recursively.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="0d6ee-140">除了主控台外，也將移轉報告輸出到檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-140">Output migration report to a file in addition to the console.</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="0d6ee-141">將移轉報告檔案輸出為 JSON，而非使用者訊息。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-141">Output migration report file as JSON rather than user messages.</span></span>

`--skip-backup`

<span data-ttu-id="0d6ee-142">成功移轉後，略過將 *project.json*、*global.json* 和 *\*.xproj* 移動至 `backup` 目錄。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-142">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

## <a name="examples"></a><span data-ttu-id="0d6ee-143">範例</span><span class="sxs-lookup"><span data-stu-id="0d6ee-143">Examples</span></span>

<span data-ttu-id="0d6ee-144">移轉目前目錄中的專案和所有其專案對專案相依性：</span><span class="sxs-lookup"><span data-stu-id="0d6ee-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="0d6ee-145">移轉 *global.json* 檔案包含的所有專案：</span><span class="sxs-lookup"><span data-stu-id="0d6ee-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="0d6ee-146">只移轉目前的專案而不移轉專案對專案 (P2P) 相依性。</span><span class="sxs-lookup"><span data-stu-id="0d6ee-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="0d6ee-147">此外，使用特定的 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="0d6ee-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
