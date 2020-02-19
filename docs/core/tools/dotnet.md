---
title: dotnet 命令
description: 瞭解 dotnet 命令（.NET Core CLI 的一般驅動程式）及其使用方式。
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451164"
---
# <a name="dotnet-command"></a><span data-ttu-id="a3f88-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="a3f88-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a3f88-104">名稱</span><span class="sxs-lookup"><span data-stu-id="a3f88-104">Name</span></span>

<span data-ttu-id="a3f88-105">`dotnet` - 管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a3f88-106">概要</span><span class="sxs-lookup"><span data-stu-id="a3f88-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="a3f88-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a3f88-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[<span data-ttu-id="a3f88-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a3f88-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="a3f88-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a3f88-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="a3f88-110">描述</span><span class="sxs-lookup"><span data-stu-id="a3f88-110">Description</span></span>

<span data-ttu-id="a3f88-111">`dotnet` 是管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="a3f88-112">會公開執行特定工作的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="a3f88-113">每個命令會定義自己的引數。</span><span class="sxs-lookup"><span data-stu-id="a3f88-113">Each command defines its own arguments.</span></span> <span data-ttu-id="a3f88-114">每個命令後方鍵入 `--help` 以存取簡短說明文件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="a3f88-115">可藉由指定應用程式 DLL (例如 `dotnet`)，使用 `dotnet myapp.dll` 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="a3f88-116">請參閱 [.NET Core 應用程式部署](../deploying/index.md) 來了解部署選項。</span><span class="sxs-lookup"><span data-stu-id="a3f88-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="a3f88-117">選項。</span><span class="sxs-lookup"><span data-stu-id="a3f88-117">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a3f88-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a3f88-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="a3f88-119">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a3f88-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="a3f88-121">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="a3f88-122">*.Deps.json json*檔案包含相依性、編譯相依性和用來解決元件衝突的版本資訊的清單。</span><span class="sxs-lookup"><span data-stu-id="a3f88-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a3f88-123">如需此檔案的詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a3f88-124">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a3f88-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a3f88-125">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3f88-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a3f88-126">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a3f88-127">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a3f88-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a3f88-128">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a3f88-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="a3f88-129">顯示已安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="a3f88-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="a3f88-130">顯示已安裝的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a3f88-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="a3f88-131">在必要的共用架構無法使用時定義行為。</span><span class="sxs-lookup"><span data-stu-id="a3f88-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="a3f88-132">`N` 可以是：</span><span class="sxs-lookup"><span data-stu-id="a3f88-132">`N` can be:</span></span>

