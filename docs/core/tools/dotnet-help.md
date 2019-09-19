---
title: dotnet help 命令
description: dotnet help 命令會顯示指定命令更詳細的線上文件。
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117715"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="a33e3-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="a33e3-103">dotnet help reference</span></span>

<span data-ttu-id="a33e3-104">**本文適用于：✓** .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a33e3-104">**This article applies to: ✓** .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="a33e3-105">名稱</span><span class="sxs-lookup"><span data-stu-id="a33e3-105">Name</span></span>

<span data-ttu-id="a33e3-106">`dotnet help` - 顯示指定命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a33e3-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a33e3-107">概要</span><span class="sxs-lookup"><span data-stu-id="a33e3-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="a33e3-108">說明</span><span class="sxs-lookup"><span data-stu-id="a33e3-108">Description</span></span>

<span data-ttu-id="a33e3-109">`dotnet help` 命令會在 docs.microsoft.com 開啟參考頁面，提供指定命令的更詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a33e3-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="a33e3-110">引數</span><span class="sxs-lookup"><span data-stu-id="a33e3-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="a33e3-111">.NET Core CLI 命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="a33e3-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="a33e3-112">如需有效 CLI 命令的清單，請參閱 [CLI 命令](index.md#cli-commands)。</span><span class="sxs-lookup"><span data-stu-id="a33e3-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="a33e3-113">選項</span><span class="sxs-lookup"><span data-stu-id="a33e3-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="a33e3-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a33e3-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a33e3-115">範例</span><span class="sxs-lookup"><span data-stu-id="a33e3-115">Examples</span></span>

* <span data-ttu-id="a33e3-116">開啟 [dotnet new](dotnet-new.md) 命令的文件頁面：</span><span class="sxs-lookup"><span data-stu-id="a33e3-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
