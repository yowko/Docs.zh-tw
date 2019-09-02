---
title: dotnet add package 命令
description: "'dotnet add package' 命令提供方便的選項，將 NuGet 套件參考新增至專案。"
ms.date: 06/26/2019
ms.openlocfilehash: 124e42b1d5897802bb1698c8e22b7e76031391a2
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105170"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="83c95-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="83c95-103">dotnet add package</span></span>

<span data-ttu-id="83c95-104">**本文適用於：✓** .NET Core 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="83c95-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="83c95-105">名稱</span><span class="sxs-lookup"><span data-stu-id="83c95-105">Name</span></span>

<span data-ttu-id="83c95-106">`dotnet add package` - 將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="83c95-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83c95-107">概要</span><span class="sxs-lookup"><span data-stu-id="83c95-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="83c95-108">說明</span><span class="sxs-lookup"><span data-stu-id="83c95-108">Description</span></span>

<span data-ttu-id="83c95-109">`dotnet add package` 命令提供方便的選項，可將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="83c95-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="83c95-110">執行命令之後，會執行相容性檢查，確保套件與專案中的架構相容。</span><span class="sxs-lookup"><span data-stu-id="83c95-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="83c95-111">如果通過檢查，系統會將 `<PackageReference>` 元素新增到專案檔，並執行 [dotnet restore](dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="83c95-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="83c95-112">例如，將 `Newtonsoft.Json` 新增至 *ToDo.csproj* 會產生類似下例的輸出：</span><span class="sxs-lookup"><span data-stu-id="83c95-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="83c95-113">*ToDo.csproj* 檔案現在會包含參考套件的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素。</span><span class="sxs-lookup"><span data-stu-id="83c95-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="83c95-114">引數</span><span class="sxs-lookup"><span data-stu-id="83c95-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="83c95-115">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="83c95-115">Specifies the project file.</span></span> <span data-ttu-id="83c95-116">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="83c95-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="83c95-117">要新增的套件參考。</span><span class="sxs-lookup"><span data-stu-id="83c95-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="83c95-118">選項</span><span class="sxs-lookup"><span data-stu-id="83c95-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="83c95-119">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增套件參考。</span><span class="sxs-lookup"><span data-stu-id="83c95-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="83c95-120">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="83c95-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="83c95-121">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="83c95-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="83c95-122">自 .NET Core 2.1 SDK 2.1.400 版起可用。</span><span class="sxs-lookup"><span data-stu-id="83c95-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="83c95-123">新增套件參考，而不執行還原預覽和相容性檢查。</span><span class="sxs-lookup"><span data-stu-id="83c95-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="83c95-124">還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="83c95-124">The directory where to restore the packages.</span></span> <span data-ttu-id="83c95-125">Windows 上的預設套件還原位置為 `%userprofile%\.nuget\packages`，macOS 和 Linux 上則為 `~/.nuget/packages`。</span><span class="sxs-lookup"><span data-stu-id="83c95-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="83c95-126">如需詳細資訊，請參閱[在 NuGet 中管理全域套件、快取和暫存資料夾](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)。</span><span class="sxs-lookup"><span data-stu-id="83c95-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="83c95-127">要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="83c95-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="83c95-128">套件的版本。</span><span class="sxs-lookup"><span data-stu-id="83c95-128">Version of the package.</span></span> <span data-ttu-id="83c95-129">請參閱 [NuGet 套件版本控制](https://docs.microsoft.com/nuget/reference/package-versioning) \(部分機器翻譯\)。</span><span class="sxs-lookup"><span data-stu-id="83c95-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="83c95-130">範例</span><span class="sxs-lookup"><span data-stu-id="83c95-130">Examples</span></span>

- <span data-ttu-id="83c95-131">將 `Newtonsoft.Json` NuGet 套件新增至專案：</span><span class="sxs-lookup"><span data-stu-id="83c95-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```console
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="83c95-132">將特定版本的套件新增至專案：</span><span class="sxs-lookup"><span data-stu-id="83c95-132">Add a specific version of a package to a project:</span></span>

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="83c95-133">使用特定 NuGet 來源新增套件：</span><span class="sxs-lookup"><span data-stu-id="83c95-133">Add a package using a specific NuGet source:</span></span>

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="83c95-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83c95-134">See also</span></span>

- [<span data-ttu-id="83c95-135">在 NuGet 中管理全域套件、快取和暫存資料夾</span><span class="sxs-lookup"><span data-stu-id="83c95-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="83c95-136">NuGet 套件版本控制</span><span class="sxs-lookup"><span data-stu-id="83c95-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
