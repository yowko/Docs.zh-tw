---
title: .NET 核心工具
description: 如何安裝、使用、更新和刪除 .NET 核心工具。 涵蓋全域工具、刀具路徑工具和本地工具。
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847779"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="6bf5d-104">如何管理 .NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="6bf5d-105">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="6bf5d-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="6bf5d-106">.NET Core 工具是包含主控台應用程式的特殊 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="6bf5d-107">可通過以下方式在機器上安裝工具：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="6bf5d-108">作為一個全域工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-108">As a global tool.</span></span>

  <span data-ttu-id="6bf5d-109">工具二進位檔案安裝在添加到 PATH 環境變數的預設目錄中。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="6bf5d-110">可以從電腦上的任何目錄調用該工具，而無需指定其位置。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="6bf5d-111">工具的一個版本用於電腦上的所有目錄。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="6bf5d-112">作為自訂位置的全域工具（也稱為工具路徑工具）。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="6bf5d-113">工具二進位檔案安裝在您指定的位置。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="6bf5d-114">可以從安裝目錄中調用該工具，也可以通過向目錄提供命令名稱或將目錄添加到 PATH 環境變數來調用該工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="6bf5d-115">工具的一個版本用於電腦上的所有目錄。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="6bf5d-116">作為本地工具（適用于 .NET 核心 SDK 3.0 及更高版本）。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="6bf5d-117">工具二進位檔案安裝在預設目錄中。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="6bf5d-118">從安裝目錄或其任何子目錄調用該工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="6bf5d-119">不同的目錄可以使用同一工具的不同版本。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="6bf5d-120">.NET CLI 使用清單檔來跟蹤哪些工具作為目錄的本地安裝。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="6bf5d-121">當清單檔保存在原始程式碼存儲庫的根目錄中時，參與者可以克隆存儲庫並調用單個 .NET Core CLI 命令，該命令安裝清單檔中列出的所有工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6bf5d-122">.NET 核心工具完全信任運行。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="6bf5d-123">除非信任作者，否則不要安裝 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="6bf5d-124">查找工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-124">Find a tool</span></span>