- <span data-ttu-id="a3f88-133">`0` - 對次要版本也停用向前復原。</span><span class="sxs-lookup"><span data-stu-id="a3f88-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="a3f88-134">`1` - 對次要版本向前復原，主要版本則不。</span><span class="sxs-lookup"><span data-stu-id="a3f88-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="a3f88-135">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="a3f88-135">This is the default behavior.</span></span>
- <span data-ttu-id="a3f88-136">`2` - 對次要及主要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a3f88-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="a3f88-137">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="a3f88-138">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="a3f88-139">*.Runtimeconfig.json json*檔案是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="a3f88-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="a3f88-140">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a3f88-141">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a3f88-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a3f88-142">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a3f88-143">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a3f88-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a3f88-144">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a3f88-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="a3f88-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a3f88-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="a3f88-146">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a3f88-147">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="a3f88-148">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="a3f88-149">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a3f88-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a3f88-150">如需此檔案的詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="a3f88-151">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a3f88-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a3f88-152">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3f88-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a3f88-153">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a3f88-154">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a3f88-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a3f88-155">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a3f88-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="a3f88-156">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a3f88-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a3f88-157">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="a3f88-158">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="a3f88-159">*.Runtimeconfig.json json*檔案是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="a3f88-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="a3f88-160">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a3f88-161">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a3f88-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a3f88-162">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a3f88-163">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a3f88-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a3f88-164">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a3f88-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="a3f88-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a3f88-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="a3f88-166">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="a3f88-167">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="a3f88-168">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a3f88-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a3f88-169">如需此檔案的詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="a3f88-170">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a3f88-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a3f88-171">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3f88-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a3f88-172">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a3f88-173">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a3f88-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a3f88-174">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a3f88-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="a3f88-175">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3f88-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="a3f88-176">*.Runtimeconfig.json json*檔案是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="a3f88-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="a3f88-177">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a3f88-178">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a3f88-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a3f88-179">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a3f88-180">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a3f88-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a3f88-181">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a3f88-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="a3f88-182">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="a3f88-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="a3f88-183">一般</span><span class="sxs-lookup"><span data-stu-id="a3f88-183">General</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a3f88-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a3f88-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="a3f88-185">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-185">Command</span></span>                                       | <span data-ttu-id="a3f88-186">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a3f88-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a3f88-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="a3f88-188">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a3f88-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="a3f88-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="a3f88-190">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="a3f88-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="a3f88-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a3f88-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="a3f88-192">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a3f88-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="a3f88-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a3f88-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="a3f88-194">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a3f88-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a3f88-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="a3f88-196">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a3f88-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a3f88-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a3f88-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="a3f88-198">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a3f88-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a3f88-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a3f88-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="a3f88-200">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a3f88-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a3f88-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a3f88-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="a3f88-202">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a3f88-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a3f88-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="a3f88-204">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a3f88-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a3f88-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="a3f88-206">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a3f88-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a3f88-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a3f88-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="a3f88-208">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a3f88-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a3f88-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="a3f88-210">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a3f88-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a3f88-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a3f88-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="a3f88-212">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a3f88-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a3f88-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="a3f88-214">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a3f88-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20"></a>[<span data-ttu-id="a3f88-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a3f88-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="a3f88-216">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-216">Command</span></span>                             | <span data-ttu-id="a3f88-217">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a3f88-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a3f88-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a3f88-219">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a3f88-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a3f88-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a3f88-221">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a3f88-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a3f88-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a3f88-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="a3f88-223">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a3f88-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a3f88-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a3f88-225">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a3f88-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a3f88-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a3f88-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a3f88-227">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a3f88-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a3f88-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a3f88-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a3f88-229">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a3f88-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a3f88-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a3f88-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a3f88-231">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a3f88-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a3f88-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a3f88-233">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a3f88-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a3f88-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a3f88-235">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a3f88-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a3f88-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a3f88-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a3f88-237">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a3f88-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a3f88-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a3f88-239">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a3f88-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a3f88-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a3f88-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="a3f88-241">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a3f88-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a3f88-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a3f88-243">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a3f88-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1x"></a>[<span data-ttu-id="a3f88-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a3f88-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="a3f88-245">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-245">Command</span></span>                             | <span data-ttu-id="a3f88-246">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a3f88-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a3f88-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a3f88-248">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a3f88-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a3f88-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a3f88-250">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a3f88-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a3f88-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a3f88-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a3f88-252">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a3f88-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a3f88-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a3f88-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a3f88-254">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a3f88-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a3f88-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a3f88-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a3f88-256">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a3f88-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a3f88-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a3f88-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a3f88-258">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a3f88-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a3f88-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a3f88-260">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a3f88-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a3f88-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a3f88-262">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a3f88-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a3f88-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a3f88-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a3f88-264">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a3f88-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a3f88-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a3f88-266">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a3f88-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a3f88-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a3f88-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a3f88-268">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a3f88-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="a3f88-269">專案參考</span><span class="sxs-lookup"><span data-stu-id="a3f88-269">Project references</span></span>

<span data-ttu-id="a3f88-270">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-270">Command</span></span> | <span data-ttu-id="a3f88-271">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-271">Function</span></span>
--- | ---
[<span data-ttu-id="a3f88-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a3f88-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="a3f88-273">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="a3f88-273">Adds a project reference.</span></span>
[<span data-ttu-id="a3f88-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a3f88-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="a3f88-275">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="a3f88-275">Lists project references.</span></span>
[<span data-ttu-id="a3f88-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a3f88-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="a3f88-277">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="a3f88-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="a3f88-278">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="a3f88-278">NuGet packages</span></span>

<span data-ttu-id="a3f88-279">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-279">Command</span></span> | <span data-ttu-id="a3f88-280">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-280">Function</span></span>
--- | ---
[<span data-ttu-id="a3f88-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="a3f88-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="a3f88-282">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="a3f88-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a3f88-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="a3f88-284">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="a3f88-285">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="a3f88-285">NuGet commands</span></span>

<span data-ttu-id="a3f88-286">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-286">Command</span></span> | <span data-ttu-id="a3f88-287">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-287">Function</span></span>
--- | ---
[<span data-ttu-id="a3f88-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="a3f88-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="a3f88-289">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="a3f88-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="a3f88-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="a3f88-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="a3f88-291">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3f88-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="a3f88-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a3f88-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="a3f88-293">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="a3f88-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="a3f88-294">全域、工具路徑和本機工具命令</span><span class="sxs-lookup"><span data-stu-id="a3f88-294">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="a3f88-295">工具是從 NuGet 套件安裝並從命令提示字元叫用的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f88-295">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="a3f88-296">您可以自行撰寫工具，或安裝由協力廠商撰寫的工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-296">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="a3f88-297">工具也稱為「通用工具」、「工具路徑工具」和「本機工具」。</span><span class="sxs-lookup"><span data-stu-id="a3f88-297">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="a3f88-298">如需詳細資訊，請參閱[.Net Core 工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-298">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="a3f88-299">從 .NET Core SDK 2.1 開始提供全域和工具路徑工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-299">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="a3f88-300">從 .NET Core SDK 3.0 開始提供本機工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-300">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="a3f88-301">Command</span><span class="sxs-lookup"><span data-stu-id="a3f88-301">Command</span></span> | <span data-ttu-id="a3f88-302">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-302">Function</span></span>
--- | ---
[<span data-ttu-id="a3f88-303">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a3f88-303">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="a3f88-304">在您的電腦上安裝工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-304">Installs a tool on your machine.</span></span>
[<span data-ttu-id="a3f88-305">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a3f88-305">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a3f88-306">列出目前安裝在您電腦上的所有全域、工具路徑或本機工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-306">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="a3f88-307">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="a3f88-307">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="a3f88-308">從您的電腦卸載工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-308">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="a3f88-309">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="a3f88-309">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="a3f88-310">更新安裝在您電腦上的工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-310">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="a3f88-311">其他工具</span><span class="sxs-lookup"><span data-stu-id="a3f88-311">Additional tools</span></span>

<span data-ttu-id="a3f88-312">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="a3f88-312">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="a3f88-313">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="a3f88-313">These tools are listed in the following table:</span></span>

| <span data-ttu-id="a3f88-314">工具</span><span class="sxs-lookup"><span data-stu-id="a3f88-314">Tool</span></span>                                              | <span data-ttu-id="a3f88-315">函式</span><span class="sxs-lookup"><span data-stu-id="a3f88-315">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="a3f88-316">dev-certs</span><span class="sxs-lookup"><span data-stu-id="a3f88-316">dev-certs</span></span>                                         | <span data-ttu-id="a3f88-317">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="a3f88-317">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="a3f88-318">ef</span><span class="sxs-lookup"><span data-stu-id="a3f88-318">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="a3f88-319">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-319">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="a3f88-320">sql-cache</span><span class="sxs-lookup"><span data-stu-id="a3f88-320">sql-cache</span></span>                                         | <span data-ttu-id="a3f88-321">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a3f88-321">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="a3f88-322">user-secrets</span><span class="sxs-lookup"><span data-stu-id="a3f88-322">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="a3f88-323">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="a3f88-323">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="a3f88-324">watch</span><span class="sxs-lookup"><span data-stu-id="a3f88-324">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="a3f88-325">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="a3f88-325">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="a3f88-326">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-326">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="a3f88-327">範例</span><span class="sxs-lookup"><span data-stu-id="a3f88-327">Examples</span></span>

<span data-ttu-id="a3f88-328">建立新的 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="a3f88-328">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="a3f88-329">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="a3f88-329">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a3f88-330">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="a3f88-330">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="a3f88-331">執行應用程式 DLL，例如 `myapp.dll`：</span><span class="sxs-lookup"><span data-stu-id="a3f88-331">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="a3f88-332">環境變數</span><span class="sxs-lookup"><span data-stu-id="a3f88-332">Environment variables</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a3f88-333">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a3f88-333">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="a3f88-334">全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3f88-334">The global packages folder.</span></span> <span data-ttu-id="a3f88-335">如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-335">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a3f88-336">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a3f88-336">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a3f88-337">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a3f88-337">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a3f88-338">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-338">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a3f88-339">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-339">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a3f88-340">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a3f88-340">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a3f88-341">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="a3f88-341">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a3f88-342">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-342">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a3f88-343">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-343">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a3f88-344">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-344">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="a3f88-345">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a3f88-345">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a3f88-346">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-346">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="a3f88-347">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a3f88-347">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="a3f88-348">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="a3f88-348">The primary package cache.</span></span> <span data-ttu-id="a3f88-349">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-349">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a3f88-350">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a3f88-350">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a3f88-351">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a3f88-351">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a3f88-352">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-352">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a3f88-353">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-353">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a3f88-354">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a3f88-354">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a3f88-355">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="a3f88-355">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a3f88-356">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a3f88-356">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a3f88-357">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-357">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a3f88-358">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-358">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="a3f88-359">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a3f88-359">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="a3f88-360">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="a3f88-360">The primary package cache.</span></span> <span data-ttu-id="a3f88-361">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-361">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a3f88-362">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a3f88-362">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a3f88-363">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a3f88-363">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a3f88-364">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-364">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a3f88-365">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a3f88-365">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a3f88-366">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a3f88-366">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="a3f88-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f88-367">See also</span></span>

- <span data-ttu-id="a3f88-368">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)</span><span class="sxs-lookup"><span data-stu-id="a3f88-368">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)</span></span>
- [<span data-ttu-id="a3f88-369">.NET Core 執行時間設定</span><span class="sxs-lookup"><span data-stu-id="a3f88-369">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
