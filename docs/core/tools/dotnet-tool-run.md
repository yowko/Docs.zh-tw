---
title: dotnet 工具執行命令
description: Dotnet 工具執行命令會叫用本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543877"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="c6836-103">dotnet 工具執行</span><span class="sxs-lookup"><span data-stu-id="c6836-103">dotnet tool run</span></span>

<span data-ttu-id="c6836-104">**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="c6836-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c6836-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c6836-105">Name</span></span>

<span data-ttu-id="c6836-106">`dotnet tool run`-叫用本機工具。</span><span class="sxs-lookup"><span data-stu-id="c6836-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6836-107">概要</span><span class="sxs-lookup"><span data-stu-id="c6836-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="c6836-108">描述</span><span class="sxs-lookup"><span data-stu-id="c6836-108">Description</span></span>

<span data-ttu-id="c6836-109">`dotnet tool run` 命令會搜尋目前目錄範圍內的工具資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="c6836-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="c6836-110">當它找到指定之工具的參考時，就會執行工具。</span><span class="sxs-lookup"><span data-stu-id="c6836-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="c6836-111">如需詳細資訊，請參閱叫[用本機工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="c6836-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="c6836-112">引數</span><span class="sxs-lookup"><span data-stu-id="c6836-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="c6836-113">要執行之工具的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="c6836-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="c6836-114">選項。</span><span class="sxs-lookup"><span data-stu-id="c6836-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="c6836-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c6836-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="c6836-116">範例</span><span class="sxs-lookup"><span data-stu-id="c6836-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="c6836-117">執行 `dotnetsay` 本機工具。</span><span class="sxs-lookup"><span data-stu-id="c6836-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6836-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6836-118">See also</span></span>

- [<span data-ttu-id="c6836-119">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="c6836-119">.NET Core tools</span></span>](global-tools.md)
