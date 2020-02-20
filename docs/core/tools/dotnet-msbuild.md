---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503674"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="819d4-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="819d4-103">dotnet msbuild</span></span>

<span data-ttu-id="819d4-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="819d4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="819d4-105">名稱</span><span class="sxs-lookup"><span data-stu-id="819d4-105">Name</span></span>

<span data-ttu-id="819d4-106">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="819d4-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="819d4-107">概要</span><span class="sxs-lookup"><span data-stu-id="819d4-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="819d4-108">描述</span><span class="sxs-lookup"><span data-stu-id="819d4-108">Description</span></span>

<span data-ttu-id="819d4-109">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="819d4-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="819d4-110">此命令與僅適用于 SDK 樣式專案的現有 MSBuild 命令列用戶端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="819d4-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="819d4-111">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="819d4-111">The options are all the same.</span></span> <span data-ttu-id="819d4-112">如需可用選項的詳細資訊，請參閱[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="819d4-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="819d4-113">[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="819d4-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="819d4-114">[dotnet build](dotnet-build.md)較常用來建立專案，但因為它一律會執行組建目標，所以當您不想要建立專案時，可以使用 `dotnet msbuild`。</span><span class="sxs-lookup"><span data-stu-id="819d4-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="819d4-115">例如，如果您有想要執行而不建立專案的特定目標，請使用 `dotnet msbuild` 並指定目標。</span><span class="sxs-lookup"><span data-stu-id="819d4-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="819d4-116">範例</span><span class="sxs-lookup"><span data-stu-id="819d4-116">Examples</span></span>

- <span data-ttu-id="819d4-117">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="819d4-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="819d4-118">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="819d4-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="819d4-119">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="819d4-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="819d4-120">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="819d4-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
