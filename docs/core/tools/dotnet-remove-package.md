---
title: dotnet remove package 命令 - .NET Core CLI
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ed6086bfdfadaa06494c857fc74687f1273af971
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696854"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="44e79-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="44e79-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="44e79-104">名稱</span><span class="sxs-lookup"><span data-stu-id="44e79-104">Name</span></span>

<span data-ttu-id="44e79-105">`dotnet remove package` - 從專案檔中移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="44e79-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="44e79-106">概要</span><span class="sxs-lookup"><span data-stu-id="44e79-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="44e79-107">描述</span><span class="sxs-lookup"><span data-stu-id="44e79-107">Description</span></span>

<span data-ttu-id="44e79-108">`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="44e79-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="44e79-109">引數</span><span class="sxs-lookup"><span data-stu-id="44e79-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="44e79-110">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="44e79-110">Specifies the project file.</span></span> <span data-ttu-id="44e79-111">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="44e79-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="44e79-112">要移除的套件參考。</span><span class="sxs-lookup"><span data-stu-id="44e79-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="44e79-113">選項</span><span class="sxs-lookup"><span data-stu-id="44e79-113">Options</span></span>

`-h|--help`

<span data-ttu-id="44e79-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="44e79-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="44e79-115">範例</span><span class="sxs-lookup"><span data-stu-id="44e79-115">Examples</span></span>

<span data-ttu-id="44e79-116">從目前目錄中的專案移除 `Newtonsoft.Json` NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="44e79-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`