---
title: "dotnet list reference 命令 - .NET Core CLI"
description: "dotnet list reference 命令提供方便的選項，以列出專案對專案參考。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-list-reference"></a><span data-ttu-id="70344-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="70344-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="70344-104">name</span><span class="sxs-lookup"><span data-stu-id="70344-104">Name</span></span>

<span data-ttu-id="70344-105">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="70344-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70344-106">概要</span><span class="sxs-lookup"><span data-stu-id="70344-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="70344-107">說明</span><span class="sxs-lookup"><span data-stu-id="70344-107">Description</span></span>

<span data-ttu-id="70344-108">`dotnet list reference` 命令提供方便的選項，以列出指定專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="70344-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="70344-109">引數</span><span class="sxs-lookup"><span data-stu-id="70344-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="70344-110">指定要用於列出參考的專案檔。</span><span class="sxs-lookup"><span data-stu-id="70344-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="70344-111">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="70344-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="70344-112">選項</span><span class="sxs-lookup"><span data-stu-id="70344-112">Options</span></span>

`-h|--help`

<span data-ttu-id="70344-113">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="70344-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="70344-114">範例</span><span class="sxs-lookup"><span data-stu-id="70344-114">Examples</span></span>

<span data-ttu-id="70344-115">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="70344-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="70344-116">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="70344-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`

