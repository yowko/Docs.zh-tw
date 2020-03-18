---
title: dotnet 命令
description: 瞭解 dotnet 命令（.NET Core CLI 的通用驅動程式）及其用法。
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398892"
---
# <a name="dotnet-command"></a><span data-ttu-id="6725d-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="6725d-103">dotnet command</span></span>

<span data-ttu-id="6725d-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="6725d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6725d-105">名稱</span><span class="sxs-lookup"><span data-stu-id="6725d-105">Name</span></span>

<span data-ttu-id="6725d-106">`dotnet`- .NET 核心 CLI 的通用驅動程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6725d-107">概要</span><span class="sxs-lookup"><span data-stu-id="6725d-107">Synopsis</span></span>

<span data-ttu-id="6725d-108">要獲取有關可用命令和環境的資訊，請訪問：</span><span class="sxs-lookup"><span data-stu-id="6725d-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="6725d-109">要運行命令（需要 SDK 安裝）：</span><span class="sxs-lookup"><span data-stu-id="6725d-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="6725d-110">要運行應用程式：</span><span class="sxs-lookup"><span data-stu-id="6725d-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="6725d-111">`--roll-forward`可用自 .NET 核心 3.x。</span><span class="sxs-lookup"><span data-stu-id="6725d-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="6725d-112">用於`--roll-forward-on-no-candidate-fx`.NET 核心 2.x。</span><span class="sxs-lookup"><span data-stu-id="6725d-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="6725d-113">描述</span><span class="sxs-lookup"><span data-stu-id="6725d-113">Description</span></span>

<span data-ttu-id="6725d-114">該`dotnet`命令具有兩個函數：</span><span class="sxs-lookup"><span data-stu-id="6725d-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="6725d-115">它提供了用於處理 .NET Core 專案的命令。</span><span class="sxs-lookup"><span data-stu-id="6725d-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="6725d-116">例如，[`dotnet build`](dotnet-build.md)生成專案。</span><span class="sxs-lookup"><span data-stu-id="6725d-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="6725d-117">每個命令定義自己的選項和參數。</span><span class="sxs-lookup"><span data-stu-id="6725d-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="6725d-118">所有命令都支援列印`--help`有關如何使用該命令的簡短文檔的選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="6725d-119">它運行 .NET 核心應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="6725d-120">指定應用程式`.dll`檔的路徑以運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="6725d-121">例如，`dotnet myapp.dll`運行`myapp`應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="6725d-122">請參閱[.NET 核心應用程式部署](../deploying/index.md)以瞭解部署選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="6725d-123">選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-123">Options</span></span>

<span data-ttu-id="6725d-124">不同的選項本身可用於`dotnet`運行命令和運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="6725d-125">點網本身的選項</span><span class="sxs-lookup"><span data-stu-id="6725d-125">Options for dotnet by itself</span></span>

<span data-ttu-id="6725d-126">以下選項`dotnet`本身。</span><span class="sxs-lookup"><span data-stu-id="6725d-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="6725d-127">例如： `dotnet --info` 。</span><span class="sxs-lookup"><span data-stu-id="6725d-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="6725d-128">他們列印出有關環境的資訊。</span><span class="sxs-lookup"><span data-stu-id="6725d-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="6725d-129">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="6725d-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="6725d-130">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="6725d-131">列印已安裝的 .NET 核心運行時的清單。</span><span class="sxs-lookup"><span data-stu-id="6725d-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="6725d-132">列印已安裝的 .NET 核心 SDK 的清單。</span><span class="sxs-lookup"><span data-stu-id="6725d-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6725d-133">列印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="6725d-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="6725d-134">用於運行命令的 SDK 選項</span><span class="sxs-lookup"><span data-stu-id="6725d-134">SDK options for running a command</span></span>

