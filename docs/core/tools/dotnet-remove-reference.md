---
title: dotnet remove reference 命令
description: dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158329"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="02bc3-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="02bc3-103">dotnet remove reference</span></span>

<span data-ttu-id="02bc3-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="02bc3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="02bc3-105">名稱</span><span class="sxs-lookup"><span data-stu-id="02bc3-105">Name</span></span>

<span data-ttu-id="02bc3-106">`dotnet remove reference`-移除專案對專案（P2P）參考。</span><span class="sxs-lookup"><span data-stu-id="02bc3-106">`dotnet remove reference` - Removes project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="02bc3-107">概要</span><span class="sxs-lookup"><span data-stu-id="02bc3-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="02bc3-108">描述</span><span class="sxs-lookup"><span data-stu-id="02bc3-108">Description</span></span>

<span data-ttu-id="02bc3-109">`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="02bc3-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="02bc3-110">引數</span><span class="sxs-lookup"><span data-stu-id="02bc3-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="02bc3-111">目標專案檔。</span><span class="sxs-lookup"><span data-stu-id="02bc3-111">Target project file.</span></span> <span data-ttu-id="02bc3-112">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="02bc3-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="02bc3-113">要移除的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="02bc3-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="02bc3-114">您可以指定一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="02bc3-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="02bc3-115">以 Unix/Linux 為基礎的終端機上支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="02bc3-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="02bc3-116">選項。</span><span class="sxs-lookup"><span data-stu-id="02bc3-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="02bc3-117">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="02bc3-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="02bc3-118">只有在以使用 TFM 格式的特定[架構](../../standard/frameworks.md)為目標時，才會移除參考。</span><span class="sxs-lookup"><span data-stu-id="02bc3-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

## <a name="examples"></a><span data-ttu-id="02bc3-119">範例</span><span class="sxs-lookup"><span data-stu-id="02bc3-119">Examples</span></span>

- <span data-ttu-id="02bc3-120">從指定的專案中移除專案參考：</span><span class="sxs-lookup"><span data-stu-id="02bc3-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="02bc3-121">從目前目錄中的專案移除多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="02bc3-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="02bc3-122">在 Unix/Linux 上使用 Glob 模式移除多個專案參考︰</span><span class="sxs-lookup"><span data-stu-id="02bc3-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
