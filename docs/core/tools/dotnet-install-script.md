---
title: dotnet-install 指令碼
description: 瞭解安裝 .NET Core SDK 和共用執行時間的 dotnet-安裝腳本。
ms.date: 04/30/2020
ms.openlocfilehash: 464e6fafa1c2e661892bcb3b35ba172ca1d7e76b
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141239"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="7c351-103">dotnet-install 指令碼參考</span><span class="sxs-lookup"><span data-stu-id="7c351-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="7c351-104">名稱</span><span class="sxs-lookup"><span data-stu-id="7c351-104">Name</span></span>

<span data-ttu-id="7c351-105">`dotnet-install.ps1` | `dotnet-install.sh`-用來安裝 .NET Core SDK 和共用執行時間的腳本。</span><span class="sxs-lookup"><span data-stu-id="7c351-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7c351-106">概要</span><span class="sxs-lookup"><span data-stu-id="7c351-106">Synopsis</span></span>

<span data-ttu-id="7c351-107">Windows：</span><span class="sxs-lookup"><span data-stu-id="7c351-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="7c351-108">Linux/macOS：</span><span class="sxs-lookup"><span data-stu-id="7c351-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="7c351-109">描述</span><span class="sxs-lookup"><span data-stu-id="7c351-109">Description</span></span>