<span data-ttu-id="6bf5d-125">目前，.NET Core 沒有工具搜索功能。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="6bf5d-126">以下是查找工具的一些方法：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="6bf5d-127">請參閱[natemcmaster/點網工具](https://github.com/natemcmaster/dotnet-tools)GitHub 存儲庫中的工具清單。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-127">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="6bf5d-128">使用[工具獲取](https://www.toolget.net/)搜索 .NET 工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-128">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="6bf5d-129">在[dotnet/aspnetcore GitHub 存儲庫的工具目錄中](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)，請參閱 ASP.NET核心團隊創建的工具的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="6bf5d-130">瞭解[.NET 核心點網診斷工具](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)的診斷工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-130">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>
* <span data-ttu-id="6bf5d-131">搜索[NuGet](https://www.nuget.org)網站。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-131">Search the [NuGet](https://www.nuget.org) website.</span></span> <span data-ttu-id="6bf5d-132">但是，NuGet 網站還沒有一個功能，允許您只搜索工具組。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-132">However, the NuGet site doesn't yet have a feature that lets you search only for tool packages.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="6bf5d-133">檢查作者和統計資料</span><span class="sxs-lookup"><span data-stu-id="6bf5d-133">Check the author and statistics</span></span>

<span data-ttu-id="6bf5d-134">由於 .NET Core 工具完全信任運行，並且全域工具被添加到 PATH 環境變數中，因此它們可能非常強大。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="6bf5d-135">請不要下載來自不信任人員的工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="6bf5d-136">如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="6bf5d-137">安裝全域工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-137">Install a global tool</span></span>

<span data-ttu-id="6bf5d-138">要將工具安裝為全域工具，請使用`-g`[dotnet 工具安裝](dotnet-tool-install.md)的 或`--global`選項，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="6bf5d-139">輸出顯示用於調用工具和安裝的版本的命令，類似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="6bf5d-140">工具二進位檔案的預設位置取決於作業系統：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="6bf5d-141">OS</span><span class="sxs-lookup"><span data-stu-id="6bf5d-141">OS</span></span>          | <span data-ttu-id="6bf5d-142">Path</span><span class="sxs-lookup"><span data-stu-id="6bf5d-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="6bf5d-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="6bf5d-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="6bf5d-144">Windows</span><span class="sxs-lookup"><span data-stu-id="6bf5d-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="6bf5d-145">首次運行 SDK 時，此位置將添加到使用者的路徑中，因此可以從任何目錄調用全域工具，而無需指定工具位置。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="6bf5d-146">工具訪問是特定于使用者的，而不是電腦全域。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="6bf5d-147">全域工具僅對安裝該工具的使用者可用。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="6bf5d-148">在自訂位置安裝全域工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="6bf5d-149">要將工具作為全域工具安裝在自訂位置，請使用`--tool-path`[dotnet 工具安裝](dotnet-tool-install.md)選項，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="6bf5d-150">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="6bf5d-151">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="6bf5d-152">.NET 核心 SDK 不會自動將此位置添加到 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="6bf5d-153">要[調用工具路徑工具](#invoke-a-tool-path-tool)，您必須使用以下方法之一確保該命令可用：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="6bf5d-154">將安裝目錄添加到 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="6bf5d-155">調用工具時指定工具的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="6bf5d-156">從安裝目錄中調用該工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="6bf5d-157">安裝本地工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-157">Install a local tool</span></span>

<span data-ttu-id="6bf5d-158">**適用于 .NET 核心 3.0 SDK 及更高版本。**</span><span class="sxs-lookup"><span data-stu-id="6bf5d-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="6bf5d-159">要僅安裝用於本地訪問的工具（對於目前的目錄和子目錄），必須將其添加到工具清單檔中。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="6bf5d-160">要創建工具清單檔，請運行以下`dotnet new tool-manifest`命令：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="6bf5d-161">此命令在 *.config*目錄下創建名為*dotnet-tools.json*的清單檔。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="6bf5d-162">要向清單檔添加本地工具，請使用[dotnet 工具安裝](dotnet-tool-install.md)命令並**省略**和`--global``--tool-path`選項，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="6bf5d-163">命令輸出顯示新安裝的工具位於哪個清單檔，類似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="6bf5d-164">下面的示例顯示了一個已安裝兩個本地工具的清單檔：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-164">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="6bf5d-165">通常將本地工具添加到存儲庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="6bf5d-166">將清單檔簽入存儲庫後，從存儲庫簽出代碼的開發人員將獲得最新的清單檔。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="6bf5d-167">要安裝清單檔中列出的所有工具，它們運行以下`dotnet tool restore`命令：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="6bf5d-168">輸出指示已還原的工具：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="6bf5d-169">安裝特定的工具版本</span><span class="sxs-lookup"><span data-stu-id="6bf5d-169">Install a specific tool version</span></span>

<span data-ttu-id="6bf5d-170">要安裝預發佈版本或工具的特定版本，請使用`--version`選項指定版本號，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="6bf5d-171">使用工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-171">Use a tool</span></span>

<span data-ttu-id="6bf5d-172">用於調用工具的命令可能與安裝的包的名稱不同。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="6bf5d-173">要顯示當前使用者電腦上當前安裝的所有工具，請使用[dotnet 工具清單](dotnet-tool-list.md)命令：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="6bf5d-174">輸出顯示每個工具的版本和命令，類似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="6bf5d-175">如本示例所示，清單顯示本地工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="6bf5d-176">要查看全域工具，請使用 選項`--global`，要查看工具路徑工具，請使用 選項`--tool-path`。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="6bf5d-177">調用全域工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-177">Invoke a global tool</span></span>

<span data-ttu-id="6bf5d-178">對於全域工具，請使用工具命令本身。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="6bf5d-179">例如，如果命令是`dotnetsay`或`dotnet-doc`，則用於調用 命令：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="6bf5d-180">如果命令以首碼`dotnet-`開頭，則調用該工具的另一種方法是使用 命令`dotnet`並省略工具命令首碼。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="6bf5d-181">例如，如果命令為`dotnet-doc`，以下命令將調用該工具：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="6bf5d-182">但是，在以下方案中，不能使用 命令`dotnet`調用全域工具：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="6bf5d-183">全域工具和本地工具具有相同的命令，該命令由 預`dotnet-`定。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="6bf5d-184">您希望從本地工具範圍內的目錄中調用全域工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="6bf5d-185">在這種情況下，`dotnet doc`並`dotnet dotnet-doc`調用本地工具。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="6bf5d-186">要調用全域工具，請自行使用 命令：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="6bf5d-187">調用工具路徑工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="6bf5d-188">要調用使用`tool-path`option 安裝的全域工具，請確保該命令可用，如[本文前面](#install-a-global-tool-in-a-custom-location)所述。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="6bf5d-189">調用本地工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-189">Invoke a local tool</span></span>

<span data-ttu-id="6bf5d-190">要調用本地工具，必須從安裝目錄中使用`dotnet`該命令。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="6bf5d-191">您可以使用長表單 （`dotnet tool run <COMMAND_NAME>`） 或短表單 （`dotnet <COMMAND_NAME>`），如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="6bf5d-192">如果命令被預綴于`dotnet-`，則可以在調用該工具時包括或省略首碼。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="6bf5d-193">例如，如果命令為`dotnet-doc`，以下任何示例都調用本地工具：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="6bf5d-194">更新工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-194">Update a tool</span></span>

<span data-ttu-id="6bf5d-195">更新工具涉及卸載和重新安裝它與最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="6bf5d-196">要更新工具，請使用[dotnet 工具更新](dotnet-tool-update.md)命令，該選項與安裝該工具的選項相同：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="6bf5d-197">對於本地工具，SDK 通過查找目前的目錄和父目錄查找包含包 ID 的第一個清單檔。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="6bf5d-198">如果任何清單檔中沒有此類包 ID，SDK 會向最近的清單檔添加新條目。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="6bf5d-199">卸載工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-199">Uninstall a tool</span></span>

<span data-ttu-id="6bf5d-200">使用[dotnet 工具卸載](dotnet-tool-uninstall.md)命令，使用與安裝該工具相同的選項移除工具：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="6bf5d-201">對於本地工具，SDK 通過查找目前的目錄和父目錄查找包含包 ID 的第一個清單檔。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="6bf5d-202">獲取説明和故障排除</span><span class="sxs-lookup"><span data-stu-id="6bf5d-202">Get help and troubleshoot</span></span>

<span data-ttu-id="6bf5d-203">要獲取可用`dotnet tool`命令的清單，請輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="6bf5d-204">要獲取工具使用說明，請輸入以下命令之一或查看該工具的網站：</span><span class="sxs-lookup"><span data-stu-id="6bf5d-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="6bf5d-205">如果工具無法安裝或運行，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf5d-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6bf5d-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bf5d-206">See also</span></span>

- [<span data-ttu-id="6bf5d-207">教程：使用 .NET 核心 CLI 創建 .NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-207">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="6bf5d-208">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-208">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="6bf5d-209">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="6bf5d-209">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
