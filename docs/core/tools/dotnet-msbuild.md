---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803166"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="a6245-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a6245-103">dotnet msbuild</span></span>

<span data-ttu-id="a6245-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a6245-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a6245-105">Name</span><span class="sxs-lookup"><span data-stu-id="a6245-105">Name</span></span>

<span data-ttu-id="a6245-106">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="a6245-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="a6245-107">注意：如果有多個方案或專案檔，可能需要指定。</span><span class="sxs-lookup"><span data-stu-id="a6245-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a6245-108">概要</span><span class="sxs-lookup"><span data-stu-id="a6245-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="a6245-109">描述</span><span class="sxs-lookup"><span data-stu-id="a6245-109">Description</span></span>

<span data-ttu-id="a6245-110">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="a6245-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="a6245-111">此命令與僅適用于 SDK 樣式專案的現有 MSBuild 命令列用戶端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="a6245-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="a6245-112">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="a6245-112">The options are all the same.</span></span> <span data-ttu-id="a6245-113">如需可用選項的詳細資訊，請參閱[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="a6245-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="a6245-114">[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore`。</span><span class="sxs-lookup"><span data-stu-id="a6245-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="a6245-115">當您不想要建立專案，而且您有想要執行的特定目標時，請使用 `dotnet build` 或 `dotnet msbuild` ，並指定目標。</span><span class="sxs-lookup"><span data-stu-id="a6245-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="a6245-116">範例</span><span class="sxs-lookup"><span data-stu-id="a6245-116">Examples</span></span>

- <span data-ttu-id="a6245-117">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="a6245-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="a6245-118">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="a6245-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="a6245-119">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="a6245-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="a6245-120">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="a6245-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
