---
title: .NET 工具
description: 如何安裝、使用、更新和移除 .NET 工具。 涵蓋通用工具、工具路徑工具和區域工具。
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: 3669ed17d58542aab0435ccea22700c82ba8ea26
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556897"
---
# <a name="how-to-manage-net-tools"></a><span data-ttu-id="31e7e-104">如何管理 .NET 工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-104">How to manage .NET tools</span></span>

<span data-ttu-id="31e7e-105">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="31e7e-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="31e7e-106">.NET 工具是包含主控台應用程式的特殊 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="31e7e-106">A .NET tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="31e7e-107">您可以透過下列方式在電腦上安裝工具：</span><span class="sxs-lookup"><span data-stu-id="31e7e-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="31e7e-108">作為全域工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-108">As a global tool.</span></span>

  <span data-ttu-id="31e7e-109">工具二進位檔會安裝在已新增至 PATH 環境變數的預設目錄中。</span><span class="sxs-lookup"><span data-stu-id="31e7e-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="31e7e-110">您可以從電腦上的任何目錄中叫用此工具，而不需指定其位置。</span><span class="sxs-lookup"><span data-stu-id="31e7e-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="31e7e-111">電腦上的所有目錄都會使用一個版本的工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="31e7e-112">做為自訂位置中的全域工具 (也稱為工具路徑工具) 。</span><span class="sxs-lookup"><span data-stu-id="31e7e-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="31e7e-113">工具二進位檔會安裝在您指定的位置。</span><span class="sxs-lookup"><span data-stu-id="31e7e-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="31e7e-114">您可以從安裝目錄中叫用此工具，或提供具有命令名稱的目錄，或將目錄新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="31e7e-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="31e7e-115">電腦上的所有目錄都會使用一個版本的工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="31e7e-116">作為本機工具 (適用于 .NET Core SDK 3.0 和更新版本) 。</span><span class="sxs-lookup"><span data-stu-id="31e7e-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="31e7e-117">工具二進位檔會安裝在預設目錄中。</span><span class="sxs-lookup"><span data-stu-id="31e7e-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="31e7e-118">您可以從安裝目錄或其任何子目錄中叫用此工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="31e7e-119">不同的目錄可以使用相同工具的不同版本。</span><span class="sxs-lookup"><span data-stu-id="31e7e-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="31e7e-120">.NET CLI 會使用資訊清單檔案來追蹤哪些工具會以本機方式安裝到目錄。</span><span class="sxs-lookup"><span data-stu-id="31e7e-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="31e7e-121">在原始程式碼存放庫的根目錄中儲存資訊清單檔案時，參與者可以複製存放庫，並叫用單一 .NET CLI 命令，以安裝資訊清單檔案中列出的所有工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31e7e-122">.NET 工具會以完全信任的方式執行。</span><span class="sxs-lookup"><span data-stu-id="31e7e-122">.NET tools run in full trust.</span></span> <span data-ttu-id="31e7e-123">除非您信任作者，否則請勿安裝 .NET 工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-123">Do not install a .NET tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="31e7e-124">尋找工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-124">Find a tool</span></span>

<span data-ttu-id="31e7e-125">以下是一些尋找工具的方法：</span><span class="sxs-lookup"><span data-stu-id="31e7e-125">Here are some ways to find tools:</span></span>

