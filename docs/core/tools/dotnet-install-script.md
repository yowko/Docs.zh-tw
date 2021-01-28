---
title: dotnet-install 指令碼
description: 瞭解安裝 .NET SDK 和共用執行時間的 dotnet 安裝腳本。
ms.date: 09/22/2020
ms.openlocfilehash: 1904d0322774de25aeba7e7a53ab36ce135d685d
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957869"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="463b4-103">dotnet-install 指令碼參考</span><span class="sxs-lookup"><span data-stu-id="463b4-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="463b4-104">Name</span><span class="sxs-lookup"><span data-stu-id="463b4-104">Name</span></span>

<span data-ttu-id="463b4-105">`dotnet-install.ps1` | `dotnet-install.sh` -用來安裝 .NET SDK 和共用執行時間的腳本。</span><span class="sxs-lookup"><span data-stu-id="463b4-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="463b4-106">概要</span><span class="sxs-lookup"><span data-stu-id="463b4-106">Synopsis</span></span>

<span data-ttu-id="463b4-107">Windows：</span><span class="sxs-lookup"><span data-stu-id="463b4-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="463b4-108">Linux/macOS：</span><span class="sxs-lookup"><span data-stu-id="463b4-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="463b4-109">Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。</span><span class="sxs-lookup"><span data-stu-id="463b4-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="463b4-110">Description</span><span class="sxs-lookup"><span data-stu-id="463b4-110">Description</span></span>

<span data-ttu-id="463b4-111">`dotnet-install`腳本會執行 .NET SDK 的非系統管理員安裝，其中包含 .NET CLI 和共用執行時間。</span><span class="sxs-lookup"><span data-stu-id="463b4-111">The `dotnet-install` scripts perform a non-admin installation of the .NET SDK, which includes the .NET CLI and the shared runtime.</span></span> <span data-ttu-id="463b4-112">有兩個腳本：</span><span class="sxs-lookup"><span data-stu-id="463b4-112">There are two scripts:</span></span>

* <span data-ttu-id="463b4-113">適用于 Windows 的 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="463b4-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="463b4-114">在 Linux/macOS 上運作的 bash 腳本。</span><span class="sxs-lookup"><span data-stu-id="463b4-114">A bash script that works on Linux/macOS.</span></span>

### <a name="purpose"></a><span data-ttu-id="463b4-115">目的</span><span class="sxs-lookup"><span data-stu-id="463b4-115">Purpose</span></span>

 <span data-ttu-id="463b4-116">腳本的預期用途是持續整合 (CI) 案例，其中：</span><span class="sxs-lookup"><span data-stu-id="463b4-116">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="463b4-117">您必須在不需使用者互動的情況下安裝 SDK，而且不需要系統管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="463b4-117">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="463b4-118">SDK 安裝不需要跨多個 CI 執行來保存。</span><span class="sxs-lookup"><span data-stu-id="463b4-118">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="463b4-119">一般的事件順序：</span><span class="sxs-lookup"><span data-stu-id="463b4-119">The typical sequence of events:</span></span>
  * <span data-ttu-id="463b4-120">觸發 CI。</span><span class="sxs-lookup"><span data-stu-id="463b4-120">CI is triggered.</span></span>
  * <span data-ttu-id="463b4-121">CI 會使用其中一個腳本來安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="463b4-121">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="463b4-122">CI 完成其工作，並清除包含 SDK 安裝的暫存資料。</span><span class="sxs-lookup"><span data-stu-id="463b4-122">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="463b4-123">若要設定開發環境或執行應用程式，請使用安裝程式，而不是這些腳本。</span><span class="sxs-lookup"><span data-stu-id="463b4-123">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="463b4-124">建議的版本</span><span class="sxs-lookup"><span data-stu-id="463b4-124">Recommended version</span></span>

<span data-ttu-id="463b4-125">建議您使用穩定版本的腳本：</span><span class="sxs-lookup"><span data-stu-id="463b4-125">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="463b4-126">Bash (Linux/macOS) ： <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="463b4-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="463b4-127">PowerShell (Windows)：<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="463b4-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="463b4-128">腳本行為</span><span class="sxs-lookup"><span data-stu-id="463b4-128">Script behavior</span></span>

