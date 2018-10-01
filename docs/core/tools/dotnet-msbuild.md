---
title: dotnet msbuild 命令 - .NET Core CLI
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47421186"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="834ce-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="834ce-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="834ce-104">名稱</span><span class="sxs-lookup"><span data-stu-id="834ce-104">Name</span></span>

<span data-ttu-id="834ce-105">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="834ce-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="834ce-106">概要</span><span class="sxs-lookup"><span data-stu-id="834ce-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="834ce-107">描述</span><span class="sxs-lookup"><span data-stu-id="834ce-107">Description</span></span>

<span data-ttu-id="834ce-108">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="834ce-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="834ce-109">命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="834ce-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="834ce-110">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="834ce-110">The options are all the same.</span></span> <span data-ttu-id="834ce-111">如需可用選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="834ce-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="834ce-112">範例</span><span class="sxs-lookup"><span data-stu-id="834ce-112">Examples</span></span>

<span data-ttu-id="834ce-113">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="834ce-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="834ce-114">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="834ce-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild -p:Configuration=Release`

<span data-ttu-id="834ce-115">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="834ce-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="834ce-116">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="834ce-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild -pp`
