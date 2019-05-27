---
title: dotnet-add reference 命令
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
ms.date: 04/24/2019
ms.openlocfilehash: e90f95527d4f14c7851ccd8d30201daaaaefa2ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631931"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="8a3d9-103">dotnet-add reference</span><span class="sxs-lookup"><span data-stu-id="8a3d9-103">dotnet-add reference</span></span>

<span data-ttu-id="8a3d9-104">**本文適用於：✓** .NET Core 1.x SDK 及更新版本</span><span class="sxs-lookup"><span data-stu-id="8a3d9-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="8a3d9-105">名稱</span><span class="sxs-lookup"><span data-stu-id="8a3d9-105">Name</span></span>

<span data-ttu-id="8a3d9-106">`dotnet add reference` - 新增專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8a3d9-107">概要</span><span class="sxs-lookup"><span data-stu-id="8a3d9-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="8a3d9-108">說明</span><span class="sxs-lookup"><span data-stu-id="8a3d9-108">Description</span></span>

<span data-ttu-id="8a3d9-109">`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="8a3d9-110">執行命令之後，系統就會將 [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) 元素新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="8a3d9-111">引數</span><span class="sxs-lookup"><span data-stu-id="8a3d9-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="8a3d9-112">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-112">Specifies the project file.</span></span> <span data-ttu-id="8a3d9-113">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="8a3d9-114">要新增的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="8a3d9-115">指定一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-115">Specify one or more projects.</span></span> <span data-ttu-id="8a3d9-116">Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="8a3d9-117">選項</span><span class="sxs-lookup"><span data-stu-id="8a3d9-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="8a3d9-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8a3d9-119">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="8a3d9-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8a3d9-120">範例</span><span class="sxs-lookup"><span data-stu-id="8a3d9-120">Examples</span></span>

* <span data-ttu-id="8a3d9-121">新增專案參考：</span><span class="sxs-lookup"><span data-stu-id="8a3d9-121">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="8a3d9-122">新增目前目錄中專案的多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="8a3d9-122">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="8a3d9-123">在 Linux/Unix 上使用 Glob 模式新增多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="8a3d9-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
