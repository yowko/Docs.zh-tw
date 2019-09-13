---
title: dotnet 命令
description: 了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。
ms.date: 06/04/2018
ms.openlocfilehash: 8de6a6f7e584dc472dc23d60f113b03610abb3ef
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926231"
---
# <a name="dotnet-command"></a><span data-ttu-id="79902-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="79902-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="79902-104">名稱</span><span class="sxs-lookup"><span data-stu-id="79902-104">Name</span></span>

<span data-ttu-id="79902-105">`dotnet` - 管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="79902-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="79902-106">概要</span><span class="sxs-lookup"><span data-stu-id="79902-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="79902-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="79902-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="79902-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="79902-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="79902-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="79902-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="79902-110">描述</span><span class="sxs-lookup"><span data-stu-id="79902-110">Description</span></span>

<span data-ttu-id="79902-111">`dotnet` 是管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="79902-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="79902-112">會公開執行特定工作的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="79902-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="79902-113">每個命令會定義自己的引數。</span><span class="sxs-lookup"><span data-stu-id="79902-113">Each command defines its own arguments.</span></span> <span data-ttu-id="79902-114">每個命令後方鍵入 `--help` 以存取簡短說明文件。</span><span class="sxs-lookup"><span data-stu-id="79902-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="79902-115">可藉由指定應用程式 DLL (例如 `dotnet myapp.dll`)，使用 `dotnet` 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="79902-116">請參閱 [.NET Core 應用程式部署](../deploying/index.md) 來了解部署選項。</span><span class="sxs-lookup"><span data-stu-id="79902-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="79902-117">選項</span><span class="sxs-lookup"><span data-stu-id="79902-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="79902-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="79902-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="79902-119">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="79902-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="79902-121">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="79902-122">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="79902-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="79902-123">如需此檔案的詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="79902-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="79902-124">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="79902-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="79902-125">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="79902-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="79902-126">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="79902-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="79902-127">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="79902-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="79902-128">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="79902-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="79902-129">顯示已安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="79902-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="79902-130">顯示已安裝的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="79902-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="79902-131">在必要的共用架構無法使用時定義行為。</span><span class="sxs-lookup"><span data-stu-id="79902-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="79902-132">`N` 可以是：</span><span class="sxs-lookup"><span data-stu-id="79902-132">`N` can be:</span></span>

