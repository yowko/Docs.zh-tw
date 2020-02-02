---
title: dotnet 命令
description: 瞭解 dotnet 命令（.NET Core CLI 的一般驅動程式）及其使用方式。
ms.date: 06/04/2018
ms.openlocfilehash: 7674529980623caa2291987bdeba52f50ce2fc2c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920541"
---
# <a name="dotnet-command"></a><span data-ttu-id="e6398-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="e6398-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e6398-104">Name</span><span class="sxs-lookup"><span data-stu-id="e6398-104">Name</span></span>

<span data-ttu-id="e6398-105">`dotnet` - 管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e6398-106">概要</span><span class="sxs-lookup"><span data-stu-id="e6398-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e6398-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6398-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e6398-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e6398-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e6398-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e6398-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="e6398-110">描述</span><span class="sxs-lookup"><span data-stu-id="e6398-110">Description</span></span>

<span data-ttu-id="e6398-111">`dotnet` 是管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="e6398-112">會公開執行特定工作的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="e6398-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="e6398-113">每個命令會定義自己的引數。</span><span class="sxs-lookup"><span data-stu-id="e6398-113">Each command defines its own arguments.</span></span> <span data-ttu-id="e6398-114">每個命令後方鍵入 `--help` 以存取簡短說明文件。</span><span class="sxs-lookup"><span data-stu-id="e6398-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="e6398-115">可藉由指定應用程式 DLL (例如 `dotnet myapp.dll`)，使用 `dotnet` 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="e6398-116">請參閱 [.NET Core 應用程式部署](../deploying/index.md) 來了解部署選項。</span><span class="sxs-lookup"><span data-stu-id="e6398-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="e6398-117">選項</span><span class="sxs-lookup"><span data-stu-id="e6398-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e6398-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6398-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="e6398-119">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="e6398-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="e6398-121">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="e6398-122">*.Deps.json json*檔案包含相依性、編譯相依性和用來解決元件衝突的版本資訊的清單。</span><span class="sxs-lookup"><span data-stu-id="e6398-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="e6398-123">如需此檔案的詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="e6398-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="e6398-124">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="e6398-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="e6398-125">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="e6398-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="e6398-126">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="e6398-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="e6398-127">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="e6398-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="e6398-128">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="e6398-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="e6398-129">顯示已安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="e6398-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="e6398-130">顯示已安裝的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="e6398-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="e6398-131">在必要的共用架構無法使用時定義行為。</span><span class="sxs-lookup"><span data-stu-id="e6398-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="e6398-132">`N` 可以是：</span><span class="sxs-lookup"><span data-stu-id="e6398-132">`N` can be:</span></span>

