---
title: 點網工具執行命令
description: 點網工具運行命令調用本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463318"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="81c78-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="81c78-103">dotnet tool run</span></span>

<span data-ttu-id="81c78-104">**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="81c78-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="81c78-105">名稱</span><span class="sxs-lookup"><span data-stu-id="81c78-105">Name</span></span>

<span data-ttu-id="81c78-106">`dotnet tool run`- 調用本地工具。</span><span class="sxs-lookup"><span data-stu-id="81c78-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81c78-107">概要</span><span class="sxs-lookup"><span data-stu-id="81c78-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="81c78-108">描述</span><span class="sxs-lookup"><span data-stu-id="81c78-108">Description</span></span>

<span data-ttu-id="81c78-109">該`dotnet tool run`命令搜索當前目錄範圍內的工具清單檔。</span><span class="sxs-lookup"><span data-stu-id="81c78-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="81c78-110">當它找到對指定工具的引用時,它將運行該工具。</span><span class="sxs-lookup"><span data-stu-id="81c78-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="81c78-111">有關詳細資訊,請參閱[除錯工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="81c78-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="81c78-112">引數</span><span class="sxs-lookup"><span data-stu-id="81c78-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="81c78-113">要運行的工具的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="81c78-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="81c78-114">選項。</span><span class="sxs-lookup"><span data-stu-id="81c78-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="81c78-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="81c78-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="81c78-116">範例</span><span class="sxs-lookup"><span data-stu-id="81c78-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="81c78-117">運行`dotnetsay`本地工具。</span><span class="sxs-lookup"><span data-stu-id="81c78-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="81c78-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81c78-118">See also</span></span>

- [<span data-ttu-id="81c78-119">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="81c78-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="81c78-120">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="81c78-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
