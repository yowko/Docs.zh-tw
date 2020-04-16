---
title: 點網加入引言指令
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: f2bd67d181784c4858b8971d05053d196df7818e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463738"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="37cdc-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="37cdc-103">dotnet add reference</span></span>

<span data-ttu-id="37cdc-104">**本文適用於:✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="37cdc-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37cdc-105">名稱</span><span class="sxs-lookup"><span data-stu-id="37cdc-105">Name</span></span>

<span data-ttu-id="37cdc-106">`dotnet add reference` - 新增專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="37cdc-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37cdc-107">概要</span><span class="sxs-lookup"><span data-stu-id="37cdc-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="37cdc-108">描述</span><span class="sxs-lookup"><span data-stu-id="37cdc-108">Description</span></span>

<span data-ttu-id="37cdc-109">`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="37cdc-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="37cdc-110">執行命令之後，系統就會將 `<ProjectReference>` 元素新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="37cdc-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="37cdc-111">引數</span><span class="sxs-lookup"><span data-stu-id="37cdc-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="37cdc-112">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="37cdc-112">Specifies the project file.</span></span> <span data-ttu-id="37cdc-113">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="37cdc-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="37cdc-114">要新增的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="37cdc-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="37cdc-115">指定一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="37cdc-115">Specify one or more projects.</span></span> <span data-ttu-id="37cdc-116">Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="37cdc-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="37cdc-117">選項。</span><span class="sxs-lookup"><span data-stu-id="37cdc-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="37cdc-118">僅當定位特定[框架](../../standard/frameworks.md)時,才添加專案引用。</span><span class="sxs-lookup"><span data-stu-id="37cdc-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="37cdc-119">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="37cdc-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="37cdc-120">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="37cdc-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="37cdc-121">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="37cdc-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="37cdc-122">範例</span><span class="sxs-lookup"><span data-stu-id="37cdc-122">Examples</span></span>

- <span data-ttu-id="37cdc-123">新增專案參考：</span><span class="sxs-lookup"><span data-stu-id="37cdc-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="37cdc-124">新增目前目錄中專案的多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="37cdc-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="37cdc-125">在 Linux/Unix 上使用 Glob 模式新增多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="37cdc-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
