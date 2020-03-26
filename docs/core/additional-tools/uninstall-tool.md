---
title: 卸載工具
description: .NET 核心卸載工具的概述，該工具是一種引導式工具，可控制清理 .NET 核心 SDK 和運行時。
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507317"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="0240f-103">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="0240f-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="0240f-104">[.NET 核心卸載工具](https://aka.ms/dotnet-core-uninstall-tool)（`dotnet-core-uninstall`） 允許您從系統中刪除 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="0240f-105">選項組合可用於指定要卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="0240f-106">該工具支援 Windows 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="0240f-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="0240f-107">目前不支援 Linux。</span><span class="sxs-lookup"><span data-stu-id="0240f-107">Linux is currently not supported.</span></span>

<span data-ttu-id="0240f-108">在 Windows 上，該工具只能卸載使用以下安裝程式之一安裝的 SDK 和運行時：</span><span class="sxs-lookup"><span data-stu-id="0240f-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="0240f-109">.NET 核心 SDK 和運行時安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0240f-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="0240f-110">Visual Studio 安裝程式的版本早于 Visual Studio 2019 版本 16.3。</span><span class="sxs-lookup"><span data-stu-id="0240f-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="0240f-111">在 macOS 上，該工具只能卸載*位於 /usr/local/share/dotnet*資料夾中的 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="0240f-112">由於這些限制，該工具可能無法在電腦上卸載所有 .NET Core SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="0240f-113">可以使用 該`dotnet --info`命令查找已安裝的所有 .NET 核心 SDK 和運行時，包括此工具無法刪除的 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="0240f-114">該`dotnet-core-uninstall list`命令顯示可以使用該工具卸載哪些 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="0240f-115">安裝工具</span><span class="sxs-lookup"><span data-stu-id="0240f-115">Install the tool</span></span>

<span data-ttu-id="0240f-116">您可以[在此處](https://aka.ms/dotnet-core-uninstall-tool)下載 .NET 核心卸載工具，並在[dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub 存儲庫中找到原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0240f-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="0240f-117">該工具需要提升才能卸載 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="0240f-118">因此，它應安裝在受寫入保護的目錄中，如 Windows 上的*C：*程式檔\*或 macOS 上的 */usr/local/bin。*</span><span class="sxs-lookup"><span data-stu-id="0240f-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="0240f-119">另請參閱[點網命令的提升訪問](../tools/elevated-access.md)。</span><span class="sxs-lookup"><span data-stu-id="0240f-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="0240f-120">有關詳細資訊，請參閱[詳細的安裝說明](https://aka.ms/dotnet-core-uninstall-tool)。</span><span class="sxs-lookup"><span data-stu-id="0240f-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="0240f-121">執行工具</span><span class="sxs-lookup"><span data-stu-id="0240f-121">Run the tool</span></span>

<span data-ttu-id="0240f-122">以下步驟顯示了運行卸載工具的建議方法：</span><span class="sxs-lookup"><span data-stu-id="0240f-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="0240f-123">步驟 1 - 顯示已安裝的 .NET 核心 SDK 和運行時</span><span class="sxs-lookup"><span data-stu-id="0240f-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="0240f-124">第 2 步 - 進行幹跑</span><span class="sxs-lookup"><span data-stu-id="0240f-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="0240f-125">步驟 3 - 卸載 .NET 核心 SDK 和運行時</span><span class="sxs-lookup"><span data-stu-id="0240f-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="0240f-126">步驟 4 - 刪除 NuGet 回退資料夾（可選）</span><span class="sxs-lookup"><span data-stu-id="0240f-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="0240f-127">步驟 1 - 顯示已安裝的 .NET 核心 SDK 和運行時</span><span class="sxs-lookup"><span data-stu-id="0240f-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="0240f-128">該`dotnet-core-uninstall list`命令列出了可使用此工具刪除的已安裝的 .NET Core SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="0240f-129">Visual Studio 可能需要某些 SDK 和運行時，並且顯示它們時會記下為什麼不建議卸載它們。</span><span class="sxs-lookup"><span data-stu-id="0240f-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="0240f-130">在大多數情況下，`dotnet-core-uninstall list`命令的輸出與 已`dotnet --info`安裝版本的清單不匹配。</span><span class="sxs-lookup"><span data-stu-id="0240f-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="0240f-131">具體來說，此工具不會顯示由 ZIP 檔案安裝或由 Visual Studio 管理的版本（任何與 Visual Studio 2019 16.3 或更高版本一起安裝的版本）。</span><span class="sxs-lookup"><span data-stu-id="0240f-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="0240f-132">檢查版本是否由 Visual Studio 管理的方法之一是在 中`Add or Remove Programs`查看它，其中 Visual Studio 託管版本在其顯示名稱中標記為此類版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="0240f-133">**點網核心卸載清單**</span><span class="sxs-lookup"><span data-stu-id="0240f-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="0240f-134">概要</span><span class="sxs-lookup"><span data-stu-id="0240f-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="0240f-135">選項。</span><span class="sxs-lookup"><span data-stu-id="0240f-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="0240f-136">Windows</span><span class="sxs-lookup"><span data-stu-id="0240f-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="0240f-137">列出可以使用此工具卸載的所有ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="0240f-138">列出可以使用此工具卸載的所有 .NET Core 運行時和託管包。</span><span class="sxs-lookup"><span data-stu-id="0240f-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="0240f-139">列出可以使用此工具卸載的所有 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="0240f-140">列出可以使用此工具卸載的所有 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="0240f-141">設置詳細程度級別。</span><span class="sxs-lookup"><span data-stu-id="0240f-141">Sets the verbosity level.</span></span> <span data-ttu-id="0240f-142">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0240f-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0240f-143">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="0240f-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="0240f-144">列出可以使用此工具卸載的所有 x64 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="0240f-145">列出可以使用此工具卸載的所有 x86 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="0240f-146">macOS</span><span class="sxs-lookup"><span data-stu-id="0240f-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="0240f-147">列出可以使用此工具卸載的所有 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="0240f-148">列出可以使用此工具卸載的所有 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="0240f-149">設置詳細程度級別。</span><span class="sxs-lookup"><span data-stu-id="0240f-149">Sets the verbosity level.</span></span> <span data-ttu-id="0240f-150">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0240f-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0240f-151">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="0240f-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="0240f-152">範例</span><span class="sxs-lookup"><span data-stu-id="0240f-152">Examples</span></span>

* <span data-ttu-id="0240f-153">列出可以使用此工具刪除的所有 .NET 核心 SDK 和運行時：</span><span class="sxs-lookup"><span data-stu-id="0240f-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="0240f-154">列出所有 x64 .NET 核心 SDK 和運行時：</span><span class="sxs-lookup"><span data-stu-id="0240f-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="0240f-155">列出所有 x86 .NET 核心 SDK：</span><span class="sxs-lookup"><span data-stu-id="0240f-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="0240f-156">第 2 步 - 進行幹跑</span><span class="sxs-lookup"><span data-stu-id="0240f-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="0240f-157">`dotnet-core-uninstall dry-run`和`dotnet-core-uninstall whatif`命令顯示 .NET Core SDK 和運行時，將根據提供的選項在不執行卸載的情況下刪除這些選項。</span><span class="sxs-lookup"><span data-stu-id="0240f-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="0240f-158">這些命令是同義字。</span><span class="sxs-lookup"><span data-stu-id="0240f-158">These commands are synonyms.</span></span>

<span data-ttu-id="0240f-159">**點網-核心卸載幹運行和點網核心卸載什麼**</span><span class="sxs-lookup"><span data-stu-id="0240f-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="0240f-160">概要</span><span class="sxs-lookup"><span data-stu-id="0240f-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="0240f-161">引數</span><span class="sxs-lookup"><span data-stu-id="0240f-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="0240f-162">要卸載的指定版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-162">The specified version to uninstall.</span></span> <span data-ttu-id="0240f-163">您可以逐個列出多個版本，由空格分隔。</span><span class="sxs-lookup"><span data-stu-id="0240f-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="0240f-164">還支援回應檔。</span><span class="sxs-lookup"><span data-stu-id="0240f-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="0240f-165">回應檔是將所有版本放在命令列上的替代方法。</span><span class="sxs-lookup"><span data-stu-id="0240f-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="0240f-166">它們是文字檔，通常帶有\*.rsp 副檔名，每個版本都列在單獨的行上。</span><span class="sxs-lookup"><span data-stu-id="0240f-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="0240f-167">要為`VERSION`參數指定回應檔，請使用該\@字元，緊跟回應檔案名。</span><span class="sxs-lookup"><span data-stu-id="0240f-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="0240f-168">選項。</span><span class="sxs-lookup"><span data-stu-id="0240f-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="0240f-169">Windows</span><span class="sxs-lookup"><span data-stu-id="0240f-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="0240f-170">刪除所有 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="0240f-171">僅刪除版本小於指定版本的 .NET Core SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="0240f-172">指定的版本將保持安裝狀態。</span><span class="sxs-lookup"><span data-stu-id="0240f-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="0240f-173">刪除所有 .NET 核心 SDK 和運行時，但指定的版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="0240f-174">刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="0240f-175">刪除 .NET 核心 SDK，運行時被較高的修補程式取代。</span><span class="sxs-lookup"><span data-stu-id="0240f-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="0240f-176">此選項保護全域.json。</span><span class="sxs-lookup"><span data-stu-id="0240f-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="0240f-177">刪除 .NET 核心 SDK 和標記為預覽的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="0240f-178">刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="0240f-179">僅刪除ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="0240f-180">僅刪除 .NET 核心運行時和託管捆綁包。</span><span class="sxs-lookup"><span data-stu-id="0240f-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="0240f-181">刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="0240f-182">僅刪除 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="0240f-183">僅刪除 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="0240f-184">設置詳細程度級別。</span><span class="sxs-lookup"><span data-stu-id="0240f-184">Sets the verbosity level.</span></span> <span data-ttu-id="0240f-185">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0240f-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0240f-186">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="0240f-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="0240f-187">必須與 一`--sdk`起使用`--runtime`，並`--aspnet-runtime`刪除 x64 SDK 或運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="0240f-188">必須與 和`--sdk``--runtime`一起使用`--aspnet-runtime`，並刪除 x86 SDK 或運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="0240f-189">**`--force`** 強制刪除視覺工作室可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="0240f-190">注意：</span><span class="sxs-lookup"><span data-stu-id="0240f-190">Notes:</span></span>

1. <span data-ttu-id="0240f-191">是 、 `--sdk` `--runtime`和`--aspnet-runtime``--hosting-bundle`的一個。</span><span class="sxs-lookup"><span data-stu-id="0240f-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="0240f-192">`--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`</span><span class="sxs-lookup"><span data-stu-id="0240f-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="0240f-193">如果`--x64`或`--x86`未指定，則將刪除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="0240f-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="0240f-194">macOS</span><span class="sxs-lookup"><span data-stu-id="0240f-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="0240f-195">刪除所有 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="0240f-196">刪除 .NET 核心 SDK 和低於指定版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="0240f-197">指定的版本將保留。</span><span class="sxs-lookup"><span data-stu-id="0240f-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="0240f-198">刪除 .NET 核心 SDK 和運行時，但指定的版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="0240f-199">刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="0240f-200">刪除 .NET 核心 SDK，運行時被較高的修補程式取代。</span><span class="sxs-lookup"><span data-stu-id="0240f-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="0240f-201">此選項保護全域.json。</span><span class="sxs-lookup"><span data-stu-id="0240f-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="0240f-202">刪除 .NET 核心 SDK 和標記為預覽的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="0240f-203">刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="0240f-204">刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="0240f-205">僅刪除 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="0240f-206">僅刪除 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="0240f-207">設置詳細程度級別。</span><span class="sxs-lookup"><span data-stu-id="0240f-207">Sets the verbosity level.</span></span> <span data-ttu-id="0240f-208">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0240f-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0240f-209">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="0240f-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="0240f-210">**`--force`** 強制刪除視覺工作室或 SDK 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="0240f-211">注意：</span><span class="sxs-lookup"><span data-stu-id="0240f-211">Notes:</span></span>

1. <span data-ttu-id="0240f-212">正好是`--sdk`和`--runtime`，</span><span class="sxs-lookup"><span data-stu-id="0240f-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="0240f-213">`--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`</span><span class="sxs-lookup"><span data-stu-id="0240f-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="0240f-214">範例</span><span class="sxs-lookup"><span data-stu-id="0240f-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="0240f-215">預設情況下，輸出中`dotnet-core-uninstall dry-run`不包括 Visual Studio 或其他 SDK 可能需要的 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="0240f-216">在以下示例中，某些指定的 SDK 和運行時可能不包含在輸出中，具體取決於電腦的狀態。</span><span class="sxs-lookup"><span data-stu-id="0240f-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="0240f-217">要包括所有 SDK 和運行時，請將其顯式列為參數或使用 選項`--force`。</span><span class="sxs-lookup"><span data-stu-id="0240f-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="0240f-218">刪除已被更高修補程式取代的所有 .NET Core 運行時的幹運行：</span><span class="sxs-lookup"><span data-stu-id="0240f-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="0240f-219">刪除版本`2.2.301`以下的所有 .NET 核心 SDK 的幹運行：</span><span class="sxs-lookup"><span data-stu-id="0240f-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="0240f-220">步驟 3 - 卸載 .NET 核心 SDK 和運行時</span><span class="sxs-lookup"><span data-stu-id="0240f-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="0240f-221">`dotnet-core-uninstall remove`卸載 .NET 核心 SDK 和執行時間，這些 SDK 由選項組合指定。</span><span class="sxs-lookup"><span data-stu-id="0240f-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="0240f-222">該工具不能用於卸載版本 5.0 或以上版本的 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="0240f-223">由於此工具具有破壞性行為，因此**強烈建議**您在運行刪除命令之前進行幹運行。</span><span class="sxs-lookup"><span data-stu-id="0240f-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="0240f-224">幹運行將顯示使用`remove`命令時將刪除什麼 .NET Core SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="0240f-225">請參閱[是否應刪除版本？](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)以瞭解哪些 SDK 和運行時可以安全刪除。</span><span class="sxs-lookup"><span data-stu-id="0240f-225">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="0240f-226">請記住下列注意事項：</span><span class="sxs-lookup"><span data-stu-id="0240f-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="0240f-227">此工具可以卸載電腦上的`global.json`檔所需的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="0240f-228">可以從[下載 .NET 核心](https://dotnet.microsoft.com/download/dotnet-core)頁面重新安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="0240f-229">此工具可以卸載電腦上依賴于框架的應用程式所需的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="0240f-230">可以從[下載 .NET 核心](https://dotnet.microsoft.com/download/dotnet-core)頁面重新安裝 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="0240f-231">此工具可以卸載 Visual Studio 所依賴的 .NET 核心 SDK 和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="0240f-232">如果中斷 Visual Studio 安裝，請在 Visual Studio 安裝程式中運行"修復"以返回工作狀態。</span><span class="sxs-lookup"><span data-stu-id="0240f-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="0240f-233">預設情況下，所有命令都保留 Visual Studio 或其他 SDK 可能需要的 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="0240f-234">可以通過顯式將它們列為參數或使用 選項`--force`來卸載這些 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="0240f-235">該工具需要提升才能卸載 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="0240f-236">在 Windows 上和 macOS`sudo`上以管理員命令提示符運行該工具。</span><span class="sxs-lookup"><span data-stu-id="0240f-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="0240f-237">`dry-run`和`whatif`命令不需要高程。</span><span class="sxs-lookup"><span data-stu-id="0240f-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="0240f-238">**點網核心卸載刪除**</span><span class="sxs-lookup"><span data-stu-id="0240f-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="0240f-239">概要</span><span class="sxs-lookup"><span data-stu-id="0240f-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="0240f-240">引數</span><span class="sxs-lookup"><span data-stu-id="0240f-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="0240f-241">要卸載的指定版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-241">The specified version to uninstall.</span></span> <span data-ttu-id="0240f-242">您可以逐個列出多個版本，由空格分隔。</span><span class="sxs-lookup"><span data-stu-id="0240f-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="0240f-243">還支援回應檔。</span><span class="sxs-lookup"><span data-stu-id="0240f-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="0240f-244">回應檔是將所有版本放在命令列上的替代方法。</span><span class="sxs-lookup"><span data-stu-id="0240f-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="0240f-245">它們是文字檔，通常帶有\*.rsp 副檔名，每個版本都列在單獨的行上。</span><span class="sxs-lookup"><span data-stu-id="0240f-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="0240f-246">要為`VERSION`參數指定回應檔，請使用該\@字元，緊跟回應檔案名。</span><span class="sxs-lookup"><span data-stu-id="0240f-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="0240f-247">選項。</span><span class="sxs-lookup"><span data-stu-id="0240f-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="0240f-248">Windows</span><span class="sxs-lookup"><span data-stu-id="0240f-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="0240f-249">刪除所有 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="0240f-250">僅刪除版本小於指定版本的 .NET Core SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="0240f-251">指定的版本將保持安裝狀態。</span><span class="sxs-lookup"><span data-stu-id="0240f-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="0240f-252">刪除所有 .NET 核心 SDK 和運行時，但指定的版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="0240f-253">刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="0240f-254">刪除 .NET 核心 SDK，運行時被較高的修補程式取代。</span><span class="sxs-lookup"><span data-stu-id="0240f-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="0240f-255">此選項保護全域.json。</span><span class="sxs-lookup"><span data-stu-id="0240f-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="0240f-256">刪除 .NET 核心 SDK 和標記為預覽的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="0240f-257">刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="0240f-258">僅刪除ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="0240f-259">僅刪除 .NET 核心運行時和託管捆綁包。</span><span class="sxs-lookup"><span data-stu-id="0240f-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="0240f-260">刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="0240f-261">僅刪除 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="0240f-262">僅刪除 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="0240f-263">設置詳細程度級別。</span><span class="sxs-lookup"><span data-stu-id="0240f-263">Sets the verbosity level.</span></span> <span data-ttu-id="0240f-264">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0240f-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0240f-265">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="0240f-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="0240f-266">必須與 一`--sdk`起使用`--runtime`，並`--aspnet-runtime`刪除 x64 SDK 或運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="0240f-267">必須與 和`--sdk``--runtime`一起使用`--aspnet-runtime`，並刪除 x86 SDK 或運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="0240f-268">**`-y, --yes`** 執行命令，無需確認或確認。</span><span class="sxs-lookup"><span data-stu-id="0240f-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="0240f-269">**`--force`** 強制刪除視覺工作室可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="0240f-270">注意：</span><span class="sxs-lookup"><span data-stu-id="0240f-270">Notes:</span></span>

1. <span data-ttu-id="0240f-271">是 、 `--sdk` `--runtime`和`--aspnet-runtime``--hosting-bundle`的一個。</span><span class="sxs-lookup"><span data-stu-id="0240f-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="0240f-272">`--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`</span><span class="sxs-lookup"><span data-stu-id="0240f-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="0240f-273">如果`--x64`或`--x86`未指定，則將刪除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="0240f-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="0240f-274">macOS</span><span class="sxs-lookup"><span data-stu-id="0240f-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="0240f-275">刪除所有 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="0240f-276">刪除 .NET 核心 SDK 和低於指定版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="0240f-277">指定的版本將保留。</span><span class="sxs-lookup"><span data-stu-id="0240f-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="0240f-278">刪除 .NET 核心 SDK 和運行時，但指定的版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="0240f-279">刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="0240f-280">刪除 .NET 核心 SDK，運行時被較高的修補程式取代。</span><span class="sxs-lookup"><span data-stu-id="0240f-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="0240f-281">此選項保護全域.json。</span><span class="sxs-lookup"><span data-stu-id="0240f-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="0240f-282">刪除 .NET 核心 SDK 和標記為預覽的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="0240f-283">刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。</span><span class="sxs-lookup"><span data-stu-id="0240f-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="0240f-284">刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="0240f-285">僅刪除 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="0240f-286">僅刪除 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="0240f-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="0240f-287">設置詳細程度級別。</span><span class="sxs-lookup"><span data-stu-id="0240f-287">Sets the verbosity level.</span></span> <span data-ttu-id="0240f-288">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0240f-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0240f-289">預設值是 `normal`。</span><span class="sxs-lookup"><span data-stu-id="0240f-289">The default value is `normal`.</span></span>

* <span data-ttu-id="0240f-290">**`-y, --yes`** 執行命令，無需 Y/N 確認。</span><span class="sxs-lookup"><span data-stu-id="0240f-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="0240f-291">**`--force`** 強制刪除視覺工作室或 SDK 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="0240f-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="0240f-292">注意：</span><span class="sxs-lookup"><span data-stu-id="0240f-292">Notes:</span></span>

1. <span data-ttu-id="0240f-293">正好是`--sdk`和`--runtime`，</span><span class="sxs-lookup"><span data-stu-id="0240f-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="0240f-294">`--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`</span><span class="sxs-lookup"><span data-stu-id="0240f-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="0240f-295">範例</span><span class="sxs-lookup"><span data-stu-id="0240f-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="0240f-296">預設情況下，保留 Visual Studio 或其他 SDK 可能需要的 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="0240f-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="0240f-297">在以下示例中，某些指定的 SDK 和運行時可能會保留，具體取決於電腦的狀態。</span><span class="sxs-lookup"><span data-stu-id="0240f-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="0240f-298">要刪除所有 SDK 和運行時，請將其顯式列為參數或使用 選項`--force`。</span><span class="sxs-lookup"><span data-stu-id="0240f-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="0240f-299">刪除除版本`3.0.0-preview6-27804-01`外的所有 .NET 核心運行時，無需 Y/N 確認：</span><span class="sxs-lookup"><span data-stu-id="0240f-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="0240f-300">刪除所有 .NET 核心 1.1 SDK，無需 Y/n 確認：</span><span class="sxs-lookup"><span data-stu-id="0240f-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="0240f-301">刪除 .NET 核心 1.1.11 SDK，無需主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="0240f-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="0240f-302">刪除此工具可以安全地刪除的所有 .NET 核心 SDK：</span><span class="sxs-lookup"><span data-stu-id="0240f-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="0240f-303">刪除此工具可以刪除的所有 .NET 核心 SDK，包括 Visual Studio 可能需要的 SDK（不推薦）：</span><span class="sxs-lookup"><span data-stu-id="0240f-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="0240f-304">刪除回應檔中指定的所有 .NET 核心 SDK`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="0240f-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="0240f-305">*版本.rsp*的內容如下：</span><span class="sxs-lookup"><span data-stu-id="0240f-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="0240f-306">步驟 4 - 刪除 NuGet 回退資料夾（可選）</span><span class="sxs-lookup"><span data-stu-id="0240f-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="0240f-307">在某些情況下，您不再需要 ，`NuGetFallbackFolder`並且可能希望將其刪除。</span><span class="sxs-lookup"><span data-stu-id="0240f-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="0240f-308">有關刪除此資料夾的詳細資訊，請參閱[刪除 NuGet 回資料夾](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。</span><span class="sxs-lookup"><span data-stu-id="0240f-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="0240f-309">卸載工具</span><span class="sxs-lookup"><span data-stu-id="0240f-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="0240f-310">Windows</span><span class="sxs-lookup"><span data-stu-id="0240f-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="0240f-311">開啟 [新增或移除程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0240f-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="0240f-312">搜尋 `Microsoft .NET Core SDK Uninstall Tool`。</span><span class="sxs-lookup"><span data-stu-id="0240f-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="0240f-313">選取 [解除安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0240f-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="0240f-314">macOS</span><span class="sxs-lookup"><span data-stu-id="0240f-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="0240f-315">從安裝該檔的目錄中刪除下載的*dotnet-core 卸載.tar.gz*檔。</span><span class="sxs-lookup"><span data-stu-id="0240f-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="0240f-316">如果將此檔的內容解壓縮到另一個目錄中，請確保也刪除該內容。</span><span class="sxs-lookup"><span data-stu-id="0240f-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