<span data-ttu-id="6725d-135">以下選項適用于`dotnet`命令。</span><span class="sxs-lookup"><span data-stu-id="6725d-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="6725d-136">例如： `dotnet build --help` 。</span><span class="sxs-lookup"><span data-stu-id="6725d-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="6725d-137">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="6725d-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6725d-138">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="6725d-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6725d-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="6725d-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="6725d-140">每個命令都不支援。</span><span class="sxs-lookup"><span data-stu-id="6725d-140">Not supported in every command.</span></span> <span data-ttu-id="6725d-141">請參閱特定命令頁以確定此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="6725d-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6725d-142">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="6725d-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="6725d-143">每個命令定義特定于該命令的選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="6725d-144">有關可用選項的清單，請參閱特定命令頁。</span><span class="sxs-lookup"><span data-stu-id="6725d-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="6725d-145">運行時選項</span><span class="sxs-lookup"><span data-stu-id="6725d-145">Runtime options</span></span>

<span data-ttu-id="6725d-146">運行應用程式時`dotnet`，以下選項可用。</span><span class="sxs-lookup"><span data-stu-id="6725d-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="6725d-147">例如： `dotnet myapp.dll --fx-version 3.1.1` 。</span><span class="sxs-lookup"><span data-stu-id="6725d-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="6725d-148">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6725d-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="6725d-149">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6725d-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="6725d-150">*deps.json*檔包含用於解決程式集衝突的依賴項、編譯依賴項和版本資訊的清單。</span><span class="sxs-lookup"><span data-stu-id="6725d-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="6725d-151">如需詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="6725d-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="6725d-152">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="6725d-153">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6725d-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="6725d-154">*運行時 config.json*檔是包含運行時設置的設定檔。</span><span class="sxs-lookup"><span data-stu-id="6725d-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="6725d-155">有關詳細資訊，請參閱[.NET Core 運行時配置設置](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="6725d-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="6725d-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*在 .NET 核心 2.x SDK 中提供。**</span><span class="sxs-lookup"><span data-stu-id="6725d-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="6725d-157">在必要的共用架構無法使用時定義行為。</span><span class="sxs-lookup"><span data-stu-id="6725d-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="6725d-158">`N` 可以是：</span><span class="sxs-lookup"><span data-stu-id="6725d-158">`N` can be:</span></span>

  - <span data-ttu-id="6725d-159">`0` - 對次要版本也停用向前復原。</span><span class="sxs-lookup"><span data-stu-id="6725d-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="6725d-160">`1` - 對次要版本向前復原，主要版本則不。</span><span class="sxs-lookup"><span data-stu-id="6725d-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="6725d-161">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="6725d-161">This is the default behavior.</span></span>
  - <span data-ttu-id="6725d-162">`2` - 對次要及主要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="6725d-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="6725d-163">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="6725d-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="6725d-164">**`--roll-forward <SETTING>`\*\*\*\*可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="6725d-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="6725d-165">控制如何向前滾動應用於應用。</span><span class="sxs-lookup"><span data-stu-id="6725d-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="6725d-166">`SETTING`可以是以下值之一。</span><span class="sxs-lookup"><span data-stu-id="6725d-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="6725d-167">如果未指定，`Minor`則為預設值。</span><span class="sxs-lookup"><span data-stu-id="6725d-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="6725d-168">`LatestPatch`- 向前滾動到最高補丁版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="6725d-169">這會停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="6725d-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="6725d-170">`Minor`- 如果缺少請求的次要版本，請向前滾動到最低較高的次要版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="6725d-171">如果要求的次要版本存在，則會使用 LatestPatch 原則。</span><span class="sxs-lookup"><span data-stu-id="6725d-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="6725d-172">`Major`- 如果缺少請求的主要版本，則向前滾動到最低較高主版本和最低次要版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="6725d-173">如果要求的主要版本存在，則會使用 Minor 原則。</span><span class="sxs-lookup"><span data-stu-id="6725d-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="6725d-174">`LatestMinor`- 向前滾動到最高次要版本，即使存在請求的次要版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="6725d-175">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="6725d-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="6725d-176">`LatestMajor`- 向前滾動到最高主要和最高的次要版本，即使請求的主要存在。</span><span class="sxs-lookup"><span data-stu-id="6725d-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="6725d-177">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="6725d-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="6725d-178">`Disable`-別向前滾</span><span class="sxs-lookup"><span data-stu-id="6725d-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="6725d-179">只會繫結至指定的版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-179">Only bind to specified version.</span></span> <span data-ttu-id="6725d-180">此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。</span><span class="sxs-lookup"><span data-stu-id="6725d-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="6725d-181">只有測試時才建議使用這個值。</span><span class="sxs-lookup"><span data-stu-id="6725d-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="6725d-182">除 之外`Disable`，所有設置都將使用最高可用的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="6725d-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="6725d-183">前滾行為也可以在專案檔案屬性、運行時配置檔案屬性和環境變數中配置。</span><span class="sxs-lookup"><span data-stu-id="6725d-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="6725d-184">有關詳細資訊，請參閱[主版本運行時向前滾動](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="6725d-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="6725d-185">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="6725d-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="6725d-186">一般</span><span class="sxs-lookup"><span data-stu-id="6725d-186">General</span></span>

| <span data-ttu-id="6725d-187">Command</span><span class="sxs-lookup"><span data-stu-id="6725d-187">Command</span></span>                                       | <span data-ttu-id="6725d-188">函式</span><span class="sxs-lookup"><span data-stu-id="6725d-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="6725d-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="6725d-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="6725d-190">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="6725d-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="6725d-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="6725d-192">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="6725d-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="6725d-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="6725d-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="6725d-194">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="6725d-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="6725d-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="6725d-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="6725d-196">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="6725d-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="6725d-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="6725d-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="6725d-198">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="6725d-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="6725d-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="6725d-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="6725d-200">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="6725d-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="6725d-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6725d-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="6725d-202">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="6725d-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="6725d-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6725d-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="6725d-204">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6725d-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="6725d-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6725d-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="6725d-206">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="6725d-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="6725d-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="6725d-208">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="6725d-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="6725d-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="6725d-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="6725d-210">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="6725d-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="6725d-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="6725d-212">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="6725d-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="6725d-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="6725d-214">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="6725d-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="6725d-215">點網測試</span><span class="sxs-lookup"><span data-stu-id="6725d-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="6725d-216">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="6725d-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="6725d-217">專案參考</span><span class="sxs-lookup"><span data-stu-id="6725d-217">Project references</span></span>

<span data-ttu-id="6725d-218">Command</span><span class="sxs-lookup"><span data-stu-id="6725d-218">Command</span></span> | <span data-ttu-id="6725d-219">函式</span><span class="sxs-lookup"><span data-stu-id="6725d-219">Function</span></span>
--- | ---
[<span data-ttu-id="6725d-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="6725d-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="6725d-221">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="6725d-221">Adds a project reference.</span></span>
[<span data-ttu-id="6725d-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="6725d-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="6725d-223">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="6725d-223">Lists project references.</span></span>
[<span data-ttu-id="6725d-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="6725d-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="6725d-225">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="6725d-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="6725d-226">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="6725d-226">NuGet packages</span></span>

<span data-ttu-id="6725d-227">Command</span><span class="sxs-lookup"><span data-stu-id="6725d-227">Command</span></span> | <span data-ttu-id="6725d-228">函式</span><span class="sxs-lookup"><span data-stu-id="6725d-228">Function</span></span>
--- | ---
[<span data-ttu-id="6725d-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="6725d-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="6725d-230">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6725d-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="6725d-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="6725d-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="6725d-232">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6725d-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="6725d-233">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="6725d-233">NuGet commands</span></span>

<span data-ttu-id="6725d-234">Command</span><span class="sxs-lookup"><span data-stu-id="6725d-234">Command</span></span> | <span data-ttu-id="6725d-235">函式</span><span class="sxs-lookup"><span data-stu-id="6725d-235">Function</span></span>
--- | ---
[<span data-ttu-id="6725d-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="6725d-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="6725d-237">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="6725d-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="6725d-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="6725d-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="6725d-239">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="6725d-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="6725d-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="6725d-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="6725d-241">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="6725d-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="6725d-242">全域、工具路徑和本地工具命令</span><span class="sxs-lookup"><span data-stu-id="6725d-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="6725d-243">工具是從 NuGet 包安裝並從命令提示符調用的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="6725d-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="6725d-244">您可以自己編寫工具或安裝由協力廠商編寫的工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="6725d-245">工具也稱為全域工具、刀具路徑工具和本地工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="6725d-246">有關詳細資訊，請參閱[.NET 核心工具概述](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="6725d-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="6725d-247">全域和工具路徑工具可從 .NET 核心 SDK 2.1 開始。</span><span class="sxs-lookup"><span data-stu-id="6725d-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="6725d-248">本地工具可從 .NET 核心 SDK 3.0 開始。</span><span class="sxs-lookup"><span data-stu-id="6725d-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="6725d-249">Command</span><span class="sxs-lookup"><span data-stu-id="6725d-249">Command</span></span> | <span data-ttu-id="6725d-250">函式</span><span class="sxs-lookup"><span data-stu-id="6725d-250">Function</span></span>
--- | ---
[<span data-ttu-id="6725d-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="6725d-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="6725d-252">在電腦上安裝工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="6725d-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="6725d-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="6725d-254">列出電腦上當前安裝的所有全域、工具路徑或本地工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="6725d-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="6725d-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="6725d-256">從電腦卸載工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="6725d-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="6725d-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="6725d-258">更新安裝在電腦上的工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="6725d-259">其他工具</span><span class="sxs-lookup"><span data-stu-id="6725d-259">Additional tools</span></span>

<span data-ttu-id="6725d-260">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="6725d-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="6725d-261">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="6725d-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="6725d-262">工具</span><span class="sxs-lookup"><span data-stu-id="6725d-262">Tool</span></span>                                              | <span data-ttu-id="6725d-263">函式</span><span class="sxs-lookup"><span data-stu-id="6725d-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="6725d-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="6725d-264">dev-certs</span></span>                                         | <span data-ttu-id="6725d-265">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="6725d-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="6725d-266">ef</span><span class="sxs-lookup"><span data-stu-id="6725d-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="6725d-267">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="6725d-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="6725d-268">sql-cache</span></span>                                         | <span data-ttu-id="6725d-269">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="6725d-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="6725d-270">user-secrets</span><span class="sxs-lookup"><span data-stu-id="6725d-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="6725d-271">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="6725d-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="6725d-272">看</span><span class="sxs-lookup"><span data-stu-id="6725d-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="6725d-273">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="6725d-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="6725d-274">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="6725d-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="6725d-275">範例</span><span class="sxs-lookup"><span data-stu-id="6725d-275">Examples</span></span>

<span data-ttu-id="6725d-276">創建新的 .NET 核心主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="6725d-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="6725d-277">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="6725d-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="6725d-278">運行應用程式：</span><span class="sxs-lookup"><span data-stu-id="6725d-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="6725d-279">環境變數</span><span class="sxs-lookup"><span data-stu-id="6725d-279">Environment variables</span></span>

- <span data-ttu-id="6725d-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="6725d-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="6725d-281">指定 .NET Core 運行時的位置（如果它們未安裝在預設位置）。</span><span class="sxs-lookup"><span data-stu-id="6725d-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="6725d-282">Windows 上的預設位置為`C:\Program Files\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="6725d-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="6725d-283">Linux 和 macOS 上的預設`/usr/share/dotnet`位置為 。</span><span class="sxs-lookup"><span data-stu-id="6725d-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="6725d-284">僅當通過生成的可執行檔（應用程式主機）運行應用時，才會使用此環境變數。</span><span class="sxs-lookup"><span data-stu-id="6725d-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="6725d-285">`DOTNET_ROOT(x86)`在 64 位作業系統上運行 32 位可執行檔時，將改為使用。</span><span class="sxs-lookup"><span data-stu-id="6725d-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="6725d-286">全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="6725d-286">The global packages folder.</span></span> <span data-ttu-id="6725d-287">如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="6725d-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="6725d-288">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="6725d-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="6725d-289">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="6725d-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="6725d-290">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="6725d-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="6725d-291">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="6725d-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="6725d-292">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="6725d-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="6725d-293">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="6725d-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="6725d-294">如果未設置，則預設為 1（邏輯`true`）。</span><span class="sxs-lookup"><span data-stu-id="6725d-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="6725d-295">設置為 0（邏輯`false`），以不從全域位置解析，並且具有隔離的 .NET Core 安裝。</span><span class="sxs-lookup"><span data-stu-id="6725d-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="6725d-296">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="6725d-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="6725d-297">`DOTNET_ROLL_FORWARD`**可從 .NET 核心 3.x SDK 開始。**</span><span class="sxs-lookup"><span data-stu-id="6725d-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="6725d-298">確定向前滾行行為。</span><span class="sxs-lookup"><span data-stu-id="6725d-298">Determines roll forward behavior.</span></span> <span data-ttu-id="6725d-299">有關詳細資訊，請參閱本文前面`--roll-forward`的選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="6725d-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**在 .NET 核心 2.x SDK 中提供。**</span><span class="sxs-lookup"><span data-stu-id="6725d-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="6725d-301">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="6725d-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="6725d-302">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="6725d-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="6725d-303">使用地區設定值（如`en-us`）設置 CLI UI 的語言。</span><span class="sxs-lookup"><span data-stu-id="6725d-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="6725d-304">支援的值與 Visual Studio 的值相同。</span><span class="sxs-lookup"><span data-stu-id="6725d-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="6725d-305">有關詳細資訊，請參閱[Visual Studio 安裝文檔中](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)有關更改安裝程式語言的部分。</span><span class="sxs-lookup"><span data-stu-id="6725d-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="6725d-306">.NET 資源管理器規則適用，因此您不必選擇完全符合項&mdash;，您也可以在樹中選擇`CultureInfo`後代。</span><span class="sxs-lookup"><span data-stu-id="6725d-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="6725d-307">例如，如果將其設置為`fr-CA`，CLI 將查找並使用`fr`翻譯。</span><span class="sxs-lookup"><span data-stu-id="6725d-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="6725d-308">如果將其設置為不支援的語言，則 CLI 將回退為英語。</span><span class="sxs-lookup"><span data-stu-id="6725d-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="6725d-309">對於啟用 GUI 生成的可執行檔 - 禁用通常顯示某些類別錯誤的對話方塊快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="6725d-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="6725d-310">在這種情況下，它只寫入`stderr`和退出。</span><span class="sxs-lookup"><span data-stu-id="6725d-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="6725d-311">等效于 CLI`--additional-deps`選項。</span><span class="sxs-lookup"><span data-stu-id="6725d-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="6725d-312">覆蓋檢測到的 RID。</span><span class="sxs-lookup"><span data-stu-id="6725d-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="6725d-313">"共用存儲"的位置，在某些情況下，程式集解析度會回退于該存儲。</span><span class="sxs-lookup"><span data-stu-id="6725d-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="6725d-314">要載入和執行啟動掛鉤的程式集的清單。</span><span class="sxs-lookup"><span data-stu-id="6725d-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="6725d-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="6725d-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="6725d-316">控制從宿主元件（如`dotnet.exe`）`hostfxr`和`hostpolicy`的診斷跟蹤。</span><span class="sxs-lookup"><span data-stu-id="6725d-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6725d-317">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6725d-317">See also</span></span>

- <span data-ttu-id="6725d-318">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)</span><span class="sxs-lookup"><span data-stu-id="6725d-318">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)</span></span>
- [<span data-ttu-id="6725d-319">.NET 核心運行時配置設置</span><span class="sxs-lookup"><span data-stu-id="6725d-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
