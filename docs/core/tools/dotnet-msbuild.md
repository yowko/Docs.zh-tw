---
title: dotnet msbuild 命令 - .NET Core CLI
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: c51c058391de4925afd4339fe84e28500d692e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="700c3-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="700c3-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="700c3-104">名稱</span><span class="sxs-lookup"><span data-stu-id="700c3-104">Name</span></span>

<span data-ttu-id="700c3-105">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="700c3-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="700c3-106">概要</span><span class="sxs-lookup"><span data-stu-id="700c3-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="700c3-107">描述</span><span class="sxs-lookup"><span data-stu-id="700c3-107">Description</span></span>

<span data-ttu-id="700c3-108">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="700c3-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="700c3-109">命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="700c3-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="700c3-110">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="700c3-110">The options are all the same.</span></span> <span data-ttu-id="700c3-111">使用 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)來取得可用選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="700c3-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="700c3-112">範例</span><span class="sxs-lookup"><span data-stu-id="700c3-112">Examples</span></span>

<span data-ttu-id="700c3-113">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="700c3-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="700c3-114">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="700c3-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="700c3-115">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="700c3-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="700c3-116">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="700c3-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
