---
title: dotnet tool run 命令
description: Dotnet tool run 命令會叫用本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 116ecb61748a0ca70ed385b279b11b939748f4a8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634151"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="f5426-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="f5426-103">dotnet tool run</span></span>

<span data-ttu-id="f5426-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f5426-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f5426-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f5426-105">Name</span></span>

<span data-ttu-id="f5426-106">`dotnet tool run` -叫用本機工具。</span><span class="sxs-lookup"><span data-stu-id="f5426-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f5426-107">概要</span><span class="sxs-lookup"><span data-stu-id="f5426-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="f5426-108">描述</span><span class="sxs-lookup"><span data-stu-id="f5426-108">Description</span></span>

<span data-ttu-id="f5426-109">此 `dotnet tool run` 命令會搜尋目前目錄範圍內的工具資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="f5426-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="f5426-110">當它找到指定之工具的參考時，就會執行工具。</span><span class="sxs-lookup"><span data-stu-id="f5426-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="f5426-111">如需詳細資訊，請參閱叫 [用本機工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="f5426-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="f5426-112">引數</span><span class="sxs-lookup"><span data-stu-id="f5426-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="f5426-113">要執行之工具的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="f5426-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="f5426-114">選項</span><span class="sxs-lookup"><span data-stu-id="f5426-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f5426-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f5426-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="f5426-116">範例</span><span class="sxs-lookup"><span data-stu-id="f5426-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="f5426-117">執行 `dotnetsay` 本機工具。</span><span class="sxs-lookup"><span data-stu-id="f5426-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5426-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5426-118">See also</span></span>

- [<span data-ttu-id="f5426-119">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="f5426-119">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="f5426-120">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="f5426-120">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
