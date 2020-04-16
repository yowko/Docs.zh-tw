---
title: dotnet add package 命令
description: "'dotnet add package' 命令提供方便的選項，將 NuGet 套件參考新增至專案。"
ms.date: 02/14/2020
ms.openlocfilehash: 24a25cdab2aab30d52f8407adfda437f47437290
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463748"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="53ba6-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="53ba6-103">dotnet add package</span></span>

<span data-ttu-id="53ba6-104">**本文適用於:✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="53ba6-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="53ba6-105">名稱</span><span class="sxs-lookup"><span data-stu-id="53ba6-105">Name</span></span>

<span data-ttu-id="53ba6-106">`dotnet add package` - 將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="53ba6-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="53ba6-107">概要</span><span class="sxs-lookup"><span data-stu-id="53ba6-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="53ba6-108">描述</span><span class="sxs-lookup"><span data-stu-id="53ba6-108">Description</span></span>

<span data-ttu-id="53ba6-109">`dotnet add package` 命令提供方便的選項，可將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="53ba6-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="53ba6-110">執行命令之後，會執行相容性檢查，確保套件與專案中的架構相容。</span><span class="sxs-lookup"><span data-stu-id="53ba6-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="53ba6-111">如果通過檢查，系統會將 `<PackageReference>` 元素新增到專案檔，並執行 [dotnet restore](dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="53ba6-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="53ba6-112">例如，將 `Newtonsoft.Json` 新增至 *ToDo.csproj* 會產生類似下例的輸出：</span><span class="sxs-lookup"><span data-stu-id="53ba6-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
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

<span data-ttu-id="53ba6-113">*ToDo.csproj* 檔案現在會包含參考套件的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素。</span><span class="sxs-lookup"><span data-stu-id="53ba6-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="53ba6-114">引數</span><span class="sxs-lookup"><span data-stu-id="53ba6-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="53ba6-115">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="53ba6-115">Specifies the project file.</span></span> <span data-ttu-id="53ba6-116">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="53ba6-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="53ba6-117">要新增的套件參考。</span><span class="sxs-lookup"><span data-stu-id="53ba6-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="53ba6-118">選項。</span><span class="sxs-lookup"><span data-stu-id="53ba6-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="53ba6-119">僅當定位特定[框架](../../standard/frameworks.md)時,才添加包引用。</span><span class="sxs-lookup"><span data-stu-id="53ba6-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="53ba6-120">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="53ba6-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="53ba6-121">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="53ba6-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="53ba6-122">自 .NET Core 2.1 SDK 2.1.400 版起可用。</span><span class="sxs-lookup"><span data-stu-id="53ba6-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="53ba6-123">新增套件參考，而不執行還原預覽和相容性檢查。</span><span class="sxs-lookup"><span data-stu-id="53ba6-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="53ba6-124">還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="53ba6-124">The directory where to restore the packages.</span></span> <span data-ttu-id="53ba6-125">Windows 上的預設套件還原位置為 `%userprofile%\.nuget\packages`，macOS 和 Linux 上則為 `~/.nuget/packages`。</span><span class="sxs-lookup"><span data-stu-id="53ba6-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="53ba6-126">如需詳細資訊，請參閱[在 NuGet 中管理全域套件、快取和暫存資料夾](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)。</span><span class="sxs-lookup"><span data-stu-id="53ba6-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="53ba6-127">要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="53ba6-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="53ba6-128">套件的版本。</span><span class="sxs-lookup"><span data-stu-id="53ba6-128">Version of the package.</span></span> <span data-ttu-id="53ba6-129">請參閱 [NuGet 套件版本控制](https://docs.microsoft.com/nuget/reference/package-versioning) \(部分機器翻譯\)。</span><span class="sxs-lookup"><span data-stu-id="53ba6-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="53ba6-130">範例</span><span class="sxs-lookup"><span data-stu-id="53ba6-130">Examples</span></span>

- <span data-ttu-id="53ba6-131">將 `Newtonsoft.Json` NuGet 套件新增至專案：</span><span class="sxs-lookup"><span data-stu-id="53ba6-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="53ba6-132">將特定版本的套件新增至專案：</span><span class="sxs-lookup"><span data-stu-id="53ba6-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="53ba6-133">使用特定 NuGet 來源新增套件：</span><span class="sxs-lookup"><span data-stu-id="53ba6-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="53ba6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ba6-134">See also</span></span>

- [<span data-ttu-id="53ba6-135">在 NuGet 中管理全域套件、快取和暫存資料夾</span><span class="sxs-lookup"><span data-stu-id="53ba6-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="53ba6-136">NuGet 套件版本控制</span><span class="sxs-lookup"><span data-stu-id="53ba6-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
