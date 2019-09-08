---
title: dotnet-add reference 命令
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
ms.date: 06/26/2019
ms.openlocfilehash: 867596058aad8f9c38918e6d6657709d0d0699b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784042"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="b28db-103">dotnet-add reference</span><span class="sxs-lookup"><span data-stu-id="b28db-103">dotnet-add reference</span></span>

<span data-ttu-id="b28db-104">**本文適用於：✓** .NET Core 1.x SDK 及更新版本</span><span class="sxs-lookup"><span data-stu-id="b28db-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="b28db-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b28db-105">Name</span></span>

<span data-ttu-id="b28db-106">`dotnet add reference` - 新增專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="b28db-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b28db-107">概要</span><span class="sxs-lookup"><span data-stu-id="b28db-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="b28db-108">說明</span><span class="sxs-lookup"><span data-stu-id="b28db-108">Description</span></span>

<span data-ttu-id="b28db-109">`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="b28db-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="b28db-110">執行命令之後， `<ProjectReference>`元素會加入至專案檔。</span><span class="sxs-lookup"><span data-stu-id="b28db-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="b28db-111">引數</span><span class="sxs-lookup"><span data-stu-id="b28db-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="b28db-112">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="b28db-112">Specifies the project file.</span></span> <span data-ttu-id="b28db-113">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="b28db-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="b28db-114">要新增的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="b28db-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="b28db-115">指定一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="b28db-115">Specify one or more projects.</span></span> <span data-ttu-id="b28db-116">Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="b28db-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="b28db-117">選項</span><span class="sxs-lookup"><span data-stu-id="b28db-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="b28db-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b28db-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b28db-119">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="b28db-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`--interactive`**

  <span data-ttu-id="b28db-120">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="b28db-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="b28db-121">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b28db-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="b28db-122">範例</span><span class="sxs-lookup"><span data-stu-id="b28db-122">Examples</span></span>

* <span data-ttu-id="b28db-123">新增專案參考：</span><span class="sxs-lookup"><span data-stu-id="b28db-123">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="b28db-124">新增目前目錄中專案的多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="b28db-124">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="b28db-125">在 Linux/Unix 上使用 Glob 模式新增多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="b28db-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
