---
title: 卸載工具
description: 介紹 .NET Core 卸載工具，這是可讓您以 .NET Core Sdk 和執行時間進行受控制清除的引導式工具。
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: ed43b4ec8437ae0ccaf5f1234758dda9f16bd51e
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235348"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="b1202-103">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="b1202-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="b1202-104">[.Net Core 卸載工具](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) 可讓您從系統移除 .net Core sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="b1202-105">選項的集合可以用來指定您要卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="b1202-106">此工具支援 Windows 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="b1202-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="b1202-107">目前不支援 Linux。</span><span class="sxs-lookup"><span data-stu-id="b1202-107">Linux is currently not supported.</span></span>

<span data-ttu-id="b1202-108">在 Windows 中，此工具只能卸載使用下列其中一個安裝程式所安裝的 Sdk 和執行時間：</span><span class="sxs-lookup"><span data-stu-id="b1202-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="b1202-109">.NET Core SDK 與執行時間安裝程式。</span><span class="sxs-lookup"><span data-stu-id="b1202-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="b1202-110">Visual Studio 2019 16.3 版之前的版本 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="b1202-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="b1202-111">在 macOS 上，工具只能卸載位於 */usr/local/share/dotnet* 資料夾中的 sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="b1202-112">由於有這些限制，因此工具可能無法卸載電腦上的所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="b1202-113">您可以使用 `dotnet --info` 命令來尋找已安裝的所有 .Net Core sdk 和執行時間，包括這項工具無法移除的 sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="b1202-114">此 `dotnet-core-uninstall list` 命令會顯示哪些 sdk 可以使用工具來卸載。</span><span class="sxs-lookup"><span data-stu-id="b1202-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span> <span data-ttu-id="b1202-115">1.2 和更新版本可以卸載5.0 版或更早版本的 Sdk 和執行時間，而舊版工具可以卸載3.1 和更早版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-115">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="b1202-116">安裝工具</span><span class="sxs-lookup"><span data-stu-id="b1202-116">Install the tool</span></span>

