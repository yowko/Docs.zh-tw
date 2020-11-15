---
title: dotnet 命令
description: 瞭解 dotnet 命令 (.NET CLI 的一般驅動程式) 和其使用方式。
ms.date: 11/11/2020
ms.openlocfilehash: 7a0c8f2eb7ab407bd725db56cbf31da4689970e4
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634021"
---
# <a name="dotnet-command"></a><span data-ttu-id="a7cac-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-103">dotnet command</span></span>

<span data-ttu-id="a7cac-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a7cac-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a7cac-105">名稱</span><span class="sxs-lookup"><span data-stu-id="a7cac-105">Name</span></span>

<span data-ttu-id="a7cac-106">`dotnet` -.NET CLI 的一般驅動程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-106">`dotnet` - The generic driver for the .NET CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7cac-107">概要</span><span class="sxs-lookup"><span data-stu-id="a7cac-107">Synopsis</span></span>

<span data-ttu-id="a7cac-108">若要取得可用命令和環境的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="a7cac-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="a7cac-109">若要執行命令 (需要 SDK 安裝) ：</span><span class="sxs-lookup"><span data-stu-id="a7cac-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="a7cac-110">若要執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="a7cac-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="a7cac-111">`--roll-forward` 自 .NET Core 3.x 起提供。</span><span class="sxs-lookup"><span data-stu-id="a7cac-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="a7cac-112">用於 `--roll-forward-on-no-candidate-fx` .Net Core 2.x。</span><span class="sxs-lookup"><span data-stu-id="a7cac-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="a7cac-113">描述</span><span class="sxs-lookup"><span data-stu-id="a7cac-113">Description</span></span>