* <span data-ttu-id="31e7e-126">使用 [dotnet 工具搜尋](dotnet-tool-search.md) 命令來尋找已發佈至 NuGet.org 的工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-126">Use the [dotnet tool search](dotnet-tool-search.md) command to find a tool that is published to NuGet.org.</span></span>
* <span data-ttu-id="31e7e-127">使用 ".NET tool" 套件類型篩選準則來搜尋 [NuGet](https://www.nuget.org) 網站。</span><span class="sxs-lookup"><span data-stu-id="31e7e-127">Search the [NuGet](https://www.nuget.org) website by using the ".NET tool" package type filter.</span></span> <span data-ttu-id="31e7e-128">如需詳細資訊，請參閱[尋找及選擇套件](/nuget/consume-packages/finding-and-choosing-packages)。</span><span class="sxs-lookup"><span data-stu-id="31e7e-128">For more information, see [Finding and choosing packages](/nuget/consume-packages/finding-and-choosing-packages).</span></span>
* <span data-ttu-id="31e7e-129">請參閱 [natemcmaster/dotnet 工具](https://github.com/natemcmaster/dotnet-tools) GitHub 存放庫中的工具清單。</span><span class="sxs-lookup"><span data-stu-id="31e7e-129">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="31e7e-130">使用 [ToolGet](https://www.toolget.net/) 搜尋 .net 工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-130">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="31e7e-131">請參閱 [dotnet/Aspnetcore GitHub 存放庫的 tools 目錄](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)中，由 ASP.NET Core 團隊所建立之工具的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="31e7e-131">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="31e7e-132">瞭解 [.net 診斷工具](../diagnostics/index.md#net-core-diagnostic-global-tools)上的診斷工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-132">Learn about diagnostic tools at [.NET diagnostic tools](../diagnostics/index.md#net-core-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="31e7e-133">檢查作者和統計資料</span><span class="sxs-lookup"><span data-stu-id="31e7e-133">Check the author and statistics</span></span>

<span data-ttu-id="31e7e-134">由於 .NET 工具是以完全信任的方式執行，而全域工具會新增至 PATH 環境變數中，因此可能非常強大。</span><span class="sxs-lookup"><span data-stu-id="31e7e-134">Since .NET tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="31e7e-135">請不要下載來自不信任人員的工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="31e7e-136">如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。</span><span class="sxs-lookup"><span data-stu-id="31e7e-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="31e7e-137">安裝通用工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-137">Install a global tool</span></span>

<span data-ttu-id="31e7e-138">若要將工具安裝為通用工具，請使用 `-g` `--global` [dotnet 工具安裝](dotnet-tool-install.md)的或選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31e7e-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="31e7e-139">輸出會顯示用來叫用工具和安裝版本的命令，類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="31e7e-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="31e7e-140">工具二進位檔的預設位置取決於作業系統：</span><span class="sxs-lookup"><span data-stu-id="31e7e-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="31e7e-141">OS</span><span class="sxs-lookup"><span data-stu-id="31e7e-141">OS</span></span>          | <span data-ttu-id="31e7e-142">路徑</span><span class="sxs-lookup"><span data-stu-id="31e7e-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="31e7e-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="31e7e-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="31e7e-144">Windows</span><span class="sxs-lookup"><span data-stu-id="31e7e-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="31e7e-145">第一次執行 SDK 時，此位置會新增至使用者的路徑，因此可以從任何目錄叫用通用工具，而不需指定工具位置。</span><span class="sxs-lookup"><span data-stu-id="31e7e-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="31e7e-146">工具存取是使用者特定的，而不是電腦全域。</span><span class="sxs-lookup"><span data-stu-id="31e7e-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="31e7e-147">通用工具僅供已安裝此工具的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="31e7e-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="31e7e-148">在自訂位置安裝通用工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="31e7e-149">若要在自訂位置將工具安裝為通用工具，請使用 `--tool-path` [dotnet 工具安裝](dotnet-tool-install.md)的選項，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="31e7e-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="31e7e-150">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="31e7e-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="31e7e-151">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="31e7e-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="31e7e-152">.NET SDK 不會自動將此位置新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="31e7e-152">The .NET SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="31e7e-153">若要叫用 [工具路徑工具](#invoke-a-tool-path-tool)，您必須使用下列其中一種方法來確定命令可供使用：</span><span class="sxs-lookup"><span data-stu-id="31e7e-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="31e7e-154">將安裝目錄新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="31e7e-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="31e7e-155">當您叫用工具時，指定該工具的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="31e7e-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="31e7e-156">從安裝目錄中叫用工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="31e7e-157">安裝本機工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-157">Install a local tool</span></span>

<span data-ttu-id="31e7e-158">**適用于 .NET Core 3.0 SDK 和更新版本。**</span><span class="sxs-lookup"><span data-stu-id="31e7e-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="31e7e-159">若要安裝僅限本機存取的工具 (針對目前的目錄和子目錄) ，必須將其新增至工具資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="31e7e-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="31e7e-160">若要建立工具資訊清單檔，請執行 `dotnet new tool-manifest` 下列命令：</span><span class="sxs-lookup"><span data-stu-id="31e7e-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="31e7e-161">此命令會在 *.config* 目錄下建立名為 *dotnet-tools.js* 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="31e7e-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="31e7e-162">若要將本機工具新增至資訊清單檔，請使用 [dotnet tool install](dotnet-tool-install.md) 命令，並 **省略** `--global` 和 `--tool-path` 選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31e7e-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="31e7e-163">命令輸出會顯示新安裝的工具所在的資訊清單檔案，類似下列範例：</span><span class="sxs-lookup"><span data-stu-id="31e7e-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="31e7e-164">下列範例顯示已安裝兩個本機工具的資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="31e7e-164">The following example shows a manifest file with two local tools installed:</span></span>

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

<span data-ttu-id="31e7e-165">您通常會將本機工具新增至存放庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="31e7e-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="31e7e-166">將資訊清單檔案簽入存放庫之後，從儲存機制簽出程式碼的開發人員會取得最新的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="31e7e-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="31e7e-167">若要安裝資訊清單檔案中列出的所有工具，請執行 `dotnet tool restore` 下列命令：</span><span class="sxs-lookup"><span data-stu-id="31e7e-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="31e7e-168">輸出會指出已還原的工具：</span><span class="sxs-lookup"><span data-stu-id="31e7e-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="31e7e-169">安裝特定的工具版本</span><span class="sxs-lookup"><span data-stu-id="31e7e-169">Install a specific tool version</span></span>

<span data-ttu-id="31e7e-170">若要安裝發行前版本或特定版本的工具，請使用選項來指定版本號碼 `--version` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31e7e-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="31e7e-171">使用工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-171">Use a tool</span></span>

<span data-ttu-id="31e7e-172">您用來叫用工具的命令可能與您安裝的封裝名稱不同。</span><span class="sxs-lookup"><span data-stu-id="31e7e-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="31e7e-173">若要顯示目前使用者目前安裝在電腦上的所有工具，請使用 [dotnet 工具清單](dotnet-tool-list.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="31e7e-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="31e7e-174">輸出會顯示每個工具的版本和命令，類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="31e7e-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="31e7e-175">如這個範例所示，此清單會顯示本機工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="31e7e-176">若要查看通用工具，請使用 `--global` 選項，若要查看工具路徑工具，請使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="31e7e-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="31e7e-177">叫用通用工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-177">Invoke a global tool</span></span>

<span data-ttu-id="31e7e-178">若為通用工具，請單獨使用工具命令。</span><span class="sxs-lookup"><span data-stu-id="31e7e-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="31e7e-179">例如，如果命令是 `dotnetsay` 或，就會 `dotnet-doc` 用來叫用命令：</span><span class="sxs-lookup"><span data-stu-id="31e7e-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="31e7e-180">如果命令的開頭是前置詞 `dotnet-` ，則叫用工具的替代方式是使用 `dotnet` 命令並省略工具命令前置詞。</span><span class="sxs-lookup"><span data-stu-id="31e7e-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="31e7e-181">例如，如果命令為 `dotnet-doc` ，則下列命令會叫用工具：</span><span class="sxs-lookup"><span data-stu-id="31e7e-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="31e7e-182">不過，在下列案例中，您無法使用 `dotnet` 命令叫用通用工具：</span><span class="sxs-lookup"><span data-stu-id="31e7e-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="31e7e-183">全域工具和本機工具的前面都有相同的命令 `dotnet-` 。</span><span class="sxs-lookup"><span data-stu-id="31e7e-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="31e7e-184">您想要從本機工具範圍中的目錄叫用全域工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="31e7e-185">在此案例中，會叫用 `dotnet doc` `dotnet dotnet-doc` 本機工具。</span><span class="sxs-lookup"><span data-stu-id="31e7e-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="31e7e-186">若要叫用全域工具，請單獨使用命令：</span><span class="sxs-lookup"><span data-stu-id="31e7e-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="31e7e-187">叫用工具路徑工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="31e7e-188">若要叫用使用選項所安裝的通用工具 `tool-path` ，請確定命令可供使用，如本文稍 [早](#install-a-global-tool-in-a-custom-location)所述。</span><span class="sxs-lookup"><span data-stu-id="31e7e-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="31e7e-189">叫用本機工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-189">Invoke a local tool</span></span>

<span data-ttu-id="31e7e-190">若要叫用本機工具，您必須 `dotnet` 從安裝目錄中使用命令。</span><span class="sxs-lookup"><span data-stu-id="31e7e-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="31e7e-191">您可以使用 [完整格式] (`dotnet tool run <COMMAND_NAME>`) 或 () 的簡短格式 `dotnet <COMMAND_NAME>` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31e7e-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="31e7e-192">如果命令的前置詞為 `dotnet-` ，當您叫用工具時，可以包含或省略前置詞。</span><span class="sxs-lookup"><span data-stu-id="31e7e-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="31e7e-193">例如，如果命令為 `dotnet-doc` ，下列任何範例都會叫用本機工具：</span><span class="sxs-lookup"><span data-stu-id="31e7e-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="31e7e-194">更新工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-194">Update a tool</span></span>

<span data-ttu-id="31e7e-195">更新工具需要以最新的穩定版本卸載並重新安裝。</span><span class="sxs-lookup"><span data-stu-id="31e7e-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="31e7e-196">若要更新工具，請使用 [dotnet tool update](dotnet-tool-update.md) 命令與您用來安裝此工具的相同選項：</span><span class="sxs-lookup"><span data-stu-id="31e7e-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="31e7e-197">針對本機工具，SDK 會藉由查看目前目錄和上層目錄，尋找包含封裝識別碼的第一個資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="31e7e-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="31e7e-198">如果任何資訊清單檔中沒有這類套件識別碼，SDK 會將新專案新增至最接近的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="31e7e-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="31e7e-199">卸載工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-199">Uninstall a tool</span></span>

<span data-ttu-id="31e7e-200">使用您用來安裝此工具的相同選項，以 [dotnet 工具 uninstall](dotnet-tool-uninstall.md) 命令移除工具：</span><span class="sxs-lookup"><span data-stu-id="31e7e-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="31e7e-201">針對本機工具，SDK 會藉由查看目前目錄和上層目錄，尋找包含封裝識別碼的第一個資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="31e7e-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="31e7e-202">取得協助及進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="31e7e-202">Get help and troubleshoot</span></span>

<span data-ttu-id="31e7e-203">若要取得可用命令的清單 `dotnet tool` ，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="31e7e-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="31e7e-204">若要取得工具使用方式的指示，請輸入下列其中一個命令，或查看工具的網站：</span><span class="sxs-lookup"><span data-stu-id="31e7e-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="31e7e-205">如果工具無法安裝或執行，請參閱針對 [.net 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="31e7e-205">If a tool fails to install or run, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31e7e-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31e7e-206">See also</span></span>

- [<span data-ttu-id="31e7e-207">教學課程：使用 .NET CLI 建立 .NET 工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-207">Tutorial: Create a .NET tool using the .NET CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="31e7e-208">教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-208">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="31e7e-209">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="31e7e-209">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
