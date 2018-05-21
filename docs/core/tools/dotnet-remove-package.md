---
title: dotnet remove package 命令 - .NET Core CLI
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 6a18be1a853119be245623e8fa0a0e44ed819e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="5768a-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="5768a-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5768a-104">名稱</span><span class="sxs-lookup"><span data-stu-id="5768a-104">Name</span></span>

<span data-ttu-id="5768a-105">`dotnet remove package` - 從專案檔中移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="5768a-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5768a-106">概要</span><span class="sxs-lookup"><span data-stu-id="5768a-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="5768a-107">描述</span><span class="sxs-lookup"><span data-stu-id="5768a-107">Description</span></span>

<span data-ttu-id="5768a-108">`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="5768a-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5768a-109">引數</span><span class="sxs-lookup"><span data-stu-id="5768a-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5768a-110">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="5768a-110">Specifies the project file.</span></span> <span data-ttu-id="5768a-111">如果未指定，命令會在目前的目錄中搜尋一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="5768a-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5768a-112">要移除的套件參考。</span><span class="sxs-lookup"><span data-stu-id="5768a-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="5768a-113">選項</span><span class="sxs-lookup"><span data-stu-id="5768a-113">Options</span></span>

`-h|--help`

<span data-ttu-id="5768a-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5768a-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5768a-115">範例</span><span class="sxs-lookup"><span data-stu-id="5768a-115">Examples</span></span>

<span data-ttu-id="5768a-116">從目前目錄中的專案移除 `Newtonsoft.Json` NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="5768a-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