- <span data-ttu-id="79902-133">`0` - 對次要版本也停用向前復原。</span><span class="sxs-lookup"><span data-stu-id="79902-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="79902-134">`1` - 對次要版本向前復原，主要版本則不。</span><span class="sxs-lookup"><span data-stu-id="79902-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="79902-135">這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="79902-135">This is the default behavior.</span></span>
- <span data-ttu-id="79902-136">`2` - 對次要及主要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="79902-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="79902-137">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="79902-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="79902-138">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="79902-139">*runtimeconfig.json* 檔案是包含執行階段組態設定的組態檔。</span><span class="sxs-lookup"><span data-stu-id="79902-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="79902-140">如需詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="79902-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="79902-141">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="79902-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="79902-142">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="79902-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="79902-143">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="79902-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="79902-144">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="79902-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="79902-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="79902-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="79902-146">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="79902-147">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="79902-148">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="79902-149">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="79902-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="79902-150">如需此檔案的詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="79902-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="79902-151">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="79902-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="79902-152">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="79902-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="79902-153">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="79902-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="79902-154">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="79902-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="79902-155">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="79902-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="79902-156">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="79902-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="79902-157">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="79902-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="79902-158">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="79902-159">*runtimeconfig.json* 檔案是包含執行階段組態設定的組態檔。</span><span class="sxs-lookup"><span data-stu-id="79902-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="79902-160">如需詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="79902-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="79902-161">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="79902-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="79902-162">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="79902-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="79902-163">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="79902-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="79902-164">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="79902-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="79902-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="79902-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="79902-166">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="79902-167">*deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="79902-168">*deps.json* 檔案包含相依性、編譯相依性及用來解決組件衝突的版本資訊清單。</span><span class="sxs-lookup"><span data-stu-id="79902-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="79902-169">如需此檔案的詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="79902-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="79902-170">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="79902-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="79902-171">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="79902-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="79902-172">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="79902-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="79902-173">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="79902-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="79902-174">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="79902-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="79902-175">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="79902-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="79902-176">*runtimeconfig.json* 檔案是包含執行階段組態設定的組態檔。</span><span class="sxs-lookup"><span data-stu-id="79902-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="79902-177">如需詳細資料，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="79902-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="79902-178">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="79902-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="79902-179">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="79902-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="79902-180">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="79902-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="79902-181">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="79902-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="79902-182">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="79902-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="79902-183">一般</span><span class="sxs-lookup"><span data-stu-id="79902-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="79902-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="79902-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="79902-185">命令</span><span class="sxs-lookup"><span data-stu-id="79902-185">Command</span></span>                                       | <span data-ttu-id="79902-186">函數</span><span class="sxs-lookup"><span data-stu-id="79902-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="79902-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="79902-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="79902-188">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="79902-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="79902-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="79902-190">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="79902-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="79902-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="79902-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="79902-192">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="79902-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="79902-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="79902-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="79902-194">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="79902-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="79902-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="79902-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="79902-196">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="79902-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="79902-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="79902-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="79902-198">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="79902-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="79902-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="79902-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="79902-200">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="79902-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="79902-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="79902-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="79902-202">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="79902-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="79902-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="79902-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="79902-204">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="79902-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="79902-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="79902-206">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="79902-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="79902-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="79902-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="79902-208">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="79902-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="79902-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="79902-210">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="79902-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="79902-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="79902-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="79902-212">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="79902-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="79902-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="79902-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="79902-214">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="79902-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="79902-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="79902-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="79902-216">命令</span><span class="sxs-lookup"><span data-stu-id="79902-216">Command</span></span>                             | <span data-ttu-id="79902-217">函數</span><span class="sxs-lookup"><span data-stu-id="79902-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="79902-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="79902-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="79902-219">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="79902-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="79902-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="79902-221">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="79902-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="79902-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="79902-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="79902-223">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="79902-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="79902-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="79902-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="79902-225">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="79902-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="79902-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="79902-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="79902-227">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="79902-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="79902-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="79902-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="79902-229">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="79902-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="79902-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="79902-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="79902-231">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="79902-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="79902-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="79902-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="79902-233">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="79902-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="79902-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="79902-235">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="79902-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="79902-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="79902-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="79902-237">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="79902-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="79902-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="79902-239">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="79902-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="79902-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="79902-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="79902-241">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="79902-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="79902-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="79902-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="79902-243">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="79902-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="79902-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="79902-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="79902-245">命令</span><span class="sxs-lookup"><span data-stu-id="79902-245">Command</span></span>                             | <span data-ttu-id="79902-246">函數</span><span class="sxs-lookup"><span data-stu-id="79902-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="79902-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="79902-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="79902-248">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="79902-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="79902-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="79902-250">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="79902-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="79902-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="79902-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="79902-252">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="79902-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="79902-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="79902-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="79902-254">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="79902-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="79902-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="79902-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="79902-256">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="79902-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="79902-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="79902-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="79902-258">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="79902-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="79902-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="79902-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="79902-260">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="79902-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="79902-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="79902-262">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="79902-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="79902-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="79902-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="79902-264">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="79902-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="79902-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="79902-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="79902-266">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="79902-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="79902-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="79902-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="79902-268">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="79902-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="79902-269">專案參考</span><span class="sxs-lookup"><span data-stu-id="79902-269">Project references</span></span>