- <span data-ttu-id="e6398-133">`0` - 對次要版本也停用向前復原。</span><span class="sxs-lookup"><span data-stu-id="e6398-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="e6398-134">`1` - 對次要版本向前復原，主要版本則不。</span><span class="sxs-lookup"><span data-stu-id="e6398-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="e6398-135">這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="e6398-135">This is the default behavior.</span></span>
- <span data-ttu-id="e6398-136">`2` - 對次要及主要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="e6398-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="e6398-137">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="e6398-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="e6398-138">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="e6398-139">*.Runtimeconfig.json json*檔案是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6398-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="e6398-140">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="e6398-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e6398-141">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e6398-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e6398-142">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e6398-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e6398-143">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="e6398-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="e6398-144">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="e6398-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e6398-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e6398-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="e6398-146">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="e6398-147">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="e6398-148">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="e6398-149">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="e6398-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="e6398-150">如需此檔案的詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="e6398-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="e6398-151">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="e6398-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="e6398-152">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="e6398-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="e6398-153">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="e6398-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="e6398-154">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="e6398-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="e6398-155">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="e6398-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="e6398-156">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="e6398-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="e6398-157">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="e6398-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="e6398-158">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="e6398-159">*.Runtimeconfig.json json*檔案是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6398-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="e6398-160">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="e6398-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e6398-161">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e6398-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e6398-162">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e6398-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e6398-163">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="e6398-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="e6398-164">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="e6398-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e6398-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e6398-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="e6398-166">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="e6398-167">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="e6398-168">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="e6398-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="e6398-169">如需此檔案的詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="e6398-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="e6398-170">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="e6398-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="e6398-171">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="e6398-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="e6398-172">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="e6398-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="e6398-173">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="e6398-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="e6398-174">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="e6398-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="e6398-175">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6398-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="e6398-176">*.Runtimeconfig.json json*檔案是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6398-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="e6398-177">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="e6398-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e6398-178">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e6398-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e6398-179">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e6398-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e6398-180">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="e6398-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="e6398-181">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="e6398-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="e6398-182">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="e6398-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="e6398-183">一般</span><span class="sxs-lookup"><span data-stu-id="e6398-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e6398-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6398-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="e6398-185">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-185">Command</span></span>                                       | <span data-ttu-id="e6398-186">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="e6398-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e6398-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="e6398-188">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="e6398-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="e6398-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="e6398-190">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="e6398-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="e6398-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="e6398-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="e6398-192">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="e6398-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="e6398-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="e6398-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="e6398-194">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="e6398-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="e6398-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="e6398-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="e6398-196">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="e6398-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="e6398-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="e6398-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="e6398-198">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="e6398-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="e6398-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e6398-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="e6398-200">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="e6398-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="e6398-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="e6398-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="e6398-202">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e6398-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="e6398-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="e6398-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="e6398-204">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="e6398-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="e6398-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="e6398-206">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="e6398-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="e6398-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="e6398-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="e6398-208">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="e6398-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="e6398-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="e6398-210">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="e6398-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="e6398-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="e6398-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="e6398-212">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="e6398-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="e6398-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e6398-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="e6398-214">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="e6398-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e6398-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e6398-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="e6398-216">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-216">Command</span></span>                             | <span data-ttu-id="e6398-217">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="e6398-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e6398-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="e6398-219">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="e6398-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="e6398-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="e6398-221">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="e6398-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="e6398-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="e6398-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="e6398-223">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="e6398-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="e6398-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="e6398-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="e6398-225">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="e6398-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="e6398-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="e6398-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="e6398-227">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="e6398-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="e6398-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e6398-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="e6398-229">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="e6398-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="e6398-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="e6398-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="e6398-231">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e6398-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="e6398-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="e6398-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="e6398-233">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="e6398-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="e6398-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="e6398-235">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="e6398-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="e6398-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="e6398-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="e6398-237">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="e6398-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="e6398-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="e6398-239">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="e6398-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="e6398-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="e6398-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="e6398-241">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="e6398-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="e6398-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e6398-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="e6398-243">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="e6398-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e6398-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e6398-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="e6398-245">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-245">Command</span></span>                             | <span data-ttu-id="e6398-246">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="e6398-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e6398-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="e6398-248">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="e6398-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="e6398-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="e6398-250">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="e6398-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="e6398-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="e6398-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="e6398-252">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="e6398-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="e6398-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="e6398-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="e6398-254">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="e6398-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="e6398-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e6398-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="e6398-256">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="e6398-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="e6398-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="e6398-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="e6398-258">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e6398-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="e6398-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="e6398-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="e6398-260">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="e6398-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="e6398-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="e6398-262">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="e6398-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="e6398-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="e6398-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="e6398-264">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6398-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="e6398-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="e6398-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="e6398-266">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="e6398-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="e6398-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e6398-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="e6398-268">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="e6398-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="e6398-269">專案參考</span><span class="sxs-lookup"><span data-stu-id="e6398-269">Project references</span></span>

