---
title: 點網增加參考命令
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503795"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="a0acc-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a0acc-103">dotnet add reference</span></span>

<span data-ttu-id="a0acc-104">**本文適用于：✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="a0acc-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="a0acc-105">名稱</span><span class="sxs-lookup"><span data-stu-id="a0acc-105">Name</span></span>

<span data-ttu-id="a0acc-106">`dotnet add reference` - 新增專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="a0acc-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a0acc-107">概要</span><span class="sxs-lookup"><span data-stu-id="a0acc-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="a0acc-108">描述</span><span class="sxs-lookup"><span data-stu-id="a0acc-108">Description</span></span>

<span data-ttu-id="a0acc-109">`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="a0acc-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="a0acc-110">執行命令之後，系統就會將 `<ProjectReference>` 元素新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="a0acc-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="a0acc-111">引數</span><span class="sxs-lookup"><span data-stu-id="a0acc-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="a0acc-112">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="a0acc-112">Specifies the project file.</span></span> <span data-ttu-id="a0acc-113">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="a0acc-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="a0acc-114">要新增的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="a0acc-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="a0acc-115">指定一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="a0acc-115">Specify one or more projects.</span></span> <span data-ttu-id="a0acc-116">Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="a0acc-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="a0acc-117">選項。</span><span class="sxs-lookup"><span data-stu-id="a0acc-117">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="a0acc-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a0acc-118">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0acc-119">僅當定位特定[框架](../../standard/frameworks.md)時，才添加專案引用。</span><span class="sxs-lookup"><span data-stu-id="a0acc-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`--interactive`**

  <span data-ttu-id="a0acc-120">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="a0acc-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="a0acc-121">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a0acc-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="a0acc-122">範例</span><span class="sxs-lookup"><span data-stu-id="a0acc-122">Examples</span></span>

- <span data-ttu-id="a0acc-123">新增專案參考：</span><span class="sxs-lookup"><span data-stu-id="a0acc-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="a0acc-124">新增目前目錄中專案的多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="a0acc-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="a0acc-125">在 Linux/Unix 上使用 Glob 模式新增多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="a0acc-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
