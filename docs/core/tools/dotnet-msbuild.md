---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117702"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="f836f-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f836f-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f836f-104">名稱</span><span class="sxs-lookup"><span data-stu-id="f836f-104">Name</span></span>

<span data-ttu-id="f836f-105">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="f836f-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f836f-106">概要</span><span class="sxs-lookup"><span data-stu-id="f836f-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="f836f-107">描述</span><span class="sxs-lookup"><span data-stu-id="f836f-107">Description</span></span>

<span data-ttu-id="f836f-108">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="f836f-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="f836f-109">此命令與現有的 MSBuild 命令列用戶端僅針對 SDK 樣式專案具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="f836f-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="f836f-110">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="f836f-110">The options are all the same.</span></span> <span data-ttu-id="f836f-111">如需可用選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="f836f-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="f836f-112">[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="f836f-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="f836f-113">`dotnet build` 較常用來建置專案，但 `dotnet msbuild` 可提供您較多的控制權。</span><span class="sxs-lookup"><span data-stu-id="f836f-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="f836f-114">例如，如果您有想要執行的特定目標 (但不執行建置目標)，您可能會想要使用 `dotnet msbuild`。</span><span class="sxs-lookup"><span data-stu-id="f836f-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="f836f-115">範例</span><span class="sxs-lookup"><span data-stu-id="f836f-115">Examples</span></span>

* <span data-ttu-id="f836f-116">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="f836f-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="f836f-117">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="f836f-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="f836f-118">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="f836f-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="f836f-119">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="f836f-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -pp
  ```