<span data-ttu-id="b1202-117">您可以從 [工具的 [版本] 頁面](https://aka.ms/dotnet-core-uninstall-tool) 下載 .Net Core 卸載工具，並在 [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub 存放庫中尋找原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1202-117">You can download the .NET Core Uninstall Tool from [the tool's releases page](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="b1202-118">此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-118">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="b1202-119">因此，它應該安裝在受寫入保護的目錄中，例如 Windows 上的 *C:\Program* 檔案或 macOS 上的 */usr/local/bin* 。</span><span class="sxs-lookup"><span data-stu-id="b1202-119">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="b1202-120">另請參閱更 [高的 dotnet 命令存取權](../tools/elevated-access.md)。</span><span class="sxs-lookup"><span data-stu-id="b1202-120">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="b1202-121">如需詳細資訊，請參閱 [詳細的安裝指示](https://aka.ms/dotnet-core-uninstall-tool)。</span><span class="sxs-lookup"><span data-stu-id="b1202-121">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="b1202-122">執行工具</span><span class="sxs-lookup"><span data-stu-id="b1202-122">Run the tool</span></span>

<span data-ttu-id="b1202-123">下列步驟顯示執行卸載工具的建議方法：</span><span class="sxs-lookup"><span data-stu-id="b1202-123">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="b1202-124">步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="b1202-124">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="b1202-125">步驟 2-執行試執行</span><span class="sxs-lookup"><span data-stu-id="b1202-125">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="b1202-126">步驟 3-卸載 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="b1202-126">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="b1202-127">步驟 4-刪除 NuGet fallback 資料夾 (選用) </span><span class="sxs-lookup"><span data-stu-id="b1202-127">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="b1202-128">步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="b1202-128">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="b1202-129">此 `dotnet-core-uninstall list` 命令會列出已安裝的 .Net Core sdk 和執行時間，可使用此工具移除。</span><span class="sxs-lookup"><span data-stu-id="b1202-129">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="b1202-130">Visual Studio 可能需要某些 Sdk 和執行時間，而且會顯示這些 Sdk 和執行時間，並說明為何不建議將其卸載。</span><span class="sxs-lookup"><span data-stu-id="b1202-130">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="b1202-131">`dotnet-core-uninstall list`在大部分情況下，命令的輸出不會符合的輸出中已安裝版本的清單 `dotnet --info` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-131">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="b1202-132">具體而言，此工具不會顯示 zip 檔案所安裝或受 Visual Studio 管理的版本 (Visual Studio 2019 16.3 或更新版本) 安裝的任何版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-132">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="b1202-133">檢查版本是否受 Visual Studio 管理的其中一種方式是在中加以查看 `Add or Remove Programs` ，其中 Visual Studio 的 managed 版本會標示為其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b1202-133">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="b1202-134">**dotnet-核心-卸載清單**</span><span class="sxs-lookup"><span data-stu-id="b1202-134">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b1202-135">概要</span><span class="sxs-lookup"><span data-stu-id="b1202-135">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="b1202-136">選項</span><span class="sxs-lookup"><span data-stu-id="b1202-136">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b1202-137">Windows</span><span class="sxs-lookup"><span data-stu-id="b1202-137">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="b1202-138">列出所有可以使用此工具卸載的 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-138">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b1202-139">列出可以使用此工具卸載的所有 .NET Core 裝載套件組合。</span><span class="sxs-lookup"><span data-stu-id="b1202-139">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="b1202-140">列出可以使用此工具卸載的所有 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-140">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="b1202-141">列出可以使用此工具卸載的所有 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-141">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b1202-142">設定詳細程度層級。</span><span class="sxs-lookup"><span data-stu-id="b1202-142">Sets the verbosity level.</span></span> <span data-ttu-id="b1202-143">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b1202-143">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1202-144">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="b1202-144">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b1202-145">列出可以使用此工具卸載的所有 x64 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-145">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="b1202-146">列出可以使用此工具卸載的所有 x86 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-146">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b1202-147">macOS</span><span class="sxs-lookup"><span data-stu-id="b1202-147">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="b1202-148">列出可以使用此工具卸載的所有 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-148">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="b1202-149">列出可以使用此工具卸載的所有 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-149">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b1202-150">設定詳細程度層級。</span><span class="sxs-lookup"><span data-stu-id="b1202-150">Sets the verbosity level.</span></span> <span data-ttu-id="b1202-151">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b1202-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1202-152">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="b1202-152">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="b1202-153">範例</span><span class="sxs-lookup"><span data-stu-id="b1202-153">Examples</span></span>

* <span data-ttu-id="b1202-154">列出可以使用此工具移除的所有 .NET Core Sdk 和執行時間：</span><span class="sxs-lookup"><span data-stu-id="b1202-154">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="b1202-155">列出所有 x64 .NET Core Sdk 和執行時間：</span><span class="sxs-lookup"><span data-stu-id="b1202-155">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="b1202-156">列出所有 x86 .NET Core Sdk：</span><span class="sxs-lookup"><span data-stu-id="b1202-156">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="b1202-157">步驟 2-執行試執行</span><span class="sxs-lookup"><span data-stu-id="b1202-157">Step 2 - Do a dry run</span></span>

<span data-ttu-id="b1202-158">`dotnet-core-uninstall dry-run`和 `dotnet-core-uninstall whatif` 命令會顯示 .Net Core sdk 和執行時間，這些 sdk 和執行時間會根據提供的選項而移除，而不需執行卸載。</span><span class="sxs-lookup"><span data-stu-id="b1202-158">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="b1202-159">這些命令是同義字。</span><span class="sxs-lookup"><span data-stu-id="b1202-159">These commands are synonyms.</span></span>

<span data-ttu-id="b1202-160">**dotnet-核心-卸載試執行和 dotnet 核心-卸載 whatif**</span><span class="sxs-lookup"><span data-stu-id="b1202-160">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b1202-161">概要</span><span class="sxs-lookup"><span data-stu-id="b1202-161">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="b1202-162">引數</span><span class="sxs-lookup"><span data-stu-id="b1202-162">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="b1202-163">要卸載的指定版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-163">The specified version to uninstall.</span></span> <span data-ttu-id="b1202-164">您可以列出多個版本，並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="b1202-164">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="b1202-165">也支援回應檔。</span><span class="sxs-lookup"><span data-stu-id="b1202-165">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="b1202-166">回應檔是在命令列上放置所有版本的替代方法。</span><span class="sxs-lookup"><span data-stu-id="b1202-166">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="b1202-167">它們是文字檔，通常 \* 會使用 .rsp 副檔名，而且每個版本都會列在個別的行上。</span><span class="sxs-lookup"><span data-stu-id="b1202-167">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="b1202-168">若要指定引數的回應檔 `VERSION` ，請使用 \@ 緊接在回應檔名稱後面的字元。</span><span class="sxs-lookup"><span data-stu-id="b1202-168">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="b1202-169">選項</span><span class="sxs-lookup"><span data-stu-id="b1202-169">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b1202-170">Windows</span><span class="sxs-lookup"><span data-stu-id="b1202-170">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="b1202-171">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-171">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="b1202-172">只會移除版本小於指定版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-172">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="b1202-173">指定的版本仍會保持安裝。</span><span class="sxs-lookup"><span data-stu-id="b1202-173">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="b1202-174">除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-174">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b1202-175">移除最高版本以外的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-175">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b1202-176">移除較高修補程式所取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-176">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b1202-177">此選項可保護上的 global.js。</span><span class="sxs-lookup"><span data-stu-id="b1202-177">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b1202-178">移除標記為預覽版的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-178">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b1202-179">移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。</span><span class="sxs-lookup"><span data-stu-id="b1202-179">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="b1202-180">只移除 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-180">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b1202-181">只會移除 .NET Core 執行時間和裝載套件組合。</span><span class="sxs-lookup"><span data-stu-id="b1202-181">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b1202-182">移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-182">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b1202-183">僅移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-183">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b1202-184">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-184">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b1202-185">設定詳細程度層級。</span><span class="sxs-lookup"><span data-stu-id="b1202-185">Sets the verbosity level.</span></span> <span data-ttu-id="b1202-186">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b1202-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1202-187">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="b1202-187">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b1202-188">必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x64 sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="b1202-189">必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x86 sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-189">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="b1202-190">**`--force`** 強制移除 Visual Studio 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-190">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="b1202-191">注意：</span><span class="sxs-lookup"><span data-stu-id="b1202-191">Notes:</span></span>

1. <span data-ttu-id="b1202-192">只需要、、和的其中一個 `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-192">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="b1202-193">`--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。</span><span class="sxs-lookup"><span data-stu-id="b1202-193">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="b1202-194">如果 `--x64` `--x86` 指定或未指定，則會移除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="b1202-194">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b1202-195">macOS</span><span class="sxs-lookup"><span data-stu-id="b1202-195">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="b1202-196">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-196">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="b1202-197">移除低於指定版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-197">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="b1202-198">指定的版本將會保留。</span><span class="sxs-lookup"><span data-stu-id="b1202-198">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="b1202-199">移除 .NET Core Sdk 和執行時間，但指定的版本除外。</span><span class="sxs-lookup"><span data-stu-id="b1202-199">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b1202-200">移除最高版本以外的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-200">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b1202-201">移除較高修補程式所取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-201">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b1202-202">此選項可保護上的 global.js。</span><span class="sxs-lookup"><span data-stu-id="b1202-202">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b1202-203">移除標記為預覽版的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-203">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b1202-204">移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。</span><span class="sxs-lookup"><span data-stu-id="b1202-204">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b1202-205">移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-205">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b1202-206">僅移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-206">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b1202-207">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-207">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b1202-208">設定詳細程度層級。</span><span class="sxs-lookup"><span data-stu-id="b1202-208">Sets the verbosity level.</span></span> <span data-ttu-id="b1202-209">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b1202-209">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1202-210">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="b1202-210">The default value is `normal`.</span></span>
  
* <span data-ttu-id="b1202-211">**`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-211">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="b1202-212">注意：</span><span class="sxs-lookup"><span data-stu-id="b1202-212">Notes:</span></span>

1. <span data-ttu-id="b1202-213">只有其中一個 `--sdk` `--runtime` 是必要的。</span><span class="sxs-lookup"><span data-stu-id="b1202-213">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="b1202-214">`--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。</span><span class="sxs-lookup"><span data-stu-id="b1202-214">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="b1202-215">範例</span><span class="sxs-lookup"><span data-stu-id="b1202-215">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="b1202-216">根據預設，Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間不會包含在 `dotnet-core-uninstall dry-run` 輸出中。</span><span class="sxs-lookup"><span data-stu-id="b1202-216">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="b1202-217">在下列範例中，某些指定的 Sdk 和執行時間可能不會包含在輸出中，視機器的狀態而定。</span><span class="sxs-lookup"><span data-stu-id="b1202-217">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="b1202-218">若要包含所有 Sdk 和執行時間，請將它們明確地列為引數，或使用 `--force` 選項。</span><span class="sxs-lookup"><span data-stu-id="b1202-218">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="b1202-219">移除已被較高修補程式取代的所有 .NET Core 執行時間的試執行：</span><span class="sxs-lookup"><span data-stu-id="b1202-219">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="b1202-220">正在將所有 .NET Core Sdk 的版本移除，以進行移除 `2.2.301` ：</span><span class="sxs-lookup"><span data-stu-id="b1202-220">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="b1202-221">步驟 3-卸載 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="b1202-221">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="b1202-222">`dotnet-core-uninstall remove` 卸載選項組合指定的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-222">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="b1202-223">1.2 和更新版本可以卸載5.0 版或更早版本的 Sdk 和執行時間，而舊版工具可以卸載3.1 和更早版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-223">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

<span data-ttu-id="b1202-224">因為此工具具有破壞性行為， **強烈** 建議您在執行 [移除] 命令之前執行試執行。</span><span class="sxs-lookup"><span data-stu-id="b1202-224">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="b1202-225">試執行會顯示當您使用命令時，將會移除哪些 .NET Core Sdk 和執行時間 `remove` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-225">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="b1202-226">請參閱 [我是否應該移除版本？](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) 以瞭解可安全移除哪些 sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-226">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="b1202-227">請記住下列注意事項：</span><span class="sxs-lookup"><span data-stu-id="b1202-227">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="b1202-228">這項工具可以卸載電腦上的檔案所需的 .NET Core SDK 版本 `global.json` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-228">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="b1202-229">您可以從 [ [下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core) ] 頁面重新安裝 .Net core sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-229">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="b1202-230">這項工具可以卸載電腦上 framework 相依應用程式所需的 .NET Core 執行時間版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-230">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="b1202-231">您可以從 [ [下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core) ] 頁面重新安裝 .net core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-231">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="b1202-232">這項工具可以卸載 Visual Studio 依賴的 .NET Core SDK 和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-232">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="b1202-233">如果您中斷 Visual Studio 安裝，請在 Visual Studio 安裝程式中執行 [修復]，以回到工作狀態。</span><span class="sxs-lookup"><span data-stu-id="b1202-233">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="b1202-234">根據預設，所有命令都會保留 Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-234">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="b1202-235">您可以將這些 Sdk 和執行時間明確地列為引數或使用選項，以卸載這些 Sdk 和執行時間 `--force` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-235">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="b1202-236">此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-236">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="b1202-237">在 Windows 上和使用 macOS 上的系統管理員命令提示字元中執行此工具 `sudo` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-237">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="b1202-238">`dry-run`和 `whatif` 命令不需要提高許可權。</span><span class="sxs-lookup"><span data-stu-id="b1202-238">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="b1202-239">**dotnet-核心-卸載移除**</span><span class="sxs-lookup"><span data-stu-id="b1202-239">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b1202-240">概要</span><span class="sxs-lookup"><span data-stu-id="b1202-240">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="b1202-241">引數</span><span class="sxs-lookup"><span data-stu-id="b1202-241">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="b1202-242">要卸載的指定版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-242">The specified version to uninstall.</span></span> <span data-ttu-id="b1202-243">您可以列出多個版本，並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="b1202-243">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="b1202-244">也支援回應檔。</span><span class="sxs-lookup"><span data-stu-id="b1202-244">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="b1202-245">回應檔是在命令列上放置所有版本的替代方法。</span><span class="sxs-lookup"><span data-stu-id="b1202-245">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="b1202-246">它們是文字檔，通常 \* 會使用 .rsp 副檔名，而且每個版本都會列在個別的行上。</span><span class="sxs-lookup"><span data-stu-id="b1202-246">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="b1202-247">若要指定引數的回應檔 `VERSION` ，請使用 \@ 緊接在回應檔名稱後面的字元。</span><span class="sxs-lookup"><span data-stu-id="b1202-247">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="b1202-248">選項</span><span class="sxs-lookup"><span data-stu-id="b1202-248">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b1202-249">Windows</span><span class="sxs-lookup"><span data-stu-id="b1202-249">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="b1202-250">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-250">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="b1202-251">只會移除版本小於指定版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-251">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="b1202-252">指定的版本仍會保持安裝。</span><span class="sxs-lookup"><span data-stu-id="b1202-252">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="b1202-253">除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-253">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b1202-254">移除最高版本以外的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-254">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b1202-255">移除較高修補程式所取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-255">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b1202-256">此選項可保護上的 global.js。</span><span class="sxs-lookup"><span data-stu-id="b1202-256">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b1202-257">移除標記為預覽版的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-257">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b1202-258">移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。</span><span class="sxs-lookup"><span data-stu-id="b1202-258">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="b1202-259">只移除 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-259">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b1202-260">只會移除 .NET Core 裝載套件組合。</span><span class="sxs-lookup"><span data-stu-id="b1202-260">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b1202-261">移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-261">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b1202-262">僅移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-262">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b1202-263">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-263">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b1202-264">設定詳細程度層級。</span><span class="sxs-lookup"><span data-stu-id="b1202-264">Sets the verbosity level.</span></span> <span data-ttu-id="b1202-265">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b1202-265">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1202-266">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="b1202-266">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b1202-267">必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x64 sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="b1202-268">必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x86 sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-268">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="b1202-269">**`-y, --yes`** 執行命令，而不需要進行 [是] 或 [否] 確認。</span><span class="sxs-lookup"><span data-stu-id="b1202-269">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="b1202-270">**`--force`** 強制移除 Visual Studio 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-270">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="b1202-271">注意：</span><span class="sxs-lookup"><span data-stu-id="b1202-271">Notes:</span></span>

1. <span data-ttu-id="b1202-272">只需要、、和的其中一個 `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-272">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="b1202-273">`--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。</span><span class="sxs-lookup"><span data-stu-id="b1202-273">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="b1202-274">如果 `--x64` `--x86` 指定或未指定，則會移除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="b1202-274">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b1202-275">macOS</span><span class="sxs-lookup"><span data-stu-id="b1202-275">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="b1202-276">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-276">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="b1202-277">移除低於指定版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-277">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="b1202-278">指定的版本將會保留。</span><span class="sxs-lookup"><span data-stu-id="b1202-278">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="b1202-279">移除 .NET Core Sdk 和執行時間，但指定的版本除外。</span><span class="sxs-lookup"><span data-stu-id="b1202-279">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b1202-280">移除最高版本以外的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-280">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b1202-281">移除較高修補程式所取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-281">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b1202-282">此選項可保護上的 global.js。</span><span class="sxs-lookup"><span data-stu-id="b1202-282">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b1202-283">移除標記為預覽版的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-283">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b1202-284">移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。</span><span class="sxs-lookup"><span data-stu-id="b1202-284">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b1202-285">移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。</span><span class="sxs-lookup"><span data-stu-id="b1202-285">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b1202-286">僅移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-286">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b1202-287">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="b1202-287">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b1202-288">設定詳細程度層級。</span><span class="sxs-lookup"><span data-stu-id="b1202-288">Sets the verbosity level.</span></span> <span data-ttu-id="b1202-289">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b1202-289">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1202-290">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="b1202-290">The default value is `normal`.</span></span>

* <span data-ttu-id="b1202-291">**`-y, --yes`** 執行命令，而不需要進行 Y/N 確認。</span><span class="sxs-lookup"><span data-stu-id="b1202-291">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="b1202-292">**`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="b1202-292">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="b1202-293">注意：</span><span class="sxs-lookup"><span data-stu-id="b1202-293">Notes:</span></span>

1. <span data-ttu-id="b1202-294">只有其中一個 `--sdk` `--runtime` 是必要的。</span><span class="sxs-lookup"><span data-stu-id="b1202-294">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="b1202-295">`--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。</span><span class="sxs-lookup"><span data-stu-id="b1202-295">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="b1202-296">範例</span><span class="sxs-lookup"><span data-stu-id="b1202-296">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="b1202-297">根據預設，會保留 Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1202-297">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="b1202-298">在下列範例中，某些指定的 Sdk 和執行時間可能會保留，視機器的狀態而定。</span><span class="sxs-lookup"><span data-stu-id="b1202-298">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="b1202-299">若要移除所有 Sdk 和執行時間，請將它們明確地列為引數，或使用 `--force` 選項。</span><span class="sxs-lookup"><span data-stu-id="b1202-299">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="b1202-300">移除版本以外的所有 .NET Core 執行時間， `3.0.0-preview6-27804-01` 而不需要確認 Y/N：</span><span class="sxs-lookup"><span data-stu-id="b1202-300">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="b1202-301">移除所有 .NET Core 1.1 Sdk，而不需要進行 Y/n 確認：</span><span class="sxs-lookup"><span data-stu-id="b1202-301">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="b1202-302">移除沒有主控台輸出的 .NET Core 1.1.11 SDK：</span><span class="sxs-lookup"><span data-stu-id="b1202-302">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="b1202-303">移除此工具可以安全移除的所有 .NET Core Sdk：</span><span class="sxs-lookup"><span data-stu-id="b1202-303">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="b1202-304">移除此工具可以移除的所有 .NET Core Sdk，包括 Visual Studio (不建議) 所需的 Sdk：</span><span class="sxs-lookup"><span data-stu-id="b1202-304">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="b1202-305">移除回應檔案中指定的所有 .NET Core Sdk `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="b1202-305">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="b1202-306">*版本* 的內容如下所示：</span><span class="sxs-lookup"><span data-stu-id="b1202-306">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="b1202-307">步驟 4-刪除 NuGet fallback 資料夾 (選用) </span><span class="sxs-lookup"><span data-stu-id="b1202-307">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="b1202-308">在某些情況下，您不再需要， `NuGetFallbackFolder` 而且可能想要刪除它。</span><span class="sxs-lookup"><span data-stu-id="b1202-308">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="b1202-309">如需刪除此資料夾的詳細資訊，請參閱 [移除 NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。</span><span class="sxs-lookup"><span data-stu-id="b1202-309">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="b1202-310">卸載工具</span><span class="sxs-lookup"><span data-stu-id="b1202-310">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="b1202-311">Windows</span><span class="sxs-lookup"><span data-stu-id="b1202-311">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="b1202-312">開啟 [新增或移除程式]。</span><span class="sxs-lookup"><span data-stu-id="b1202-312">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="b1202-313">搜尋 `Microsoft .NET Core SDK Uninstall Tool`。</span><span class="sxs-lookup"><span data-stu-id="b1202-313">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="b1202-314">選取 [解除安裝]。</span><span class="sxs-lookup"><span data-stu-id="b1202-314">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b1202-315">macOS</span><span class="sxs-lookup"><span data-stu-id="b1202-315">macOS</span></span>](#tab/macos)

<span data-ttu-id="b1202-316">從其安裝所在的目錄中刪除下載的 *dotnet-core-uninstall gz* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b1202-316">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="b1202-317">如果您將此檔案的內容解壓縮到另一個目錄中，也請務必刪除該內容。</span><span class="sxs-lookup"><span data-stu-id="b1202-317">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
