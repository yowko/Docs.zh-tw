---
title: dotnet help 命令
description: dotnet help 命令會顯示指定命令更詳細的線上文件。
ms.date: 12/04/2018
ms.openlocfilehash: 8694494720cdb9a540754fdf79eeb99d5dbe61ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631994"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="a3fb9-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="a3fb9-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="a3fb9-104">名稱</span><span class="sxs-lookup"><span data-stu-id="a3fb9-104">Name</span></span>

<span data-ttu-id="a3fb9-105">`dotnet help` - 顯示指定命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a3fb9-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a3fb9-106">概要</span><span class="sxs-lookup"><span data-stu-id="a3fb9-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="a3fb9-107">說明</span><span class="sxs-lookup"><span data-stu-id="a3fb9-107">Description</span></span>

<span data-ttu-id="a3fb9-108">`dotnet help` 命令會在 docs.microsoft.com 開啟參考頁面，提供指定命令的更詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a3fb9-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="a3fb9-109">引數</span><span class="sxs-lookup"><span data-stu-id="a3fb9-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="a3fb9-110">.NET Core CLI 命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3fb9-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="a3fb9-111">如需有效 CLI 命令的清單，請參閱 [CLI 命令](index.md#cli-commands)。</span><span class="sxs-lookup"><span data-stu-id="a3fb9-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="a3fb9-112">選項</span><span class="sxs-lookup"><span data-stu-id="a3fb9-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="a3fb9-113">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a3fb9-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a3fb9-114">範例</span><span class="sxs-lookup"><span data-stu-id="a3fb9-114">Examples</span></span>

* <span data-ttu-id="a3fb9-115">開啟 [dotnet new](dotnet-new.md) 命令的文件頁面：</span><span class="sxs-lookup"><span data-stu-id="a3fb9-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```
