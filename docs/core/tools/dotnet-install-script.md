---
title: dotnet-install 指令碼
description: 了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: acdf49950ebb49751c55ae72b3f623e590489202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214376"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="4d170-103">dotnet-install 指令碼參考</span><span class="sxs-lookup"><span data-stu-id="4d170-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="4d170-104">名稱</span><span class="sxs-lookup"><span data-stu-id="4d170-104">Name</span></span>

<span data-ttu-id="4d170-105">`dotnet-install.ps1` | `dotnet-install.sh` - 用來安裝 .NET Core CLI 工具和共用執行階段的指令碼。</span><span class="sxs-lookup"><span data-stu-id="4d170-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4d170-106">概要</span><span class="sxs-lookup"><span data-stu-id="4d170-106">Synopsis</span></span>

<span data-ttu-id="4d170-107">Windows：</span><span class="sxs-lookup"><span data-stu-id="4d170-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="4d170-108">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="4d170-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="4d170-109">描述</span><span class="sxs-lookup"><span data-stu-id="4d170-109">Description</span></span>

<span data-ttu-id="4d170-110">`dotnet-install` 指令碼可用來執行 .NET Core SDK 的非系統管理安裝，其中包含了 .NET Core CLI 工具和共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="4d170-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="4d170-111">建議您使用 [.NET Core 主網站](https://dot.net) \(英文\) 所提供的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="4d170-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="4d170-112">指令碼的直接路徑如下：</span><span class="sxs-lookup"><span data-stu-id="4d170-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="4d170-113">https://dot.net/v1/dotnet-install.sh (bash、UNIX)</span><span class="sxs-lookup"><span data-stu-id="4d170-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="4d170-114">https://dot.net/v1/dotnet-install.ps1 (Powershell、Windows)</span><span class="sxs-lookup"><span data-stu-id="4d170-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="4d170-115">這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="4d170-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="4d170-116">指令碼有兩種：一種是在 Windows 上使用的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="4d170-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="4d170-117">另一個指令碼是可在 Linux/macOS 上運作的 bash 指令碼。</span><span class="sxs-lookup"><span data-stu-id="4d170-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="4d170-118">這兩個指令碼有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="4d170-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="4d170-119">Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。</span><span class="sxs-lookup"><span data-stu-id="4d170-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="4d170-120">安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="4d170-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="4d170-121">根據預設，安裝指令碼會下載並安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="4d170-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="4d170-122">如果您想要只取得共用執行階段，請指定 `--shared-runtime` 引數。</span><span class="sxs-lookup"><span data-stu-id="4d170-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="4d170-123">根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。</span><span class="sxs-lookup"><span data-stu-id="4d170-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="4d170-124">指定 `--no-path` 引數可以覆寫此預設行為。</span><span class="sxs-lookup"><span data-stu-id="4d170-124">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="4d170-125">執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="4d170-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="4d170-126">您可以使用 `--version` 引數安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="4d170-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="4d170-127">必須以三段式版本的格式指定版本 (例如，1.0.0-13232)。</span><span class="sxs-lookup"><span data-stu-id="4d170-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="4d170-128">如果省略，就會使用 `latest` 版本。</span><span class="sxs-lookup"><span data-stu-id="4d170-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="4d170-129">選項</span><span class="sxs-lookup"><span data-stu-id="4d170-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="4d170-130">指定安裝的來源通道。</span><span class="sxs-lookup"><span data-stu-id="4d170-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="4d170-131">可能值為：</span><span class="sxs-lookup"><span data-stu-id="4d170-131">The possible values are:</span></span>

- <span data-ttu-id="4d170-132">`Current` - 目前的版本</span><span class="sxs-lookup"><span data-stu-id="4d170-132">`Current` - Current release</span></span>
- <span data-ttu-id="4d170-133">`LTS` - 長期支援通道 (目前支援的版本)</span><span class="sxs-lookup"><span data-stu-id="4d170-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="4d170-134">X.Y 格式的兩部分版本代表特定版本 (例如 `2.0` 或 `1.0`)</span><span class="sxs-lookup"><span data-stu-id="4d170-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="4d170-135">分支名稱 [例如 `release/2.0.0`、`release/2.0.0-preview2`，或針對最新 `master` 分支的 `master` (「高度風險」每日更新版)]</span><span class="sxs-lookup"><span data-stu-id="4d170-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="4d170-136">預設值是 `LTS`。</span><span class="sxs-lookup"><span data-stu-id="4d170-136">The default value is `LTS`.</span></span> <span data-ttu-id="4d170-137">如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援週期](https://www.microsoft.com/net/core/support) \(英文\) 主題。</span><span class="sxs-lookup"><span data-stu-id="4d170-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="4d170-138">代表特定的組建版本。</span><span class="sxs-lookup"><span data-stu-id="4d170-138">Represents a specific build version.</span></span> <span data-ttu-id="4d170-139">可能值為：</span><span class="sxs-lookup"><span data-stu-id="4d170-139">The possible values are:</span></span>

