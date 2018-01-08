---
title: "dotnet msbuild 命令 - .NET Core CLI"
description: "dotnet msbuild 命令提供對 MSBuild 命令列的存取。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 682b49d44c0fb8242eeb3cb8bf4d158f73b4b9a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="78a37-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="78a37-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="78a37-104">名稱</span><span class="sxs-lookup"><span data-stu-id="78a37-104">Name</span></span>

<span data-ttu-id="78a37-105">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="78a37-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="78a37-106">概要</span><span class="sxs-lookup"><span data-stu-id="78a37-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="78a37-107">描述</span><span class="sxs-lookup"><span data-stu-id="78a37-107">Description</span></span>

<span data-ttu-id="78a37-108">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="78a37-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="78a37-109">命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="78a37-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="78a37-110">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="78a37-110">The options are all the same.</span></span> <span data-ttu-id="78a37-111">使用 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)來取得可用選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="78a37-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="78a37-112">範例</span><span class="sxs-lookup"><span data-stu-id="78a37-112">Examples</span></span>

<span data-ttu-id="78a37-113">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="78a37-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="78a37-114">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="78a37-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="78a37-115">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="78a37-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="78a37-116">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="78a37-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