<span data-ttu-id="e6398-270">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-270">Command</span></span> | <span data-ttu-id="e6398-271">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-271">Function</span></span>
--- | ---
[<span data-ttu-id="e6398-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="e6398-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="e6398-273">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="e6398-273">Adds a project reference.</span></span>
[<span data-ttu-id="e6398-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="e6398-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="e6398-275">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="e6398-275">Lists project references.</span></span>
[<span data-ttu-id="e6398-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="e6398-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="e6398-277">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="e6398-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="e6398-278">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="e6398-278">NuGet packages</span></span>

<span data-ttu-id="e6398-279">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-279">Command</span></span> | <span data-ttu-id="e6398-280">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-280">Function</span></span>
--- | ---
[<span data-ttu-id="e6398-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="e6398-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="e6398-282">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e6398-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="e6398-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="e6398-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="e6398-284">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e6398-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="e6398-285">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="e6398-285">NuGet commands</span></span>

<span data-ttu-id="e6398-286">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-286">Command</span></span> | <span data-ttu-id="e6398-287">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-287">Function</span></span>
--- | ---
[<span data-ttu-id="e6398-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="e6398-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="e6398-289">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="e6398-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="e6398-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="e6398-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="e6398-291">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6398-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="e6398-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="e6398-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="e6398-293">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="e6398-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="e6398-294">通用工具命令</span><span class="sxs-lookup"><span data-stu-id="e6398-294">Global Tools commands</span></span>

<span data-ttu-id="e6398-295">[.NET Core 通用工具](global-tools.md)將從 .NET Core SDK 2.1.300 開始提供使用：</span><span class="sxs-lookup"><span data-stu-id="e6398-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="e6398-296">命令</span><span class="sxs-lookup"><span data-stu-id="e6398-296">Command</span></span> | <span data-ttu-id="e6398-297">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-297">Function</span></span>
--- | ---
[<span data-ttu-id="e6398-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="e6398-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="e6398-299">在您的電腦上安裝通用工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="e6398-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="e6398-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="e6398-301">列出在您電腦上的預設目錄或在指定路徑中目前已安裝的所有通用工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="e6398-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="e6398-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="e6398-303">將通用工具從您的電腦解除安裝。</span><span class="sxs-lookup"><span data-stu-id="e6398-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="e6398-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="e6398-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="e6398-305">更新您電腦上的通用工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="e6398-306">其他工具</span><span class="sxs-lookup"><span data-stu-id="e6398-306">Additional tools</span></span>

<span data-ttu-id="e6398-307">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="e6398-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="e6398-308">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="e6398-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="e6398-309">工具</span><span class="sxs-lookup"><span data-stu-id="e6398-309">Tool</span></span>                                              | <span data-ttu-id="e6398-310">函數</span><span class="sxs-lookup"><span data-stu-id="e6398-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="e6398-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="e6398-311">dev-certs</span></span>                                         | <span data-ttu-id="e6398-312">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="e6398-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="e6398-313">ef</span><span class="sxs-lookup"><span data-stu-id="e6398-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="e6398-314">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="e6398-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="e6398-315">sql-cache</span></span>                                         | <span data-ttu-id="e6398-316">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="e6398-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="e6398-317">user-secrets</span><span class="sxs-lookup"><span data-stu-id="e6398-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="e6398-318">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="e6398-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="e6398-319">watch</span><span class="sxs-lookup"><span data-stu-id="e6398-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="e6398-320">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="e6398-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="e6398-321">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="e6398-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="e6398-322">範例</span><span class="sxs-lookup"><span data-stu-id="e6398-322">Examples</span></span>

<span data-ttu-id="e6398-323">建立新的 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="e6398-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="e6398-324">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="e6398-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="e6398-325">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="e6398-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="e6398-326">執行應用程式 DLL，例如 `myapp.dll`：</span><span class="sxs-lookup"><span data-stu-id="e6398-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="e6398-327">環境變數</span><span class="sxs-lookup"><span data-stu-id="e6398-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e6398-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6398-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="e6398-329">全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6398-329">The global packages folder.</span></span> <span data-ttu-id="e6398-330">如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="e6398-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="e6398-331">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="e6398-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="e6398-332">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="e6398-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="e6398-333">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="e6398-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="e6398-334">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="e6398-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="e6398-335">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="e6398-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="e6398-336">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="e6398-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="e6398-337">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6398-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="e6398-338">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="e6398-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="e6398-339">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="e6398-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="e6398-340">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="e6398-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="e6398-341">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="e6398-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e6398-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e6398-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="e6398-343">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="e6398-343">The primary package cache.</span></span> <span data-ttu-id="e6398-344">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="e6398-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="e6398-345">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="e6398-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="e6398-346">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="e6398-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="e6398-347">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="e6398-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="e6398-348">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="e6398-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="e6398-349">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="e6398-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="e6398-350">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="e6398-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="e6398-351">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6398-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="e6398-352">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="e6398-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="e6398-353">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="e6398-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e6398-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e6398-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="e6398-355">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="e6398-355">The primary package cache.</span></span> <span data-ttu-id="e6398-356">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="e6398-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="e6398-357">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="e6398-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="e6398-358">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="e6398-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="e6398-359">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="e6398-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="e6398-360">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="e6398-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="e6398-361">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="e6398-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="e6398-362">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6398-362">See also</span></span>

- <span data-ttu-id="e6398-363">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)</span><span class="sxs-lookup"><span data-stu-id="e6398-363">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)</span></span>
- [<span data-ttu-id="e6398-364">.NET Core 執行時間設定</span><span class="sxs-lookup"><span data-stu-id="e6398-364">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
