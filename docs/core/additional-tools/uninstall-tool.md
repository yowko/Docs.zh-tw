---
title: 解除安裝工具
description: 概述 .NET Core 卸載工具，這是一個引導式工具，可讓您控制 .NET Core Sdk 和執行時間的清理。
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 4944c983cbd02b456c3a09a1b03bc28ba6e458cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714545"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="3d380-103">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="3d380-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="3d380-104">[.Net Core 卸載工具](https://github.com/dotnet/cli-lab/releases)（`dotnet-core-uninstall`）可讓您從系統中移除 .Net Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-104">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="3d380-105">有一組選項可用來指定您要卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="3d380-106">此工具支援 Windows 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="3d380-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="3d380-107">目前不支援 Linux。</span><span class="sxs-lookup"><span data-stu-id="3d380-107">Linux is currently not supported.</span></span>

<span data-ttu-id="3d380-108">在 Windows 上，此工具只能使用下列其中一個安裝程式來卸載已安裝的 Sdk 和執行時間：</span><span class="sxs-lookup"><span data-stu-id="3d380-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="3d380-109">.NET Core SDK 和執行時間安裝程式。</span><span class="sxs-lookup"><span data-stu-id="3d380-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="3d380-110">Visual Studio 安裝程式的版本早于 Visual Studio 2019 16.3 版。</span><span class="sxs-lookup"><span data-stu-id="3d380-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="3d380-111">在 macOS 上，此工具只能卸載位於 */usr/local/share/dotnet*資料夾中的 sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="3d380-112">基於這些限制，此工具可能無法卸載您電腦上的所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="3d380-113">您可以使用 `dotnet --info` 命令來尋找已安裝的所有 .NET Core Sdk 和執行時間，包括此工具無法移除的 Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="3d380-114">`dotnet-core-uninstall list` 命令會顯示哪些 Sdk 可以使用工具卸載。</span><span class="sxs-lookup"><span data-stu-id="3d380-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="3d380-115">安裝工具</span><span class="sxs-lookup"><span data-stu-id="3d380-115">Install the tool</span></span>

<span data-ttu-id="3d380-116">您可以從[dotnet/cli-實驗室](https://github.com/dotnet/cli-lab/releases)GitHub 存放庫下載 .Net Core 卸載工具。</span><span class="sxs-lookup"><span data-stu-id="3d380-116">You can download the .NET Core Uninstall Tool from the [dotnet/cli-lab](https://github.com/dotnet/cli-lab/releases) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="3d380-117">此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="3d380-118">因此，它應該安裝在受寫入保護的目錄中，例如 Windows 上的*C:\Program*檔案或 macOS 上的 */usr/local/bin* 。</span><span class="sxs-lookup"><span data-stu-id="3d380-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="3d380-119">另請參閱[dotnet 命令的更高存取權](../tools/elevated-access.md)。</span><span class="sxs-lookup"><span data-stu-id="3d380-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="3d380-120">您可以在[GitHub 版本頁面](https://github.com/dotnet/cli-lab/releases)上取得詳細的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="3d380-120">Detailed installation instructions are available on the [GitHub Releases page](https://github.com/dotnet/cli-lab/releases).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="3d380-121">執行工具</span><span class="sxs-lookup"><span data-stu-id="3d380-121">Run the tool</span></span>

<span data-ttu-id="3d380-122">下列步驟顯示執行卸載工具的建議方法：</span><span class="sxs-lookup"><span data-stu-id="3d380-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="3d380-123">步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="3d380-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="3d380-124">步驟 2-進行試執行</span><span class="sxs-lookup"><span data-stu-id="3d380-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="3d380-125">步驟 3-卸載 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="3d380-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="3d380-126">步驟 4-刪除 NuGet fallback 資料夾（選擇性）</span><span class="sxs-lookup"><span data-stu-id="3d380-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="3d380-127">步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="3d380-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="3d380-128">`dotnet-core-uninstall list` 命令會列出已安裝的 .NET Core Sdk 和可使用此工具移除的執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="3d380-129">Visual Studio 可能需要一些 Sdk 和執行時間，而且會顯示不建議將它們卸載的原因。</span><span class="sxs-lookup"><span data-stu-id="3d380-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="3d380-130">**dotnet-核心-卸載清單**</span><span class="sxs-lookup"><span data-stu-id="3d380-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="3d380-131">概要</span><span class="sxs-lookup"><span data-stu-id="3d380-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="3d380-132">選項</span><span class="sxs-lookup"><span data-stu-id="3d380-132">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="3d380-133">Windows</span><span class="sxs-lookup"><span data-stu-id="3d380-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="3d380-134">列出所有可使用此工具卸載的 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="3d380-135">列出所有可使用此工具卸載的 .NET Core 執行時間和裝載套件組合。</span><span class="sxs-lookup"><span data-stu-id="3d380-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="3d380-136">列出所有可使用此工具卸載的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="3d380-137">列出所有可使用此工具卸載的 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="3d380-138">設定詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3d380-138">Sets the verbosity level.</span></span> <span data-ttu-id="3d380-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3d380-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3d380-140">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="3d380-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="3d380-141">列出所有可使用此工具卸載的 x64 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="3d380-142">列出所有可使用此工具卸載的 x86 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="3d380-143">macOS</span><span class="sxs-lookup"><span data-stu-id="3d380-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="3d380-144">列出所有可使用此工具卸載的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="3d380-145">列出所有可使用此工具卸載的 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="3d380-146">設定詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3d380-146">Sets the verbosity level.</span></span> <span data-ttu-id="3d380-147">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3d380-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3d380-148">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="3d380-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="3d380-149">範例</span><span class="sxs-lookup"><span data-stu-id="3d380-149">Examples</span></span>

* <span data-ttu-id="3d380-150">列出所有可使用此工具移除的 .NET Core Sdk 和執行時間：</span><span class="sxs-lookup"><span data-stu-id="3d380-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="3d380-151">列出所有 x64 .NET Core Sdk 和執行時間：</span><span class="sxs-lookup"><span data-stu-id="3d380-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="3d380-152">列出所有的 x86 .NET Core Sdk：</span><span class="sxs-lookup"><span data-stu-id="3d380-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="3d380-153">步驟 2-進行試執行</span><span class="sxs-lookup"><span data-stu-id="3d380-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="3d380-154">[`dotnet-core-uninstall dry-run`] 和 [`dotnet-core-uninstall whatif`] 命令會顯示 .NET Core Sdk 和執行時間，將會根據所提供的選項而移除，而不需執行卸載。</span><span class="sxs-lookup"><span data-stu-id="3d380-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="3d380-155">這些命令是同義字。</span><span class="sxs-lookup"><span data-stu-id="3d380-155">These commands are synonyms.</span></span>

<span data-ttu-id="3d380-156">**dotnet-核心-卸載試執行和 dotnet-核心-卸載 whatif**</span><span class="sxs-lookup"><span data-stu-id="3d380-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="3d380-157">概要</span><span class="sxs-lookup"><span data-stu-id="3d380-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="3d380-158">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d380-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="3d380-159">要卸載的指定版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-159">The specified version to uninstall.</span></span> <span data-ttu-id="3d380-160">您可以逐一列出數個版本，並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="3d380-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="3d380-161">也支援回應檔案。</span><span class="sxs-lookup"><span data-stu-id="3d380-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="3d380-162">回應檔案是將所有版本放在命令列上的替代方案。</span><span class="sxs-lookup"><span data-stu-id="3d380-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="3d380-163">它們是文字檔，通常具有 \*.rsp 副檔名，而每個版本都會列在個別的一行上。</span><span class="sxs-lookup"><span data-stu-id="3d380-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="3d380-164">若要指定 `VERSION` 引數的回應檔，請使用緊接在回應檔名稱後面的 \@ 字元。</span><span class="sxs-lookup"><span data-stu-id="3d380-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="3d380-165">選項</span><span class="sxs-lookup"><span data-stu-id="3d380-165">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="3d380-166">Windows</span><span class="sxs-lookup"><span data-stu-id="3d380-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="3d380-167">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="3d380-168">只移除版本小於指定版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="3d380-169">指定的版本仍會安裝。</span><span class="sxs-lookup"><span data-stu-id="3d380-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="3d380-170">除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="3d380-171">移除 .NET Core Sdk 和執行時間，但不含最高版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="3d380-172">移除由較高修補程式取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="3d380-173">此選項可保護 global. json。</span><span class="sxs-lookup"><span data-stu-id="3d380-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="3d380-174">移除標示為預覽的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="3d380-175">移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。</span><span class="sxs-lookup"><span data-stu-id="3d380-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="3d380-176">只移除 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="3d380-177">只會移除 .NET Core 執行時間和裝載套件組合。</span><span class="sxs-lookup"><span data-stu-id="3d380-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="3d380-178">移除符合指定之 `major.minor` 版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="3d380-179">只會移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="3d380-180">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="3d380-181">設定詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3d380-181">Sets the verbosity level.</span></span> <span data-ttu-id="3d380-182">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3d380-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3d380-183">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="3d380-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="3d380-184">必須搭配 `--sdk`、`--runtime`和 `--aspnet-runtime` 使用，才能移除 x64 Sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="3d380-185">必須搭配 `--sdk`、`--runtime`和 `--aspnet-runtime` 使用，才能移除 x86 Sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="3d380-186">**`--force`** 強制移除 Visual Studio 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="3d380-187">附註：</span><span class="sxs-lookup"><span data-stu-id="3d380-187">Notes:</span></span>

1. <span data-ttu-id="3d380-188">只需要其中一個 `--sdk`、`--runtime`、`--aspnet-runtime`和 `--hosting-bundle`。</span><span class="sxs-lookup"><span data-stu-id="3d380-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="3d380-189">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor`和 `[<VERSION>...]` 都是獨佔的。</span><span class="sxs-lookup"><span data-stu-id="3d380-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="3d380-190">如果未指定 `--x64` 或 `--x86`，則會移除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="3d380-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="3d380-191">macOS</span><span class="sxs-lookup"><span data-stu-id="3d380-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="3d380-192">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="3d380-193">移除指定版本底下的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="3d380-194">指定的版本將會保留。</span><span class="sxs-lookup"><span data-stu-id="3d380-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="3d380-195">除了指定的版本之外，移除 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="3d380-196">移除 .NET Core Sdk 和執行時間，但不含最高版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="3d380-197">移除由較高修補程式取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="3d380-198">此選項可保護 global. json。</span><span class="sxs-lookup"><span data-stu-id="3d380-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="3d380-199">移除標示為預覽的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="3d380-200">移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。</span><span class="sxs-lookup"><span data-stu-id="3d380-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="3d380-201">移除符合指定之 `major.minor` 版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="3d380-202">只會移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="3d380-203">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="3d380-204">設定詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3d380-204">Sets the verbosity level.</span></span> <span data-ttu-id="3d380-205">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3d380-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3d380-206">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="3d380-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="3d380-207">**`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="3d380-208">附註：</span><span class="sxs-lookup"><span data-stu-id="3d380-208">Notes:</span></span>

1. <span data-ttu-id="3d380-209">只需要其中一個 `--sdk` 和 `--runtime`。</span><span class="sxs-lookup"><span data-stu-id="3d380-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="3d380-210">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor`和 `[<VERSION>...]` 都是獨佔的。</span><span class="sxs-lookup"><span data-stu-id="3d380-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="3d380-211">範例</span><span class="sxs-lookup"><span data-stu-id="3d380-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="3d380-212">根據預設，Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間不會包含在 `dotnet-core-uninstall dry-run` 輸出中。</span><span class="sxs-lookup"><span data-stu-id="3d380-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="3d380-213">在下列範例中，某些指定的 Sdk 和執行時間可能不會包含在輸出中，視電腦的狀態而定。</span><span class="sxs-lookup"><span data-stu-id="3d380-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="3d380-214">若要包含所有 Sdk 和執行時間，請將它們明確地列為引數，或使用 [`--force`] 選項。</span><span class="sxs-lookup"><span data-stu-id="3d380-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="3d380-215">試執行移除所有已被較高修補程式取代的 .NET Core 執行時間：</span><span class="sxs-lookup"><span data-stu-id="3d380-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="3d380-216">在 `2.2.301`版本底下移除所有 .NET Core Sdk 的試執行：</span><span class="sxs-lookup"><span data-stu-id="3d380-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="3d380-217">步驟 3-卸載 .NET Core Sdk 和執行時間</span><span class="sxs-lookup"><span data-stu-id="3d380-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="3d380-218">`dotnet-core-uninstall remove` 會卸載由選項組合所指定的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="3d380-219">此工具無法用來卸載版本5.0 或更高版本的 Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="3d380-220">由於此工具具有破壞性的行為，因此**強烈**建議您在執行 [移除] 命令之前先進行試執行。</span><span class="sxs-lookup"><span data-stu-id="3d380-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="3d380-221">試執行會顯示當您使用 `remove` 命令時，將會移除哪些 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="3d380-222">請參閱[我應該移除版本嗎？](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)以瞭解哪些 sdk 和執行時間可以安全地移除。</span><span class="sxs-lookup"><span data-stu-id="3d380-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="3d380-223">請記住下列注意事項：</span><span class="sxs-lookup"><span data-stu-id="3d380-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="3d380-224">這項工具可以卸載電腦上 `global.json` 檔案所需的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="3d380-225">您可以從[下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core)頁面重新安裝 .Net core sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="3d380-226">這項工具可以卸載電腦上架構相依應用程式所需的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="3d380-227">您可以從 [[下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core) ] 頁面重新安裝 .net core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="3d380-228">這項工具可以卸載 Visual Studio 依賴之 .NET Core SDK 和執行時間的版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="3d380-229">如果您中斷 Visual Studio 安裝，請在 Visual Studio 安裝程式中執行 [修復]，以回到作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="3d380-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="3d380-230">根據預設，所有命令都會保留 Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="3d380-231">這些 Sdk 和執行時間可以藉由將它們明確地列為引數或使用 `--force` 選項來進行卸載。</span><span class="sxs-lookup"><span data-stu-id="3d380-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="3d380-232">此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="3d380-233">在 Windows 上的系統管理員命令提示字元中執行工具，並在 macOS 上使用 `sudo`。</span><span class="sxs-lookup"><span data-stu-id="3d380-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="3d380-234">`dry-run` 和 `whatif` 命令不需要提高許可權。</span><span class="sxs-lookup"><span data-stu-id="3d380-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="3d380-235">**dotnet-核心-卸載移除**</span><span class="sxs-lookup"><span data-stu-id="3d380-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="3d380-236">概要</span><span class="sxs-lookup"><span data-stu-id="3d380-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="3d380-237">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d380-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="3d380-238">要卸載的指定版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-238">The specified version to uninstall.</span></span> <span data-ttu-id="3d380-239">您可以逐一列出數個版本，並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="3d380-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="3d380-240">也支援回應檔案。</span><span class="sxs-lookup"><span data-stu-id="3d380-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="3d380-241">回應檔案是將所有版本放在命令列上的替代方案。</span><span class="sxs-lookup"><span data-stu-id="3d380-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="3d380-242">它們是文字檔，通常具有 \*.rsp 副檔名，而每個版本都會列在個別的一行上。</span><span class="sxs-lookup"><span data-stu-id="3d380-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="3d380-243">若要指定 `VERSION` 引數的回應檔，請使用緊接在回應檔名稱後面的 \@ 字元。</span><span class="sxs-lookup"><span data-stu-id="3d380-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="3d380-244">選項</span><span class="sxs-lookup"><span data-stu-id="3d380-244">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="3d380-245">Windows</span><span class="sxs-lookup"><span data-stu-id="3d380-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="3d380-246">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="3d380-247">只移除版本小於指定版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="3d380-248">指定的版本仍會安裝。</span><span class="sxs-lookup"><span data-stu-id="3d380-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="3d380-249">除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="3d380-250">移除 .NET Core Sdk 和執行時間，但不含最高版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="3d380-251">移除由較高修補程式取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="3d380-252">此選項可保護 global. json。</span><span class="sxs-lookup"><span data-stu-id="3d380-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="3d380-253">移除標示為預覽的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="3d380-254">移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。</span><span class="sxs-lookup"><span data-stu-id="3d380-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="3d380-255">只移除 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="3d380-256">只會移除 .NET Core 執行時間和裝載套件組合。</span><span class="sxs-lookup"><span data-stu-id="3d380-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="3d380-257">移除符合指定之 `major.minor` 版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="3d380-258">只會移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="3d380-259">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="3d380-260">設定詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3d380-260">Sets the verbosity level.</span></span> <span data-ttu-id="3d380-261">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3d380-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3d380-262">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="3d380-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="3d380-263">必須搭配 `--sdk`、`--runtime`和 `--aspnet-runtime` 使用，才能移除 x64 Sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="3d380-264">必須搭配 `--sdk`、`--runtime`和 `--aspnet-runtime` 使用，才能移除 x86 Sdk 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="3d380-265">**`-y, --yes`** 執行命令，而不需要有 [是] 或 [否] 確認。</span><span class="sxs-lookup"><span data-stu-id="3d380-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="3d380-266">**`--force`** 強制移除 Visual Studio 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="3d380-267">附註：</span><span class="sxs-lookup"><span data-stu-id="3d380-267">Notes:</span></span>

1. <span data-ttu-id="3d380-268">只需要其中一個 `--sdk`、`--runtime`、`--aspnet-runtime`和 `--hosting-bundle`。</span><span class="sxs-lookup"><span data-stu-id="3d380-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="3d380-269">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor`和 `[<VERSION>...]` 都是獨佔的。</span><span class="sxs-lookup"><span data-stu-id="3d380-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="3d380-270">如果未指定 `--x64` 或 `--x86`，則會移除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="3d380-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="3d380-271">macOS</span><span class="sxs-lookup"><span data-stu-id="3d380-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="3d380-272">移除所有 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="3d380-273">移除指定版本底下的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="3d380-274">指定的版本將會保留。</span><span class="sxs-lookup"><span data-stu-id="3d380-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="3d380-275">除了指定的版本之外，移除 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="3d380-276">移除 .NET Core Sdk 和執行時間，但不含最高版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="3d380-277">移除由較高修補程式取代的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="3d380-278">此選項可保護 global. json。</span><span class="sxs-lookup"><span data-stu-id="3d380-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="3d380-279">移除標示為預覽的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="3d380-280">移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。</span><span class="sxs-lookup"><span data-stu-id="3d380-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="3d380-281">移除符合指定之 `major.minor` 版本的 .NET Core Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="3d380-282">只會移除 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="3d380-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="3d380-283">僅移除 .NET Core Sdk。</span><span class="sxs-lookup"><span data-stu-id="3d380-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="3d380-284">設定詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3d380-284">Sets the verbosity level.</span></span> <span data-ttu-id="3d380-285">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3d380-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3d380-286">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="3d380-286">The default value is `normal`.</span></span>

* <span data-ttu-id="3d380-287">**`-y, --yes`** 執行命令，而不需要 Y/N 確認。</span><span class="sxs-lookup"><span data-stu-id="3d380-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="3d380-288">**`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。</span><span class="sxs-lookup"><span data-stu-id="3d380-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="3d380-289">附註：</span><span class="sxs-lookup"><span data-stu-id="3d380-289">Notes:</span></span>

1. <span data-ttu-id="3d380-290">只需要其中一個 `--sdk` 和 `--runtime`。</span><span class="sxs-lookup"><span data-stu-id="3d380-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="3d380-291">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor`和 `[<VERSION>...]` 都是獨佔的。</span><span class="sxs-lookup"><span data-stu-id="3d380-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="3d380-292">範例</span><span class="sxs-lookup"><span data-stu-id="3d380-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="3d380-293">根據預設，Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間會保留下來。</span><span class="sxs-lookup"><span data-stu-id="3d380-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="3d380-294">在下列範例中，某些指定的 Sdk 和執行時間可能會保留，視電腦的狀態而定。</span><span class="sxs-lookup"><span data-stu-id="3d380-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="3d380-295">若要移除所有 Sdk 和執行時間，請將它們明確地列為引數，或使用 [`--force`] 選項。</span><span class="sxs-lookup"><span data-stu-id="3d380-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="3d380-296">移除 `3.0.0-preview6-27804-01` 版本以外的所有 .NET Core 執行時間，而不需要進行 Y/N 確認：</span><span class="sxs-lookup"><span data-stu-id="3d380-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="3d380-297">移除所有 .NET Core 1.1 Sdk，而不需要進行 Y/n 確認：</span><span class="sxs-lookup"><span data-stu-id="3d380-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="3d380-298">移除沒有主控台輸出的 .NET Core 1.1.11 SDK：</span><span class="sxs-lookup"><span data-stu-id="3d380-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="3d380-299">移除此工具可安全移除的所有 .NET Core Sdk：</span><span class="sxs-lookup"><span data-stu-id="3d380-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="3d380-300">移除此工具可移除的所有 .NET Core Sdk，包括 Visual Studio 可能需要的 Sdk （不建議）：</span><span class="sxs-lookup"><span data-stu-id="3d380-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="3d380-301">移除回應檔中指定的所有 .NET Core Sdk `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="3d380-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="3d380-302">*版本 .rsp*的內容如下所示：</span><span class="sxs-lookup"><span data-stu-id="3d380-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="3d380-303">步驟 4-刪除 NuGet fallback 資料夾（選擇性）</span><span class="sxs-lookup"><span data-stu-id="3d380-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="3d380-304">在某些情況下，您不再需要 `NuGetFallbackFolder`，而且可能會想要將它刪除。</span><span class="sxs-lookup"><span data-stu-id="3d380-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="3d380-305">如需刪除此資料夾的詳細資訊，請參閱[移除 NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。</span><span class="sxs-lookup"><span data-stu-id="3d380-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="3d380-306">卸載工具</span><span class="sxs-lookup"><span data-stu-id="3d380-306">Uninstall the tool</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="3d380-307">Windows</span><span class="sxs-lookup"><span data-stu-id="3d380-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="3d380-308">開啟 [新增或移除程式]。</span><span class="sxs-lookup"><span data-stu-id="3d380-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="3d380-309">搜尋 `Microsoft .NET Core SDK Uninstall Tool`。</span><span class="sxs-lookup"><span data-stu-id="3d380-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="3d380-310">選取 [解除安裝]。</span><span class="sxs-lookup"><span data-stu-id="3d380-310">Select **Uninstall**.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="3d380-311">macOS</span><span class="sxs-lookup"><span data-stu-id="3d380-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="3d380-312">從安裝的目錄中刪除已下載的*dotnet-core-uninstall gz*檔案。</span><span class="sxs-lookup"><span data-stu-id="3d380-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="3d380-313">如果您將此檔案的內容解壓縮至另一個目錄，請務必一併刪除該內容。</span><span class="sxs-lookup"><span data-stu-id="3d380-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