<span data-ttu-id="79902-270">命令</span><span class="sxs-lookup"><span data-stu-id="79902-270">Command</span></span> | <span data-ttu-id="79902-271">函數</span><span class="sxs-lookup"><span data-stu-id="79902-271">Function</span></span>
--- | ---
[<span data-ttu-id="79902-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="79902-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="79902-273">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="79902-273">Adds a project reference.</span></span>
[<span data-ttu-id="79902-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="79902-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="79902-275">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="79902-275">Lists project references.</span></span>
[<span data-ttu-id="79902-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="79902-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="79902-277">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="79902-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="79902-278">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="79902-278">NuGet packages</span></span>

<span data-ttu-id="79902-279">命令</span><span class="sxs-lookup"><span data-stu-id="79902-279">Command</span></span> | <span data-ttu-id="79902-280">函數</span><span class="sxs-lookup"><span data-stu-id="79902-280">Function</span></span>
--- | ---
[<span data-ttu-id="79902-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="79902-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="79902-282">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="79902-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="79902-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="79902-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="79902-284">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="79902-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="79902-285">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="79902-285">NuGet commands</span></span>

<span data-ttu-id="79902-286">命令</span><span class="sxs-lookup"><span data-stu-id="79902-286">Command</span></span> | <span data-ttu-id="79902-287">函數</span><span class="sxs-lookup"><span data-stu-id="79902-287">Function</span></span>
--- | ---
[<span data-ttu-id="79902-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="79902-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="79902-289">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="79902-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="79902-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="79902-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="79902-291">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="79902-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="79902-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="79902-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="79902-293">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="79902-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="79902-294">通用工具命令</span><span class="sxs-lookup"><span data-stu-id="79902-294">Global Tools commands</span></span>

<span data-ttu-id="79902-295">[.NET Core 通用工具](global-tools.md)將從 .NET Core SDK 2.1.300 開始提供使用：</span><span class="sxs-lookup"><span data-stu-id="79902-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="79902-296">命令</span><span class="sxs-lookup"><span data-stu-id="79902-296">Command</span></span> | <span data-ttu-id="79902-297">函數</span><span class="sxs-lookup"><span data-stu-id="79902-297">Function</span></span>
--- | ---
[<span data-ttu-id="79902-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="79902-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="79902-299">在您的電腦上安裝通用工具。</span><span class="sxs-lookup"><span data-stu-id="79902-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="79902-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="79902-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="79902-301">列出在您電腦上的預設目錄或在指定路徑中目前已安裝的所有通用工具。</span><span class="sxs-lookup"><span data-stu-id="79902-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="79902-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="79902-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="79902-303">將通用工具從您的電腦解除安裝。</span><span class="sxs-lookup"><span data-stu-id="79902-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="79902-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="79902-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="79902-305">更新您電腦上的通用工具。</span><span class="sxs-lookup"><span data-stu-id="79902-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="79902-306">其他工具</span><span class="sxs-lookup"><span data-stu-id="79902-306">Additional tools</span></span>

<span data-ttu-id="79902-307">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="79902-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="79902-308">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="79902-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="79902-309">工具</span><span class="sxs-lookup"><span data-stu-id="79902-309">Tool</span></span>                                              | <span data-ttu-id="79902-310">函數</span><span class="sxs-lookup"><span data-stu-id="79902-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="79902-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="79902-311">dev-certs</span></span>                                         | <span data-ttu-id="79902-312">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="79902-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="79902-313">ef</span><span class="sxs-lookup"><span data-stu-id="79902-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="79902-314">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="79902-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="79902-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="79902-315">sql-cache</span></span>                                         | <span data-ttu-id="79902-316">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="79902-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="79902-317">user-secrets</span><span class="sxs-lookup"><span data-stu-id="79902-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="79902-318">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="79902-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="79902-319">watch</span><span class="sxs-lookup"><span data-stu-id="79902-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="79902-320">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="79902-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="79902-321">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="79902-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="79902-322">範例</span><span class="sxs-lookup"><span data-stu-id="79902-322">Examples</span></span>

<span data-ttu-id="79902-323">建立新的 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="79902-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="79902-324">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="79902-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="79902-325">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="79902-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="79902-326">執行應用程式 DLL，例如 `myapp.dll`：</span><span class="sxs-lookup"><span data-stu-id="79902-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="79902-327">環境變數</span><span class="sxs-lookup"><span data-stu-id="79902-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="79902-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="79902-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="79902-329">全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="79902-329">The global packages folder.</span></span> <span data-ttu-id="79902-330">如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="79902-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="79902-331">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="79902-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="79902-332">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="79902-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="79902-333">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="79902-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="79902-334">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="79902-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="79902-335">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="79902-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="79902-336">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="79902-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="79902-337">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="79902-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="79902-338">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="79902-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="79902-339">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="79902-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="79902-340">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="79902-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="79902-341">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="79902-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="79902-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="79902-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="79902-343">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="79902-343">The primary package cache.</span></span> <span data-ttu-id="79902-344">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="79902-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="79902-345">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="79902-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="79902-346">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="79902-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="79902-347">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="79902-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="79902-348">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="79902-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="79902-349">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="79902-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="79902-350">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="79902-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="79902-351">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="79902-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="79902-352">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="79902-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="79902-353">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="79902-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="79902-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="79902-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="79902-355">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="79902-355">The primary package cache.</span></span> <span data-ttu-id="79902-356">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="79902-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="79902-357">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="79902-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="79902-358">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="79902-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="79902-359">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="79902-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="79902-360">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="79902-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="79902-361">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="79902-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="79902-362">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79902-362">See also</span></span>

- <span data-ttu-id="79902-363">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)</span><span class="sxs-lookup"><span data-stu-id="79902-363">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)</span></span>