<span data-ttu-id="463b4-129">這兩個指令碼有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="463b4-129">Both scripts have the same behavior.</span></span> <span data-ttu-id="463b4-130">他們會從 CLI 組建放置下載 ZIP/tarball 檔案，並繼續將它安裝在預設位置或指定的位置 `-InstallDir|--install-dir` 。</span><span class="sxs-lookup"><span data-stu-id="463b4-130">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="463b4-131">根據預設，安裝指令碼會下載並安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="463b4-131">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="463b4-132">如果您想要只取得共用執行階段，請指定 `-Runtime|--runtime` 引數。</span><span class="sxs-lookup"><span data-stu-id="463b4-132">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="463b4-133">根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。</span><span class="sxs-lookup"><span data-stu-id="463b4-133">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="463b4-134">指定 `-NoPath|--no-path` 引數可以覆寫此預設行為。</span><span class="sxs-lookup"><span data-stu-id="463b4-134">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="463b4-135">腳本不會設定 `DOTNET_ROOT` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="463b4-135">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="463b4-136">執行指令碼之前，請安裝所有必要的[相依性 (英文)](../install/windows.md#dependencies)。</span><span class="sxs-lookup"><span data-stu-id="463b4-136">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="463b4-137">您可以使用 `-Version|--version` 引數安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="463b4-137">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="463b4-138">版本必須指定為三部分的版本號碼，例如 `2.1.0` 。</span><span class="sxs-lookup"><span data-stu-id="463b4-138">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="463b4-139">如果未指定版本，腳本會安裝 `latest` 版本。</span><span class="sxs-lookup"><span data-stu-id="463b4-139">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="463b4-140">安裝腳本不會更新 Windows 上的登錄。</span><span class="sxs-lookup"><span data-stu-id="463b4-140">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="463b4-141">他們只會下載壓縮的二進位檔，並將其複製到資料夾。</span><span class="sxs-lookup"><span data-stu-id="463b4-141">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="463b4-142">如果您想要更新登錄機碼值，請使用 .NET 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="463b4-142">If you want registry key values to be updated, use the .NET installers.</span></span>

## <a name="options"></a><span data-ttu-id="463b4-143">選項</span><span class="sxs-lookup"><span data-stu-id="463b4-143">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="463b4-144">要安裝的 .NET 二進位檔架構。</span><span class="sxs-lookup"><span data-stu-id="463b4-144">Architecture of the .NET binaries to install.</span></span> <span data-ttu-id="463b4-145">可能的值為 `<auto>`、`amd64`、`x64`、`x86`、`arm64` 和 `arm`。</span><span class="sxs-lookup"><span data-stu-id="463b4-145">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="463b4-146">預設值為 `<auto>`，代表目前正在執行的 OS 架構。</span><span class="sxs-lookup"><span data-stu-id="463b4-146">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="463b4-147">指定給安裝程式的 Azure 摘要 URL。</span><span class="sxs-lookup"><span data-stu-id="463b4-147">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="463b4-148">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="463b4-148">We recommended that you don't change this value.</span></span> <span data-ttu-id="463b4-149">預設值是 `https://dotnetcli.azureedge.net/dotnet`。</span><span class="sxs-lookup"><span data-stu-id="463b4-149">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="463b4-150">指定安裝的來源通道。</span><span class="sxs-lookup"><span data-stu-id="463b4-150">Specifies the source channel for the installation.</span></span> <span data-ttu-id="463b4-151">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="463b4-151">The possible values are:</span></span>

  - <span data-ttu-id="463b4-152">`Current` - 最新版本。</span><span class="sxs-lookup"><span data-stu-id="463b4-152">`Current` - Most current release.</span></span>
  - <span data-ttu-id="463b4-153">`LTS` - 長期支援通道 (最新的支援版本)。</span><span class="sxs-lookup"><span data-stu-id="463b4-153">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="463b4-154">代表特定版本的 X.Y 格式兩段式版本 (例如 `2.1` 或 `3.0`)。</span><span class="sxs-lookup"><span data-stu-id="463b4-154">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="463b4-155">分支名稱：例如， `release/3.1.1xx` 或 `master` (用於夜間發行) 。</span><span class="sxs-lookup"><span data-stu-id="463b4-155">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="463b4-156">使用這個選項可從預覽通道安裝版本。</span><span class="sxs-lookup"><span data-stu-id="463b4-156">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="463b4-157">使用 [安裝程式和二進位](https://github.com/dotnet/core-sdk#installers-and-binaries)檔中所列的通道名稱。</span><span class="sxs-lookup"><span data-stu-id="463b4-157">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="463b4-158">預設值是 `LTS`。</span><span class="sxs-lookup"><span data-stu-id="463b4-158">The default value is `LTS`.</span></span> <span data-ttu-id="463b4-159">如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援政策](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) \(英文\) 頁面。</span><span class="sxs-lookup"><span data-stu-id="463b4-159">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="463b4-160">如果設定，指令碼將不會執行安裝。</span><span class="sxs-lookup"><span data-stu-id="463b4-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="463b4-161">相反地，它會顯示要用來一致安裝目前要求的 .NET CLI 版本的命令列。</span><span class="sxs-lookup"><span data-stu-id="463b4-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET CLI.</span></span> <span data-ttu-id="463b4-162">例如，如果您指定 `latest` 版本，就會顯示特定版本的連結，以便在建置指令碼中以決定性方式使用此命令。</span><span class="sxs-lookup"><span data-stu-id="463b4-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="463b4-163">如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。</span><span class="sxs-lookup"><span data-stu-id="463b4-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="463b4-164">用來作為要附加至 Azure 摘要的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="463b4-164">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="463b4-165">這可允許變更 URL 以使用非公用 Blob 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="463b4-165">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="463b4-166">印出指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="463b4-166">Prints out help for the script.</span></span> <span data-ttu-id="463b4-167">只適用于 bash 腳本。</span><span class="sxs-lookup"><span data-stu-id="463b4-167">Applies only to bash script.</span></span> <span data-ttu-id="463b4-168">針對 PowerShell，請使用 `Get-Help ./dotnet-install.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="463b4-168">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="463b4-169">指定安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="463b4-169">Specifies the installation path.</span></span> <span data-ttu-id="463b4-170">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="463b4-170">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="463b4-171">預設值為 Windows 上的 *%LocalAppData%\Microsoft\dotnet* ，以及 Linux/macOS 上的 */usr/share/dotnet* 。</span><span class="sxs-lookup"><span data-stu-id="463b4-171">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="463b4-172">二進位檔會直接放在此目錄中。</span><span class="sxs-lookup"><span data-stu-id="463b4-172">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="463b4-173">指定將用來判斷 SDK 版本之檔案 [global.js](global-json.md) 的路徑。</span><span class="sxs-lookup"><span data-stu-id="463b4-173">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="463b4-174">檔案 *上的global.js* 必須有的值 `sdk:version` 。</span><span class="sxs-lookup"><span data-stu-id="463b4-174">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="463b4-175">不允許從 [Azure 內容傳遞網路 (CDN)](/azure/cdn/cdn-overview) 下載，而直接使用未快取的摘要。</span><span class="sxs-lookup"><span data-stu-id="463b4-175">Disables downloading from the [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="463b4-176">如果設定，就不會將安裝資料夾匯出至目前工作階段的路徑。</span><span class="sxs-lookup"><span data-stu-id="463b4-176">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="463b4-177">根據預設，腳本會修改路徑，讓 .NET CLI 在安裝後立即可供使用。</span><span class="sxs-lookup"><span data-stu-id="463b4-177">By default, the script modifies the PATH, which makes the .NET CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="463b4-178">如果設定，安裝程式會使用此 Proxy 進行 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="463b4-178">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="463b4-179"> (僅適用于 Windows。 ) </span><span class="sxs-lookup"><span data-stu-id="463b4-179">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="463b4-180">如果設定為 `ProxyAddress` ，則會提供略過 proxy 的逗點分隔 url 清單。</span><span class="sxs-lookup"><span data-stu-id="463b4-180">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="463b4-181"> (僅適用于 Windows。 ) </span><span class="sxs-lookup"><span data-stu-id="463b4-181">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="463b4-182">如果設定，當使用 Proxy 位址時，安裝程式會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="463b4-182">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="463b4-183"> (僅適用于 Windows。 ) </span><span class="sxs-lookup"><span data-stu-id="463b4-183">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="463b4-184">只安裝共用執行階段，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="463b4-184">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="463b4-185">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="463b4-185">The possible values are:</span></span>

  - <span data-ttu-id="463b4-186">`dotnet` - `Microsoft.NETCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="463b4-186">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="463b4-187">`aspnetcore` - `Microsoft.AspNetCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="463b4-187">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="463b4-188">`windowsdesktop` - `Microsoft.WindowsDesktop.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="463b4-188">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- <span data-ttu-id="463b4-189">**`--runtime-id <RID>` 否決**</span><span class="sxs-lookup"><span data-stu-id="463b4-189">**`--runtime-id <RID>` [Deprecated]**</span></span>

  <span data-ttu-id="463b4-190">指定要安裝工具的 [執行時間識別碼](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="463b4-190">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="463b4-191">用於 `linux-x64` 可移植的 Linux。</span><span class="sxs-lookup"><span data-stu-id="463b4-191">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="463b4-192"> (僅適用于 Linux/macOS 和 .NET Core 2.1 之前的版本。 ) </span><span class="sxs-lookup"><span data-stu-id="463b4-192">(Only valid for Linux/macOS and for versions earlier than .NET Core 2.1.)</span></span>

  **`--os <OPERATING_SYSTEM>`**

  <span data-ttu-id="463b4-193">指定要安裝工具的作業系統。</span><span class="sxs-lookup"><span data-stu-id="463b4-193">Specifies the operating system for which the tools are being installed.</span></span> <span data-ttu-id="463b4-194">可能的值為： `osx` 、 `linux` 、 `linux-musl` 、 `freebsd` 、 `rhel.6` 。</span><span class="sxs-lookup"><span data-stu-id="463b4-194">Possible values are: `osx`, `linux`, `linux-musl`, `freebsd`, `rhel.6`.</span></span> <span data-ttu-id="463b4-195"> (適用于 .NET Core 2.1 和更新版本。 ) </span><span class="sxs-lookup"><span data-stu-id="463b4-195">(Valid for .NET Core 2.1 and later.)</span></span>

  <span data-ttu-id="463b4-196">參數是選擇性的，只有在需要覆寫腳本所偵測到的作業系統時，才應使用此參數。</span><span class="sxs-lookup"><span data-stu-id="463b4-196">The parameter is optional and should only be used when it's required to override the operating system that is detected by the script.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="463b4-197">此參數已被淘汰，在未來的指令碼版本中可能會將其移除。</span><span class="sxs-lookup"><span data-stu-id="463b4-197">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="463b4-198">建議的替代方案是 `-Runtime|--runtime` 選項。</span><span class="sxs-lookup"><span data-stu-id="463b4-198">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="463b4-199">只安裝共用執行階段位元，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="463b4-199">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="463b4-200">此選項相當於指定 `-Runtime|--runtime dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="463b4-200">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="463b4-201">如果已經有非版本控制的檔案 (例如 *dotnet.exe*) 存在，便略過其安裝。</span><span class="sxs-lookup"><span data-stu-id="463b4-201">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="463b4-202">允許變更此安裝程式所使用之未快取摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="463b4-202">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="463b4-203">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="463b4-203">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="463b4-204">顯示診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="463b4-204">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="463b4-205">代表特定的組建版本。</span><span class="sxs-lookup"><span data-stu-id="463b4-205">Represents a specific build version.</span></span> <span data-ttu-id="463b4-206">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="463b4-206">The possible values are:</span></span>

  - <span data-ttu-id="463b4-207">`latest` - 通道上的最新組建 (與 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="463b4-207">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="463b4-208">代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。</span><span class="sxs-lookup"><span data-stu-id="463b4-208">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="463b4-209">例如：`2.0.0-preview2-006120`。</span><span class="sxs-lookup"><span data-stu-id="463b4-209">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="463b4-210">如果未指定，`-Version` 會預設為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="463b4-210">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="463b4-211">範例</span><span class="sxs-lookup"><span data-stu-id="463b4-211">Examples</span></span>

- <span data-ttu-id="463b4-212">將最新的長期支援 (LTS) 版本安裝至預設位置︰</span><span class="sxs-lookup"><span data-stu-id="463b4-212">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="463b4-213">Windows：</span><span class="sxs-lookup"><span data-stu-id="463b4-213">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="463b4-214">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="463b4-214">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="463b4-215">將最新版本從3.1 通道安裝至指定的位置：</span><span class="sxs-lookup"><span data-stu-id="463b4-215">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="463b4-216">Windows：</span><span class="sxs-lookup"><span data-stu-id="463b4-216">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="463b4-217">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="463b4-217">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="463b4-218">安裝共用執行時間的3.0.0 版本：</span><span class="sxs-lookup"><span data-stu-id="463b4-218">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="463b4-219">Windows：</span><span class="sxs-lookup"><span data-stu-id="463b4-219">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="463b4-220">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="463b4-220">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="463b4-221">取得指令碼並在公司 Proxy 後方安裝 2.1.2 版本 (僅適用於 Windows)：</span><span class="sxs-lookup"><span data-stu-id="463b4-221">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="463b4-222">取得腳本並安裝 .NET CLI 的單行指令範例：</span><span class="sxs-lookup"><span data-stu-id="463b4-222">Obtain script and install .NET CLI one-liner examples:</span></span>

  <span data-ttu-id="463b4-223">Windows：</span><span class="sxs-lookup"><span data-stu-id="463b4-223">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="463b4-224">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="463b4-224">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="463b4-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="463b4-225">See also</span></span>

- [<span data-ttu-id="463b4-226">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="463b4-226">.NET releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="463b4-227">.NET 執行時間和 SDK 下載封存</span><span class="sxs-lookup"><span data-stu-id="463b4-227">.NET Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