<span data-ttu-id="7c351-110">這些 `dotnet-install` 腳本是用來執行 .NET Core SDK 的非系統管理員安裝，其中包括 .NET Core CLI 和共用執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c351-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="7c351-111">建議您使用穩定版本的腳本：</span><span class="sxs-lookup"><span data-stu-id="7c351-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="7c351-112">Bash （Linux/macOS）：<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="7c351-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="7c351-113">PowerShell （Windows）：<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="7c351-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="7c351-114">這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="7c351-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="7c351-115">有兩個指令碼：一個是在 Windows 上運作的 PowerShell 指令碼，另一個是在 Linux/macOS 上運作的 Bash 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7c351-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="7c351-116">這兩個指令碼有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="7c351-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="7c351-117">Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7c351-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="7c351-118">安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="7c351-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="7c351-119">根據預設，安裝指令碼會下載並安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="7c351-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="7c351-120">如果您想要只取得共用執行階段，請指定 `-Runtime|--runtime` 引數。</span><span class="sxs-lookup"><span data-stu-id="7c351-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="7c351-121">根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。</span><span class="sxs-lookup"><span data-stu-id="7c351-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="7c351-122">指定 `-NoPath|--no-path` 引數可以覆寫此預設行為。</span><span class="sxs-lookup"><span data-stu-id="7c351-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="7c351-123">執行指令碼之前，請安裝所有必要的[相依性 (英文)](../install/dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="7c351-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="7c351-124">您可以使用 `-Version|--version` 引數安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="7c351-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="7c351-125">版本必須指定為三部分版本（例如 `2.1.0` ）。</span><span class="sxs-lookup"><span data-stu-id="7c351-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="7c351-126">如果未提供，就會使用 `latest` 版本。</span><span class="sxs-lookup"><span data-stu-id="7c351-126">If not provided, it uses the `latest` version.</span></span>

<span data-ttu-id="7c351-127">安裝腳本不會更新 Windows 上的登錄。</span><span class="sxs-lookup"><span data-stu-id="7c351-127">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="7c351-128">他們只需要下載壓縮的二進位檔，並將它們複製到資料夾即可。</span><span class="sxs-lookup"><span data-stu-id="7c351-128">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="7c351-129">如果您想要更新登錄機碼值，請使用 .NET Core 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="7c351-129">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="7c351-130">選項</span><span class="sxs-lookup"><span data-stu-id="7c351-130">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="7c351-131">要安裝的 .NET Core 二進位檔的架構。</span><span class="sxs-lookup"><span data-stu-id="7c351-131">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="7c351-132">可能的值為 `<auto>`、`amd64`、`x64`、`x86`、`arm64` 和 `arm`。</span><span class="sxs-lookup"><span data-stu-id="7c351-132">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="7c351-133">預設值為 `<auto>`，代表目前正在執行的 OS 架構。</span><span class="sxs-lookup"><span data-stu-id="7c351-133">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="7c351-134">指定給安裝程式的 Azure 摘要 URL。</span><span class="sxs-lookup"><span data-stu-id="7c351-134">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="7c351-135">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="7c351-135">We recommended that you don't change this value.</span></span> <span data-ttu-id="7c351-136">預設值是 `https://dotnetcli.azureedge.net/dotnet`。</span><span class="sxs-lookup"><span data-stu-id="7c351-136">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="7c351-137">指定安裝的來源通道。</span><span class="sxs-lookup"><span data-stu-id="7c351-137">Specifies the source channel for the installation.</span></span> <span data-ttu-id="7c351-138">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7c351-138">The possible values are:</span></span>

  - <span data-ttu-id="7c351-139">`Current` - 最新版本。</span><span class="sxs-lookup"><span data-stu-id="7c351-139">`Current` - Most current release.</span></span>
  - <span data-ttu-id="7c351-140">`LTS` - 長期支援通道 (最新的支援版本)。</span><span class="sxs-lookup"><span data-stu-id="7c351-140">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="7c351-141">代表特定版本的 X.Y 格式兩段式版本 (例如 `2.1` 或 `3.0`)。</span><span class="sxs-lookup"><span data-stu-id="7c351-141">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="7c351-142">分支名稱：例如， `release/3.1.1xx` 或 `master` （針對夜間版本）。</span><span class="sxs-lookup"><span data-stu-id="7c351-142">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="7c351-143">使用此選項可從預覽頻道安裝版本。</span><span class="sxs-lookup"><span data-stu-id="7c351-143">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="7c351-144">使用[安裝程式和二進位](https://github.com/dotnet/core-sdk#installers-and-binaries)檔中列出的通道名稱。</span><span class="sxs-lookup"><span data-stu-id="7c351-144">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="7c351-145">預設值是 `LTS`。</span><span class="sxs-lookup"><span data-stu-id="7c351-145">The default value is `LTS`.</span></span> <span data-ttu-id="7c351-146">如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援政策](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) \(英文\) 頁面。</span><span class="sxs-lookup"><span data-stu-id="7c351-146">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="7c351-147">如果設定，指令碼將不會執行安裝。</span><span class="sxs-lookup"><span data-stu-id="7c351-147">If set, the script won't perform the installation.</span></span> <span data-ttu-id="7c351-148">取而代之的是，會顯示以一致方式安裝目前所要求的 .NET Core CLI 版本時，所要使用的命令列。</span><span class="sxs-lookup"><span data-stu-id="7c351-148">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="7c351-149">例如，如果您指定 `latest` 版本，就會顯示特定版本的連結，以便在建置指令碼中以決定性方式使用此命令。</span><span class="sxs-lookup"><span data-stu-id="7c351-149">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="7c351-150">如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。</span><span class="sxs-lookup"><span data-stu-id="7c351-150">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="7c351-151">用來作為要附加至 Azure 摘要的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="7c351-151">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="7c351-152">這可允許變更 URL 以使用非公用 Blob 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="7c351-152">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="7c351-153">印出指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="7c351-153">Prints out help for the script.</span></span> <span data-ttu-id="7c351-154">僅適用于 bash 腳本。</span><span class="sxs-lookup"><span data-stu-id="7c351-154">Applies only to bash script.</span></span> <span data-ttu-id="7c351-155">針對 PowerShell，請使用 `Get-Help ./dotnet-install.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="7c351-155">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="7c351-156">指定安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="7c351-156">Specifies the installation path.</span></span> <span data-ttu-id="7c351-157">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="7c351-157">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="7c351-158">預設值是在 Windows 上 *%LocalAppData%\Microsoft\dotnet* ，而在 Linux/macOS 上則是 */usr/share/dotnet* 。</span><span class="sxs-lookup"><span data-stu-id="7c351-158">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="7c351-159">二進位檔會直接放在此目錄中。</span><span class="sxs-lookup"><span data-stu-id="7c351-159">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="7c351-160">指定將用來判斷 SDK 版本之檔案的[global.js](global-json.md)路徑。</span><span class="sxs-lookup"><span data-stu-id="7c351-160">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="7c351-161">檔案*上的global.js*必須有的值 `sdk:version` 。</span><span class="sxs-lookup"><span data-stu-id="7c351-161">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="7c351-162">不允許從 [Azure 內容傳遞網路 (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) 下載，而直接使用未快取的摘要。</span><span class="sxs-lookup"><span data-stu-id="7c351-162">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="7c351-163">如果設定，就不會將安裝資料夾匯出至目前工作階段的路徑。</span><span class="sxs-lookup"><span data-stu-id="7c351-163">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="7c351-164">根據預設，腳本會修改路徑，使 .NET Core CLI 在安裝後立即可供使用。</span><span class="sxs-lookup"><span data-stu-id="7c351-164">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="7c351-165">如果設定，安裝程式會使用此 Proxy 進行 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="7c351-165">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="7c351-166">（僅適用于 Windows。）</span><span class="sxs-lookup"><span data-stu-id="7c351-166">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="7c351-167">如果設定，當使用 Proxy 位址時，安裝程式會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="7c351-167">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="7c351-168">（僅適用于 Windows。）</span><span class="sxs-lookup"><span data-stu-id="7c351-168">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="7c351-169">只安裝共用執行階段，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="7c351-169">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="7c351-170">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7c351-170">The possible values are:</span></span>

  - <span data-ttu-id="7c351-171">`dotnet` - `Microsoft.NETCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="7c351-171">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="7c351-172">`aspnetcore` - `Microsoft.AspNetCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="7c351-172">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="7c351-173">`windowsdesktop` - `Microsoft.WindowsDesktop.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="7c351-173">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="7c351-174">指定要安裝工具的[執行時間識別碼](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="7c351-174">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="7c351-175">用於 `linux-x64` 可移植的 Linux。</span><span class="sxs-lookup"><span data-stu-id="7c351-175">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="7c351-176">（僅適用于 Linux/macOS）。</span><span class="sxs-lookup"><span data-stu-id="7c351-176">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="7c351-177">此參數已被淘汰，在未來的指令碼版本中可能會將其移除。</span><span class="sxs-lookup"><span data-stu-id="7c351-177">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="7c351-178">建議的替代方案是 `-Runtime|--runtime` 選項。</span><span class="sxs-lookup"><span data-stu-id="7c351-178">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="7c351-179">只安裝共用執行階段位元，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="7c351-179">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="7c351-180">此選項相當於指定 `-Runtime|--runtime dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="7c351-180">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="7c351-181">如果已經有非版本控制的檔案 (例如 *dotnet.exe*) 存在，便略過其安裝。</span><span class="sxs-lookup"><span data-stu-id="7c351-181">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="7c351-182">允許變更此安裝程式所使用之未快取摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="7c351-182">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="7c351-183">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="7c351-183">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="7c351-184">顯示診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="7c351-184">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="7c351-185">代表特定的組建版本。</span><span class="sxs-lookup"><span data-stu-id="7c351-185">Represents a specific build version.</span></span> <span data-ttu-id="7c351-186">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7c351-186">The possible values are:</span></span>

  - <span data-ttu-id="7c351-187">`latest` - 通道上的最新組建 (與 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="7c351-187">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="7c351-188">`coherent` - 通道上的最新一致性組建；使用最新的穩定套件組合 (與分支名稱 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="7c351-188">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="7c351-189">代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。</span><span class="sxs-lookup"><span data-stu-id="7c351-189">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="7c351-190">例如： `2.0.0-preview2-006120` 。</span><span class="sxs-lookup"><span data-stu-id="7c351-190">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="7c351-191">如果未指定，`-Version` 會預設為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="7c351-191">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="7c351-192">範例</span><span class="sxs-lookup"><span data-stu-id="7c351-192">Examples</span></span>

- <span data-ttu-id="7c351-193">將最新的長期支援 (LTS) 版本安裝至預設位置︰</span><span class="sxs-lookup"><span data-stu-id="7c351-193">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="7c351-194">Windows：</span><span class="sxs-lookup"><span data-stu-id="7c351-194">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="7c351-195">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="7c351-195">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="7c351-196">將3.1 通道的最新版本安裝至指定的位置：</span><span class="sxs-lookup"><span data-stu-id="7c351-196">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="7c351-197">Windows：</span><span class="sxs-lookup"><span data-stu-id="7c351-197">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="7c351-198">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="7c351-198">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="7c351-199">安裝共用執行時間的3.0.0 版本：</span><span class="sxs-lookup"><span data-stu-id="7c351-199">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="7c351-200">Windows：</span><span class="sxs-lookup"><span data-stu-id="7c351-200">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="7c351-201">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="7c351-201">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="7c351-202">取得指令碼並在公司 Proxy 後方安裝 2.1.2 版本 (僅適用於 Windows)：</span><span class="sxs-lookup"><span data-stu-id="7c351-202">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="7c351-203">取得指令碼並安裝 .NET Core CLI 單行範例：</span><span class="sxs-lookup"><span data-stu-id="7c351-203">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="7c351-204">Windows：</span><span class="sxs-lookup"><span data-stu-id="7c351-204">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="7c351-205">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="7c351-205">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="7c351-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c351-206">See also</span></span>

- [<span data-ttu-id="7c351-207">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="7c351-207">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="7c351-208">.NET Core 執行階段和 SDK 下載封存</span><span class="sxs-lookup"><span data-stu-id="7c351-208">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
