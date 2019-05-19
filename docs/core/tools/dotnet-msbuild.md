---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 12/03/2018
ms.openlocfilehash: 983fae6f4ecf875da0b155a668009984b5df50de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632034"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="83edb-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="83edb-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="83edb-104">名稱</span><span class="sxs-lookup"><span data-stu-id="83edb-104">Name</span></span>

<span data-ttu-id="83edb-105">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="83edb-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83edb-106">概要</span><span class="sxs-lookup"><span data-stu-id="83edb-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="83edb-107">說明</span><span class="sxs-lookup"><span data-stu-id="83edb-107">Description</span></span>

<span data-ttu-id="83edb-108">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="83edb-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="83edb-109">此命令與現有的 MSBuild 命令列用戶端僅針對 SDK 樣式專案具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="83edb-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="83edb-110">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="83edb-110">The options are all the same.</span></span> <span data-ttu-id="83edb-111">如需可用選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="83edb-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="83edb-112">[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="83edb-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="83edb-113">`dotnet build` 較常用來建置專案，但 `dotnet msbuild` 可提供您較多的控制權。</span><span class="sxs-lookup"><span data-stu-id="83edb-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="83edb-114">例如，如果您有想要執行的特定目標 (但不執行建置目標)，您可能會想要使用 `dotnet msbuild`。</span><span class="sxs-lookup"><span data-stu-id="83edb-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="83edb-115">範例</span><span class="sxs-lookup"><span data-stu-id="83edb-115">Examples</span></span>

* <span data-ttu-id="83edb-116">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="83edb-116">Build a project and its dependencies:</span></span>

  ```console
  dotnet msbuild
  ```

* <span data-ttu-id="83edb-117">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="83edb-117">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="83edb-118">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="83edb-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="83edb-119">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="83edb-119">See the whole project with all targets included by the SDK:</span></span>

  ```console
  dotnet msbuild -pp
  ```
