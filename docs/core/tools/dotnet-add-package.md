---
title: dotnet add package 命令 - .NET Core CLI
description: "'dotnet add package' 命令提供方便的選項，將 NuGet 套件參考新增至專案。"
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 3a8752ff83e069d21ebbda346efef34b17360e3b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-package"></a><span data-ttu-id="1e73e-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="1e73e-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1e73e-104">名稱</span><span class="sxs-lookup"><span data-stu-id="1e73e-104">Name</span></span>

<span data-ttu-id="1e73e-105">`dotnet add package` - 將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="1e73e-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1e73e-106">概要</span><span class="sxs-lookup"><span data-stu-id="1e73e-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="1e73e-107">描述</span><span class="sxs-lookup"><span data-stu-id="1e73e-107">Description</span></span>

<span data-ttu-id="1e73e-108">`dotnet add package` 命令提供方便的選項，可將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="1e73e-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="1e73e-109">執行命令之後，會執行相容性檢查，確保套件與專案中的架構相容。</span><span class="sxs-lookup"><span data-stu-id="1e73e-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="1e73e-110">如果通過檢查，系統會將 `<PackageReference>` 元素新增到專案檔，並執行 [dotnet restore](dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="1e73e-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1e73e-111">例如，將 `Newtonsoft.Json` 新增至 *ToDo.csproj* 會產生類似下例的輸出：</span><span class="sxs-lookup"><span data-stu-id="1e73e-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="1e73e-112">*ToDo.csproj* 檔案現在會包含參考套件的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素。</span><span class="sxs-lookup"><span data-stu-id="1e73e-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="1e73e-113">引數</span><span class="sxs-lookup"><span data-stu-id="1e73e-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="1e73e-114">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="1e73e-114">Specifies the project file.</span></span> <span data-ttu-id="1e73e-115">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="1e73e-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="1e73e-116">要新增的套件參考。</span><span class="sxs-lookup"><span data-stu-id="1e73e-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="1e73e-117">選項</span><span class="sxs-lookup"><span data-stu-id="1e73e-117">Options</span></span>

`-h|--help`

<span data-ttu-id="1e73e-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="1e73e-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="1e73e-119">套件的版本。</span><span class="sxs-lookup"><span data-stu-id="1e73e-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="1e73e-120">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增套件參考。</span><span class="sxs-lookup"><span data-stu-id="1e73e-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="1e73e-121">新增套件參考，而不執行還原預覽和相容性檢查。</span><span class="sxs-lookup"><span data-stu-id="1e73e-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="1e73e-122">在還原作業期間，使用特定 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="1e73e-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="1e73e-123">將套件還原至指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="1e73e-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="1e73e-124">範例</span><span class="sxs-lookup"><span data-stu-id="1e73e-124">Examples</span></span>

<span data-ttu-id="1e73e-125">將 `Newtonsoft.Json` NuGet 套件新增至專案：</span><span class="sxs-lookup"><span data-stu-id="1e73e-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="1e73e-126">將特定版本的套件新增至專案：</span><span class="sxs-lookup"><span data-stu-id="1e73e-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="1e73e-127">使用特定 NuGet 來源新增套件：</span><span class="sxs-lookup"><span data-stu-id="1e73e-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
