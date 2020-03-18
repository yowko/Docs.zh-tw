---
title: 點網工具運行命令
description: 點網工具運行命令調用本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847842"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="37dda-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="37dda-103">dotnet tool run</span></span>

<span data-ttu-id="37dda-104">**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="37dda-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37dda-105">名稱</span><span class="sxs-lookup"><span data-stu-id="37dda-105">Name</span></span>

<span data-ttu-id="37dda-106">`dotnet tool run`- 調用本地工具。</span><span class="sxs-lookup"><span data-stu-id="37dda-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37dda-107">概要</span><span class="sxs-lookup"><span data-stu-id="37dda-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="37dda-108">描述</span><span class="sxs-lookup"><span data-stu-id="37dda-108">Description</span></span>

<span data-ttu-id="37dda-109">該`dotnet tool run`命令搜索目前的目錄範圍內的工具清單檔。</span><span class="sxs-lookup"><span data-stu-id="37dda-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="37dda-110">當它找到對指定工具的引用時，它將運行該工具。</span><span class="sxs-lookup"><span data-stu-id="37dda-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="37dda-111">有關詳細資訊，請參閱[調用本地工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="37dda-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="37dda-112">引數</span><span class="sxs-lookup"><span data-stu-id="37dda-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="37dda-113">要運行的工具的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="37dda-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="37dda-114">選項。</span><span class="sxs-lookup"><span data-stu-id="37dda-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37dda-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="37dda-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="37dda-116">範例</span><span class="sxs-lookup"><span data-stu-id="37dda-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="37dda-117">運行`dotnetsay`本地工具。</span><span class="sxs-lookup"><span data-stu-id="37dda-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="37dda-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37dda-118">See also</span></span>

- [<span data-ttu-id="37dda-119">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="37dda-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="37dda-120">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="37dda-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
