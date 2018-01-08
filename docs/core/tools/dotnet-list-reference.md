---
title: "dotnet list reference 命令 - .NET Core CLI"
description: "dotnet list reference 命令提供方便的選項，以列出專案對專案參考。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: a4ceadb6d070d7997e75b472624bbe2c1650396d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="3a85c-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="3a85c-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3a85c-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3a85c-104">Name</span></span>

<span data-ttu-id="3a85c-105">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="3a85c-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3a85c-106">概要</span><span class="sxs-lookup"><span data-stu-id="3a85c-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="3a85c-107">描述</span><span class="sxs-lookup"><span data-stu-id="3a85c-107">Description</span></span>

<span data-ttu-id="3a85c-108">`dotnet list reference` 命令提供方便的選項，以列出指定專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="3a85c-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="3a85c-109">引數</span><span class="sxs-lookup"><span data-stu-id="3a85c-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="3a85c-110">指定要用於列出參考的專案檔。</span><span class="sxs-lookup"><span data-stu-id="3a85c-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="3a85c-111">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="3a85c-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="3a85c-112">選項</span><span class="sxs-lookup"><span data-stu-id="3a85c-112">Options</span></span>

`-h|--help`

<span data-ttu-id="3a85c-113">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3a85c-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="3a85c-114">範例</span><span class="sxs-lookup"><span data-stu-id="3a85c-114">Examples</span></span>

<span data-ttu-id="3a85c-115">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="3a85c-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="3a85c-116">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="3a85c-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