<span data-ttu-id="a7cac-114">此 `dotnet` 命令有兩個功能：</span><span class="sxs-lookup"><span data-stu-id="a7cac-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="a7cac-115">它提供使用 .NET 專案的命令。</span><span class="sxs-lookup"><span data-stu-id="a7cac-115">It provides commands for working with .NET projects.</span></span>

  <span data-ttu-id="a7cac-116">例如， [`dotnet build`](dotnet-build.md) 建立專案。</span><span class="sxs-lookup"><span data-stu-id="a7cac-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="a7cac-117">每個命令都會定義自己的選項和引數。</span><span class="sxs-lookup"><span data-stu-id="a7cac-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="a7cac-118">所有命令都支援 `--help` 列印出有關如何使用命令的簡短檔的選項。</span><span class="sxs-lookup"><span data-stu-id="a7cac-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="a7cac-119">它會執行 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-119">It runs .NET applications.</span></span>

  <span data-ttu-id="a7cac-120">您可以指定應用程式檔的路徑 `.dll` 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="a7cac-121">若要執行應用程式，您可以尋找並執行進入點，在主控台應用程式的案例中，這是 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="a7cac-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="a7cac-122">例如，會 `dotnet myapp.dll` 執行 `myapp` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="a7cac-123">若要瞭解部署選項，請參閱 [.net 應用程式部署](../deploying/index.md) 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-123">See [.NET application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="a7cac-124">選項</span><span class="sxs-lookup"><span data-stu-id="a7cac-124">Options</span></span>

<span data-ttu-id="a7cac-125">您可以使用不同的選項來執行 `dotnet` 命令，以及執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="a7cac-126">Dotnet 本身的選項</span><span class="sxs-lookup"><span data-stu-id="a7cac-126">Options for dotnet by itself</span></span>

<span data-ttu-id="a7cac-127">以下是本身的選項 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="a7cac-128">例如，`dotnet --info`。</span><span class="sxs-lookup"><span data-stu-id="a7cac-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="a7cac-129">他們會列印環境的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a7cac-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="a7cac-130">列印 .NET 安裝和電腦環境的詳細資訊，例如目前的作業系統，以及 .NET 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a7cac-130">Prints out detailed information about a .NET installation and the machine environment, such as the current operating system, and commit SHA of the .NET version.</span></span>

- **`--version`**

  <span data-ttu-id="a7cac-131">列印出使用中的 .NET SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-131">Prints out the version of the .NET SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="a7cac-132">列印已安裝之 .NET 執行時間的清單。</span><span class="sxs-lookup"><span data-stu-id="a7cac-132">Prints out a list of the installed .NET runtimes.</span></span> <span data-ttu-id="a7cac-133">X86 版本的 SDK 只會列出 x86 執行時間，而 x64 版本的 SDK 只會列出 x64 執行時間。</span><span class="sxs-lookup"><span data-stu-id="a7cac-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="a7cac-134">列印已安裝的 .NET Sdk 清單。</span><span class="sxs-lookup"><span data-stu-id="a7cac-134">Prints out a list of the installed .NET SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a7cac-135">列印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a7cac-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="a7cac-136">用來執行命令的 SDK 選項</span><span class="sxs-lookup"><span data-stu-id="a7cac-136">SDK options for running a command</span></span>

<span data-ttu-id="a7cac-137">以下是 `dotnet` 使用命令的選項。</span><span class="sxs-lookup"><span data-stu-id="a7cac-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="a7cac-138">例如，`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a7cac-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="a7cac-139">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a7cac-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a7cac-140">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a7cac-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7cac-141">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a7cac-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a7cac-142">不支援每個命令。</span><span class="sxs-lookup"><span data-stu-id="a7cac-142">Not supported in every command.</span></span> <span data-ttu-id="a7cac-143">請參閱特定的命令頁面，判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a7cac-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a7cac-144">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a7cac-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="a7cac-145">每個命令都會定義該命令特定的選項。</span><span class="sxs-lookup"><span data-stu-id="a7cac-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="a7cac-146">請參閱特定的命令頁面，以取得可用選項的清單。</span><span class="sxs-lookup"><span data-stu-id="a7cac-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="a7cac-147">執行時間選項</span><span class="sxs-lookup"><span data-stu-id="a7cac-147">Runtime options</span></span>

<span data-ttu-id="a7cac-148">當您執行應用程式時，可以使用下列選項 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="a7cac-149">例如，`dotnet myapp.dll --roll-forward Major`。</span><span class="sxs-lookup"><span data-stu-id="a7cac-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="a7cac-150">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a7cac-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="a7cac-151">其他 *.deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a7cac-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="a7cac-152">檔案 *deps.js* 包含相依性、編譯相依性的清單，以及用來解決元件衝突的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a7cac-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a7cac-153">如需詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="a7cac-154">檔案 *deps.js* 的路徑。</span><span class="sxs-lookup"><span data-stu-id="a7cac-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="a7cac-155">檔案 *上的deps.js* 是一個設定檔，其中包含執行應用程式所需相依性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a7cac-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="a7cac-156">這個檔案是由 .NET SDK 產生。</span><span class="sxs-lookup"><span data-stu-id="a7cac-156">This file is generated by the .NET SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="a7cac-157">*runtimeconfig.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a7cac-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="a7cac-158">檔案 *上的runtimeconfig.js* 是包含執行時間設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="a7cac-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="a7cac-159">如需詳細資訊，請參閱 [.net 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-159">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="a7cac-160">**`--roll-forward <SETTING>`\*\*\*\*從 .NET Core SDK 3.0 開始提供。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="a7cac-161">控制如何將向前復原套用至應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="a7cac-162">`SETTING`可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="a7cac-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="a7cac-163">如果未指定， `Minor` 則為預設值。</span><span class="sxs-lookup"><span data-stu-id="a7cac-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="a7cac-164">`LatestPatch` -向前復原到最高的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="a7cac-165">這會停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a7cac-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="a7cac-166">`Minor` -如果遺漏要求的次要版本，則向前復原到最低的次要版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="a7cac-167">如果要求的次要版本存在，則會使用 LatestPatch 原則。</span><span class="sxs-lookup"><span data-stu-id="a7cac-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="a7cac-168">`Major` -如果缺少要求的主要版本，則向前復原到最低的最高主要版本，以及最低的次要版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="a7cac-169">如果要求的主要版本存在，則會使用 Minor 原則。</span><span class="sxs-lookup"><span data-stu-id="a7cac-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="a7cac-170">`LatestMinor` -向前復原到最高的次要版本，即使有要求的次要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="a7cac-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="a7cac-171">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="a7cac-172">`LatestMajor` -向前復原到最高的主要和最高次要版本，即使有要求的主要存在。</span><span class="sxs-lookup"><span data-stu-id="a7cac-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="a7cac-173">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="a7cac-174">`Disable` -不要向前復原。</span><span class="sxs-lookup"><span data-stu-id="a7cac-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="a7cac-175">只會繫結至指定的版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-175">Only bind to specified version.</span></span> <span data-ttu-id="a7cac-176">此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。</span><span class="sxs-lookup"><span data-stu-id="a7cac-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="a7cac-177">只有測試時才建議使用這個值。</span><span class="sxs-lookup"><span data-stu-id="a7cac-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="a7cac-178">除了之外 `Disable` ，所有設定都會使用最高可用的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="a7cac-179">向前復原行為也可以在專案檔案屬性、執行時間配置檔案屬性和環境變數中設定。</span><span class="sxs-lookup"><span data-stu-id="a7cac-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="a7cac-180">如需詳細資訊，請參閱 [主要版本執行時間向前](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)復原。</span><span class="sxs-lookup"><span data-stu-id="a7cac-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="a7cac-181">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*適用于 .Net Core 2.X SDK。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="a7cac-182">在必要的共用架構無法使用時定義行為。</span><span class="sxs-lookup"><span data-stu-id="a7cac-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="a7cac-183">`N` 可以是：</span><span class="sxs-lookup"><span data-stu-id="a7cac-183">`N` can be:</span></span>

  - <span data-ttu-id="a7cac-184">`0` - 對次要版本也停用向前復原。</span><span class="sxs-lookup"><span data-stu-id="a7cac-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="a7cac-185">`1` - 對次要版本向前復原，主要版本則不。</span><span class="sxs-lookup"><span data-stu-id="a7cac-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="a7cac-186">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="a7cac-186">This is the default behavior.</span></span>
  - <span data-ttu-id="a7cac-187">`2` - 對次要及主要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a7cac-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="a7cac-188">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="a7cac-189">從 .NET Core 3.0 開始，此選項會被取代 `--roll-forward` ，而且應該改用該選項。</span><span class="sxs-lookup"><span data-stu-id="a7cac-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="a7cac-190">要用來執行應用程式的 .NET 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-190">Version of the .NET runtime to use to run the application.</span></span>

  <span data-ttu-id="a7cac-191">此選項會覆寫應用程式檔案中第一個架構參考的版本 `.runtimeconfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="a7cac-192">這表示如果只有一個架構參考，它只會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="a7cac-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="a7cac-193">如果應用程式有一個以上的架構參考，則使用這個選項可能會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7cac-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="a7cac-194">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="a7cac-195">一般</span><span class="sxs-lookup"><span data-stu-id="a7cac-195">General</span></span>

| <span data-ttu-id="a7cac-196">命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-196">Command</span></span>                                       | <span data-ttu-id="a7cac-197">函式</span><span class="sxs-lookup"><span data-stu-id="a7cac-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a7cac-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a7cac-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="a7cac-199">建立 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-199">Builds a .NET application.</span></span>                                     |
| [<span data-ttu-id="a7cac-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="a7cac-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="a7cac-201">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="a7cac-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="a7cac-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a7cac-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="a7cac-203">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a7cac-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="a7cac-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a7cac-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="a7cac-205">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a7cac-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a7cac-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="a7cac-207">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a7cac-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a7cac-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a7cac-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="a7cac-209">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a7cac-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a7cac-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a7cac-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="a7cac-211">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a7cac-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a7cac-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a7cac-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="a7cac-213">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a7cac-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a7cac-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="a7cac-215">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a7cac-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a7cac-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="a7cac-217">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a7cac-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a7cac-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a7cac-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="a7cac-219">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a7cac-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a7cac-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="a7cac-221">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a7cac-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a7cac-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a7cac-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="a7cac-223">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a7cac-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a7cac-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="a7cac-225">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a7cac-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="a7cac-226">專案參考</span><span class="sxs-lookup"><span data-stu-id="a7cac-226">Project references</span></span>

<span data-ttu-id="a7cac-227">命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-227">Command</span></span> | <span data-ttu-id="a7cac-228">函式</span><span class="sxs-lookup"><span data-stu-id="a7cac-228">Function</span></span>
--- | ---
[<span data-ttu-id="a7cac-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a7cac-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="a7cac-230">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="a7cac-230">Adds a project reference.</span></span>
[<span data-ttu-id="a7cac-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a7cac-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="a7cac-232">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="a7cac-232">Lists project references.</span></span>
[<span data-ttu-id="a7cac-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a7cac-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="a7cac-234">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="a7cac-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="a7cac-235">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="a7cac-235">NuGet packages</span></span>

<span data-ttu-id="a7cac-236">命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-236">Command</span></span> | <span data-ttu-id="a7cac-237">函式</span><span class="sxs-lookup"><span data-stu-id="a7cac-237">Function</span></span>
--- | ---
[<span data-ttu-id="a7cac-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="a7cac-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="a7cac-239">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="a7cac-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a7cac-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="a7cac-241">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="a7cac-242">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-242">NuGet commands</span></span>

<span data-ttu-id="a7cac-243">命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-243">Command</span></span> | <span data-ttu-id="a7cac-244">函式</span><span class="sxs-lookup"><span data-stu-id="a7cac-244">Function</span></span>
--- | ---
[<span data-ttu-id="a7cac-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="a7cac-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="a7cac-246">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="a7cac-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="a7cac-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a7cac-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="a7cac-248">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="a7cac-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="a7cac-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="a7cac-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="a7cac-250">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="a7cac-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="a7cac-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="a7cac-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="a7cac-252">新增 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a7cac-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="a7cac-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="a7cac-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="a7cac-254">停用 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a7cac-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="a7cac-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="a7cac-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="a7cac-256">啟用 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a7cac-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="a7cac-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="a7cac-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="a7cac-258">列出所有已設定的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a7cac-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="a7cac-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="a7cac-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="a7cac-260">移除 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a7cac-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="a7cac-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="a7cac-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="a7cac-262">更新 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a7cac-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="a7cac-263">全域、工具路徑和本機工具命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="a7cac-264">工具是從 NuGet 套件安裝的主控台應用程式，會從命令提示字元叫用。</span><span class="sxs-lookup"><span data-stu-id="a7cac-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="a7cac-265">您可以自行撰寫工具或安裝協力廠商所撰寫的工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="a7cac-266">工具也稱為「通用工具」、「工具路徑工具」和「本機工具」。</span><span class="sxs-lookup"><span data-stu-id="a7cac-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="a7cac-267">如需詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-267">For more information, see [.NET tools overview](global-tools.md).</span></span> <span data-ttu-id="a7cac-268">從 .NET Core SDK 2.1 開始，可以使用全域和工具路徑工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="a7cac-269">從 .NET Core SDK 3.0 開始，可以使用本機工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="a7cac-270">命令</span><span class="sxs-lookup"><span data-stu-id="a7cac-270">Command</span></span> | <span data-ttu-id="a7cac-271">函式</span><span class="sxs-lookup"><span data-stu-id="a7cac-271">Function</span></span>
--- | ---
[<span data-ttu-id="a7cac-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a7cac-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="a7cac-273">在您的電腦上安裝工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="a7cac-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a7cac-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a7cac-275">列出電腦上目前已安裝的所有全域、工具路徑或本機工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="a7cac-276">dotnet 工具搜尋</span><span class="sxs-lookup"><span data-stu-id="a7cac-276">dotnet tool search</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a7cac-277">搜尋 NuGet.org 是否有在其名稱或中繼資料中具有指定之搜尋詞彙的工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-277">Searches NuGet.org for tools that have the specified search term in their name or metadata.</span></span>
[<span data-ttu-id="a7cac-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="a7cac-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="a7cac-279">從您的電腦卸載工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-279">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="a7cac-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="a7cac-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="a7cac-281">更新電腦上所安裝的工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-281">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="a7cac-282">其他工具</span><span class="sxs-lookup"><span data-stu-id="a7cac-282">Additional tools</span></span>

<span data-ttu-id="a7cac-283">從 .NET Core SDK 2.1.300 開始，使用的一些工具現在僅適用于以專案為基礎的工具， `DotnetCliToolReference` 現在已可在 .NET SDK 中使用。</span><span class="sxs-lookup"><span data-stu-id="a7cac-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET SDK.</span></span> <span data-ttu-id="a7cac-284">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="a7cac-284">These tools are listed in the following table:</span></span>

| <span data-ttu-id="a7cac-285">工具</span><span class="sxs-lookup"><span data-stu-id="a7cac-285">Tool</span></span>                                              | <span data-ttu-id="a7cac-286">函式</span><span class="sxs-lookup"><span data-stu-id="a7cac-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="a7cac-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="a7cac-287">dev-certs</span></span>                                         | <span data-ttu-id="a7cac-288">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="a7cac-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="a7cac-289">ef</span><span class="sxs-lookup"><span data-stu-id="a7cac-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="a7cac-290">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="a7cac-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="a7cac-291">sql-cache</span></span>                                         | <span data-ttu-id="a7cac-292">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a7cac-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="a7cac-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="a7cac-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="a7cac-294">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="a7cac-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="a7cac-295">看</span><span class="sxs-lookup"><span data-stu-id="a7cac-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="a7cac-296">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="a7cac-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="a7cac-297">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="a7cac-297">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="a7cac-298">範例</span><span class="sxs-lookup"><span data-stu-id="a7cac-298">Examples</span></span>

<span data-ttu-id="a7cac-299">建立新的 .NET 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="a7cac-299">Create a new .NET console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="a7cac-300">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="a7cac-300">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a7cac-301">執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="a7cac-301">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="a7cac-302">環境變數</span><span class="sxs-lookup"><span data-stu-id="a7cac-302">Environment variables</span></span>

- <span data-ttu-id="a7cac-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="a7cac-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="a7cac-304">指定 .NET 執行時間的位置（如果未安裝在預設位置）。</span><span class="sxs-lookup"><span data-stu-id="a7cac-304">Specifies the location of the .NET runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="a7cac-305">Windows 上的預設位置為 `C:\Program Files\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-305">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="a7cac-306">Linux 和 macOS 上的預設位置為 `/usr/share/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-306">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="a7cac-307">此環境變數只會在透過產生的可執行檔（ (apphosts) ）執行應用程式時使用。</span><span class="sxs-lookup"><span data-stu-id="a7cac-307">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="a7cac-308">`DOTNET_ROOT(x86)` 當在64位作業系統上執行32位可執行檔時，會改用</span><span class="sxs-lookup"><span data-stu-id="a7cac-308">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `NUGET_PACKAGES`

  <span data-ttu-id="a7cac-309">全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="a7cac-309">The global packages folder.</span></span> <span data-ttu-id="a7cac-310">如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-310">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="a7cac-311">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a7cac-311">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="a7cac-312">指定是否要在第一次執行時顯示 .NET 歡迎畫面和遙測訊息。</span><span class="sxs-lookup"><span data-stu-id="a7cac-312">Specifies whether .NET welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="a7cac-313">設定為可將 `true` 這些訊息靜音 (值 `true` 、 `1` 或 `yes` 接受) 或設定為， `false` 以允許 (值 `false` 、 `0` 或 `no` 接受) 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-313">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a7cac-314">如果未設定，預設值為， `false` 而訊息將會在第一次執行時顯示。</span><span class="sxs-lookup"><span data-stu-id="a7cac-314">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="a7cac-315">此旗標不會影響遙測 (請參閱退出傳送 `DOTNET_CLI_TELEMETRY_OPTOUT` 遙測) 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-315">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="a7cac-316">指定是否收集 .NET 工具使用量的相關資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a7cac-316">Specifies whether data about the .NET tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a7cac-317">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-317">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a7cac-318">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-318">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a7cac-319">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a7cac-319">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="a7cac-320">指定是否從全域位置解析 .NET 執行時間、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="a7cac-320">Specifies whether .NET runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a7cac-321">如果未設定，則預設為 1 (邏輯 `true`) 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-321">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="a7cac-322">設定為 0 (邏輯 `false`) 不會從全域位置解析，並且具有隔離的 .net 安裝。</span><span class="sxs-lookup"><span data-stu-id="a7cac-322">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET installations.</span></span> <span data-ttu-id="a7cac-323">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-323">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="a7cac-324">`DOTNET_ROLL_FORWARD`**從 .Net Core 3.x 開始提供。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-324">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="a7cac-325">判斷向前復原行為。</span><span class="sxs-lookup"><span data-stu-id="a7cac-325">Determines roll forward behavior.</span></span> <span data-ttu-id="a7cac-326">如需詳細資訊，請參閱本文稍 `--roll-forward` 早的選項。</span><span class="sxs-lookup"><span data-stu-id="a7cac-326">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="a7cac-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE`**從 .Net Core 3.x 開始提供。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="a7cac-328">如果設定為 `1` (啟用) ，則可從發行版本向前復原至發行前版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-328">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="a7cac-329">依預設 (`0` -disabled) ，當要求 .net 執行時間的發行版本時，向前復原只會考慮已安裝的發行版本。</span><span class="sxs-lookup"><span data-stu-id="a7cac-329">By default (`0` - disabled), when a release version of .NET runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="a7cac-330">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-330">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="a7cac-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**適用于 .Net Core 2.x。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="a7cac-332">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a7cac-332">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a7cac-333">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a7cac-333">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="a7cac-334">這項設定已在 .NET Core 3.0 中取代 `DOTNET_ROLL_FORWARD` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-334">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="a7cac-335">您應改為使用新的設定。</span><span class="sxs-lookup"><span data-stu-id="a7cac-335">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="a7cac-336">使用地區設定值（例如）設定 CLI UI 的語言 `en-us` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-336">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="a7cac-337">支援的值與 Visual Studio 的值相同。</span><span class="sxs-lookup"><span data-stu-id="a7cac-337">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="a7cac-338">如需詳細資訊，請參閱 [Visual Studio 安裝檔](/visualstudio/install/install-visual-studio)中的變更安裝程式語言一節。</span><span class="sxs-lookup"><span data-stu-id="a7cac-338">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="a7cac-339">適用 .NET resource manager 規則，因此您不需要挑選完全相符的結果， &mdash; 您也可以在樹狀目錄中挑選子系 `CultureInfo` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-339">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="a7cac-340">例如，如果您將它設定為 `fr-CA` ，CLI 會尋找並使用 `fr` 翻譯。</span><span class="sxs-lookup"><span data-stu-id="a7cac-340">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="a7cac-341">如果您將它設定為不支援的語言，CLI 會切換回英文。</span><span class="sxs-lookup"><span data-stu-id="a7cac-341">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="a7cac-342">啟用 GUI 的已產生可執行檔-停用對話方塊快顯視窗，通常會針對某些錯誤類別顯示。</span><span class="sxs-lookup"><span data-stu-id="a7cac-342">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="a7cac-343">它只會 `stderr` 在這些情況下寫入和結束。</span><span class="sxs-lookup"><span data-stu-id="a7cac-343">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="a7cac-344">相當於 CLI 選項 `--additional-deps` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-344">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="a7cac-345">覆寫偵測到的 RID。</span><span class="sxs-lookup"><span data-stu-id="a7cac-345">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="a7cac-346">「共用存放區」的位置，在某些情況下，元件解析會回復為。</span><span class="sxs-lookup"><span data-stu-id="a7cac-346">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="a7cac-347">要載入和執行啟動攔截的元件清單。</span><span class="sxs-lookup"><span data-stu-id="a7cac-347">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="a7cac-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR`**從 .Net Core 3.x 開始提供。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="a7cac-349">指定在執行單一檔案應用程式之前解壓縮的目錄。</span><span class="sxs-lookup"><span data-stu-id="a7cac-349">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="a7cac-350">如需詳細資訊，請參閱 [單一檔案可執行](../whats-new/dotnet-core-3-0.md#single-file-executables)檔。</span><span class="sxs-lookup"><span data-stu-id="a7cac-350">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="a7cac-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="a7cac-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="a7cac-352">控制來自裝載元件的診斷追蹤，例如 `dotnet.exe` 、 `hostfxr` 和 `hostpolicy` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-352">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="a7cac-353">`COREHOST_TRACE=[0/1]` -預設為 `0` -追蹤已停用。</span><span class="sxs-lookup"><span data-stu-id="a7cac-353">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="a7cac-354">如果設定為 `1` ，則會啟用診斷追蹤。</span><span class="sxs-lookup"><span data-stu-id="a7cac-354">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="a7cac-355">`COREHOST_TRACEFILE=<file path>` -只有在啟用追蹤時，才會有作用 `COREHOST_TRACE=1` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-355">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="a7cac-356">設定時，追蹤資訊會寫入至指定的檔案，否則會將追蹤資訊寫入至 `stderr` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-356">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="a7cac-357">**從 .NET Core 3.x 開始提供。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-357">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="a7cac-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` -預設值為 `4` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="a7cac-359">只有透過啟用追蹤時，才會使用此設定 `COREHOST_TRACE=1` 。</span><span class="sxs-lookup"><span data-stu-id="a7cac-359">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="a7cac-360">**從 .NET Core 3.x 開始提供。**</span><span class="sxs-lookup"><span data-stu-id="a7cac-360">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="a7cac-361">`4` -寫入所有追蹤資訊</span><span class="sxs-lookup"><span data-stu-id="a7cac-361">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="a7cac-362">`3` -只寫入參考、警告和錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="a7cac-362">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="a7cac-363">`2` -只寫入警告和錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="a7cac-363">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="a7cac-364">`1` -只寫入錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="a7cac-364">`1` - only error messages are written</span></span>

  <span data-ttu-id="a7cac-365">取得應用程式啟動詳細追蹤資訊的一般方式是設定，然後 `COREHOST_TRACE=1` `COREHOST_TRACEFILE=host_trace.txt` 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7cac-365">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="a7cac-366">`host_trace.txt`將會在目前目錄中建立含有詳細資訊的新檔案。</span><span class="sxs-lookup"><span data-stu-id="a7cac-366">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7cac-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7cac-367">See also</span></span>

- <span data-ttu-id="a7cac-368">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)</span><span class="sxs-lookup"><span data-stu-id="a7cac-368">[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)</span></span>
- [<span data-ttu-id="a7cac-369">.NET 執行時間設定</span><span class="sxs-lookup"><span data-stu-id="a7cac-369">.NET run-time configuration settings</span></span>](../run-time-config/index.md)