- <span data-ttu-id="4d170-140">`latest` - 通道上的最新組建 (搭配 `-Channel` 選項來使用)</span><span class="sxs-lookup"><span data-stu-id="4d170-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="4d170-141">`coherent` - 通道上的最新一致性組建，使用最新的穩定套件組合 (搭配分支名稱 `-Channel` 選項來使用)</span><span class="sxs-lookup"><span data-stu-id="4d170-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="4d170-142">代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。</span><span class="sxs-lookup"><span data-stu-id="4d170-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="4d170-143">例如：`2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="4d170-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="4d170-144">如果省略，`-Version` 預設會設為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="4d170-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="4d170-145">指定安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="4d170-145">Specifies the installation path.</span></span> <span data-ttu-id="4d170-146">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="4d170-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="4d170-147">預設值為 *%LocalAppData%\.dotnet*。</span><span class="sxs-lookup"><span data-stu-id="4d170-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="4d170-148">請注意，二進位檔會直接放置在目錄中。</span><span class="sxs-lookup"><span data-stu-id="4d170-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="4d170-149">要安裝的 .NET Core 二進位檔的架構。</span><span class="sxs-lookup"><span data-stu-id="4d170-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="4d170-150">可能的值為 `auto`、`x64` 和 `x86`。</span><span class="sxs-lookup"><span data-stu-id="4d170-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="4d170-151">預設值為 `auto`，代表目前正在執行的 OS 架構。</span><span class="sxs-lookup"><span data-stu-id="4d170-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="4d170-152">如果設定，則此參數會限制在共用執行階段的安裝。</span><span class="sxs-lookup"><span data-stu-id="4d170-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="4d170-153">尚未安裝整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="4d170-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="4d170-154">如果設定，指令碼將不會執行安裝，而是會顯示以一致的方式安裝目前要求的 .NET Core CLI 版本時所要使用的命令列。</span><span class="sxs-lookup"><span data-stu-id="4d170-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="4d170-155">例如，如果您指定 `latest` 版本，則會顯示特定版本的連結，以便可在建置指令碼中明確使用此命令。</span><span class="sxs-lookup"><span data-stu-id="4d170-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="4d170-156">如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。</span><span class="sxs-lookup"><span data-stu-id="4d170-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="4d170-157">如果設定，則不會將 prefix/installdir 匯出至目前工作階段的路徑。</span><span class="sxs-lookup"><span data-stu-id="4d170-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="4d170-158">根據預設，指令碼將會修改此路徑，以在安裝後立即提供 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="4d170-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="4d170-159">指定給安裝程式的 Azure 摘要 URL。</span><span class="sxs-lookup"><span data-stu-id="4d170-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="4d170-160">不建議您變更這個值。</span><span class="sxs-lookup"><span data-stu-id="4d170-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="4d170-161">預設為 `https://dotnetcli.azureedge.net/dotnet`。</span><span class="sxs-lookup"><span data-stu-id="4d170-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="4d170-162">如果設定，安裝程式會使用此 Proxy 進行 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="4d170-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="4d170-163">(只適用於 Windows)</span><span class="sxs-lookup"><span data-stu-id="4d170-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="4d170-164">顯示診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="4d170-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="4d170-165">印出指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="4d170-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="4d170-166">範例</span><span class="sxs-lookup"><span data-stu-id="4d170-166">Examples</span></span>

<span data-ttu-id="4d170-167">將最新的長期支援 (LTS) 版本安裝至預設位置︰</span><span class="sxs-lookup"><span data-stu-id="4d170-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="4d170-168">Windows：</span><span class="sxs-lookup"><span data-stu-id="4d170-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="4d170-169">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="4d170-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="4d170-170">將來自 2.0 通道的最新版本安裝至指定的位置︰</span><span class="sxs-lookup"><span data-stu-id="4d170-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="4d170-171">Windows：</span><span class="sxs-lookup"><span data-stu-id="4d170-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="4d170-172">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="4d170-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="4d170-173">安裝共用執行階段 1.1.0 版本：</span><span class="sxs-lookup"><span data-stu-id="4d170-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="4d170-174">Windows：</span><span class="sxs-lookup"><span data-stu-id="4d170-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="4d170-175">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="4d170-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="4d170-176">取得指令碼並安裝 .NET Core CLI 單行範例：</span><span class="sxs-lookup"><span data-stu-id="4d170-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="4d170-177">Windows：</span><span class="sxs-lookup"><span data-stu-id="4d170-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="4d170-178">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="4d170-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="4d170-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d170-179">See also</span></span>

<span data-ttu-id="4d170-180">[.NET Core 版本](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="4d170-180">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="4d170-181">.NET Core 執行階段和 SDK 下載封存</span><span class="sxs-lookup"><span data-stu-id="4d170-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
