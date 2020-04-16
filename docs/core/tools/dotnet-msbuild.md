---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463617"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="b93e0-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b93e0-103">dotnet msbuild</span></span>

<span data-ttu-id="b93e0-104">**本文適用於:✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="b93e0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b93e0-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b93e0-105">Name</span></span>

<span data-ttu-id="b93e0-106">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="b93e0-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b93e0-107">概要</span><span class="sxs-lookup"><span data-stu-id="b93e0-107">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="b93e0-108">描述</span><span class="sxs-lookup"><span data-stu-id="b93e0-108">Description</span></span>

<span data-ttu-id="b93e0-109">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="b93e0-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="b93e0-110">該命令具有與僅針對 SDK 樣式專案的現有 MSBuild 命令行用戶端完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="b93e0-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="b93e0-111">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="b93e0-111">The options are all the same.</span></span> <span data-ttu-id="b93e0-112">有關可用選項的詳細資訊,請參閱[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="b93e0-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="b93e0-113">[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="b93e0-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="b93e0-114">[dotnet 產生](dotnet-build.md)更通常用於產生項目,但由於它總是執行產生目標,因此可以在不想產生專案時`dotnet msbuild`使用 。</span><span class="sxs-lookup"><span data-stu-id="b93e0-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="b93e0-115">例如,如果您有要在不生成項目的情況下運行的特定目標,請使用`dotnet msbuild`並指定目標。</span><span class="sxs-lookup"><span data-stu-id="b93e0-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="b93e0-116">範例</span><span class="sxs-lookup"><span data-stu-id="b93e0-116">Examples</span></span>

- <span data-ttu-id="b93e0-117">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="b93e0-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="b93e0-118">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="b93e0-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="b93e0-119">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="b93e0-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="b93e0-120">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="b93e0-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
