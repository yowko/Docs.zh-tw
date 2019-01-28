---
title: dotnet-install 指令碼
description: 了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。
ms.date: 01/16/2019
ms.openlocfilehash: f796ac494c0be5458b3ea192e809a4d875bcc6dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608783"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="8d08e-103">dotnet-install 指令碼參考</span><span class="sxs-lookup"><span data-stu-id="8d08e-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="8d08e-104">名稱</span><span class="sxs-lookup"><span data-stu-id="8d08e-104">Name</span></span>

<span data-ttu-id="8d08e-105">`dotnet-install.ps1` | `dotnet-install.sh` - 用來安裝 .NET Core CLI 工具和共用執行階段的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8d08e-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8d08e-106">概要</span><span class="sxs-lookup"><span data-stu-id="8d08e-106">Synopsis</span></span>

<span data-ttu-id="8d08e-107">Windows：</span><span class="sxs-lookup"><span data-stu-id="8d08e-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="8d08e-108">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="8d08e-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="8d08e-109">說明</span><span class="sxs-lookup"><span data-stu-id="8d08e-109">Description</span></span>

<span data-ttu-id="8d08e-110">`dotnet-install` 指令碼可用來執行 .NET Core SDK 的非系統管理安裝，其中包含了 .NET Core CLI 工具和共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="8d08e-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="8d08e-111">建議您使用 [.NET Core 主網站](https://dot.net) \(英文\) 所提供的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="8d08e-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="8d08e-112">指令碼的直接路徑如下：</span><span class="sxs-lookup"><span data-stu-id="8d08e-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="8d08e-113"><https://dot.net/v1/dotnet-install.sh> (bash、UNIX)</span><span class="sxs-lookup"><span data-stu-id="8d08e-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
* <span data-ttu-id="8d08e-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell、Windows)</span><span class="sxs-lookup"><span data-stu-id="8d08e-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="8d08e-115">這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="8d08e-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="8d08e-116">有兩個指令碼：一個是在 Windows 上運作的 PowerShell 指令碼，另一個是在 Linux/macOS 上運作的 Bash 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8d08e-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="8d08e-117">這兩個指令碼有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="8d08e-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="8d08e-118">Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8d08e-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="8d08e-119">安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="8d08e-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="8d08e-120">根據預設，安裝指令碼會下載並安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="8d08e-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="8d08e-121">如果您想要只取得共用執行階段，請指定 `--shared-runtime` 引數。</span><span class="sxs-lookup"><span data-stu-id="8d08e-121">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="8d08e-122">根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。</span><span class="sxs-lookup"><span data-stu-id="8d08e-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="8d08e-123">指定 `--no-path` 引數可以覆寫此預設行為。</span><span class="sxs-lookup"><span data-stu-id="8d08e-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="8d08e-124">執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="8d08e-125">您可以使用 `--version` 引數安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="8d08e-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="8d08e-126">指定版本時，必須以三段式版本格式指定 (例如 1.0.0-13232)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="8d08e-127">如果未提供，就會使用 `latest` 版本。</span><span class="sxs-lookup"><span data-stu-id="8d08e-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="8d08e-128">選項</span><span class="sxs-lookup"><span data-stu-id="8d08e-128">Options</span></span>

* **`-Channel <CHANNEL>`**

  <span data-ttu-id="8d08e-129">指定安裝的來源通道。</span><span class="sxs-lookup"><span data-stu-id="8d08e-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="8d08e-130">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d08e-130">The possible values are:</span></span>

  * <span data-ttu-id="8d08e-131">`Current` - 最新版本。</span><span class="sxs-lookup"><span data-stu-id="8d08e-131">`Current` - Most current release.</span></span>
  * <span data-ttu-id="8d08e-132">`LTS` - 長期支援通道 (最新的支援版本)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  * <span data-ttu-id="8d08e-133">代表特定版本的 X.Y 格式兩段式版本 (例如 `2.0` 或 `1.0`)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  * <span data-ttu-id="8d08e-134">分支名稱。</span><span class="sxs-lookup"><span data-stu-id="8d08e-134">Branch name.</span></span> <span data-ttu-id="8d08e-135">例如 `release/2.0.0`、`release/2.0.0-preview2` 或 `master` (適用於夜間版本)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="8d08e-136">預設值為 `LTS`。</span><span class="sxs-lookup"><span data-stu-id="8d08e-136">The default value is `LTS`.</span></span> <span data-ttu-id="8d08e-137">如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援政策](https://www.microsoft.com/net/platform/support-policy#dotnet-core) \(英文\) 頁面。</span><span class="sxs-lookup"><span data-stu-id="8d08e-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

* **`-Version <VERSION>`**

  <span data-ttu-id="8d08e-138">代表特定的組建版本。</span><span class="sxs-lookup"><span data-stu-id="8d08e-138">Represents a specific build version.</span></span> <span data-ttu-id="8d08e-139">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d08e-139">The possible values are:</span></span>

  * <span data-ttu-id="8d08e-140">`latest` - 通道上的最新組建 (與 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  * <span data-ttu-id="8d08e-141">`coherent` - 通道上的最新一致性組建；使用最新的穩定套件組合 (與分支名稱 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="8d08e-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  * <span data-ttu-id="8d08e-142">代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。</span><span class="sxs-lookup"><span data-stu-id="8d08e-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="8d08e-143">例如：`2.0.0-preview2-006120`。</span><span class="sxs-lookup"><span data-stu-id="8d08e-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="8d08e-144">如果未指定，`-Version` 會預設為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="8d08e-144">If not specified, `-Version` defaults to `latest`.</span></span>

* **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="8d08e-145">指定安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="8d08e-145">Specifies the installation path.</span></span> <span data-ttu-id="8d08e-146">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="8d08e-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="8d08e-147">預設值是 *%LocalAppData%\Microsoft\dotnet*。</span><span class="sxs-lookup"><span data-stu-id="8d08e-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="8d08e-148">二進位檔會直接放在此目錄中。</span><span class="sxs-lookup"><span data-stu-id="8d08e-148">Binaries are placed directly in this directory.</span></span>

* **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="8d08e-149">要安裝的 .NET Core 二進位檔的架構。</span><span class="sxs-lookup"><span data-stu-id="8d08e-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="8d08e-150">可能的值為 `<auto>`、`amd64`、`x64`、`x86`、`arm64` 和 `arm`。</span><span class="sxs-lookup"><span data-stu-id="8d08e-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="8d08e-151">預設值為 `<auto>`，代表目前正在執行的 OS 架構。</span><span class="sxs-lookup"><span data-stu-id="8d08e-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

* **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="8d08e-152">此參數已被淘汰，在未來的指令碼版本中可能會將其移除。</span><span class="sxs-lookup"><span data-stu-id="8d08e-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="8d08e-153">建議的替代方案是 `Runtime` 選項。</span><span class="sxs-lookup"><span data-stu-id="8d08e-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="8d08e-154">只安裝共用執行階段位元，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="8d08e-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="8d08e-155">這相當於指定 `-Runtime dotnet`。</span><span class="sxs-lookup"><span data-stu-id="8d08e-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

* **`-Runtime <RUNTIME>`**

  <span data-ttu-id="8d08e-156">只安裝共用執行階段，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="8d08e-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="8d08e-157">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d08e-157">The possible values are:</span></span>

  * <span data-ttu-id="8d08e-158">`dotnet` - `Microsoft.NETCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="8d08e-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  * <span data-ttu-id="8d08e-159">`aspnetcore` - `Microsoft.AspNetCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="8d08e-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

* **`-DryRun`**

  <span data-ttu-id="8d08e-160">如果設定，指令碼將不會執行安裝。</span><span class="sxs-lookup"><span data-stu-id="8d08e-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="8d08e-161">取而代之的是，會顯示以一致方式安裝目前所要求的 .NET Core CLI 版本時，所要使用的命令列。</span><span class="sxs-lookup"><span data-stu-id="8d08e-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="8d08e-162">例如，如果您指定 `latest` 版本，就會顯示特定版本的連結，以便在建置指令碼中以決定性方式使用此命令。</span><span class="sxs-lookup"><span data-stu-id="8d08e-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="8d08e-163">如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。</span><span class="sxs-lookup"><span data-stu-id="8d08e-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

* **`-NoPath`**

  <span data-ttu-id="8d08e-164">如果設定，就不會將安裝資料夾匯出至目前工作階段的路徑。</span><span class="sxs-lookup"><span data-stu-id="8d08e-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="8d08e-165">指令碼預設會修改此路徑，以讓 CLI 工具在安裝後立即可供使用。</span><span class="sxs-lookup"><span data-stu-id="8d08e-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

* **`-Verbose`**

  <span data-ttu-id="8d08e-166">顯示診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="8d08e-166">Displays diagnostics information.</span></span>

* **`-AzureFeed`**

  <span data-ttu-id="8d08e-167">指定給安裝程式的 Azure 摘要 URL。</span><span class="sxs-lookup"><span data-stu-id="8d08e-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="8d08e-168">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="8d08e-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="8d08e-169">預設值為 `https://dotnetcli.azureedge.net/dotnet`。</span><span class="sxs-lookup"><span data-stu-id="8d08e-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

* **`-UncachedFeed`**

  <span data-ttu-id="8d08e-170">允許變更此安裝程式所使用之未快取摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="8d08e-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="8d08e-171">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="8d08e-171">We recommended that you don't change this value.</span></span>

* **`-NoCdn`**

  <span data-ttu-id="8d08e-172">不允許從 [Azure 內容傳遞網路 (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) 下載，而直接使用未快取的摘要。</span><span class="sxs-lookup"><span data-stu-id="8d08e-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

* **`-FeedCredential`**

  <span data-ttu-id="8d08e-173">用來作為要附加至 Azure 摘要的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="8d08e-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="8d08e-174">這可允許變更 URL 以使用非公用 Blob 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="8d08e-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

* **`-ProxyAddress`**

  <span data-ttu-id="8d08e-175">如果設定，安裝程式會使用此 Proxy 進行 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="8d08e-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="8d08e-176">(只適用於 Windows)</span><span class="sxs-lookup"><span data-stu-id="8d08e-176">(Only valid for Windows)</span></span>

* **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="8d08e-177">如果設定，當使用 Proxy 位址時，安裝程式會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="8d08e-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="8d08e-178">(只適用於 Windows)</span><span class="sxs-lookup"><span data-stu-id="8d08e-178">(Only valid for Windows)</span></span>

* **`-SkipNonVersionedFiles`**

  <span data-ttu-id="8d08e-179">如果已經有非版本控制的檔案 (例如 *dotnet.exe*) 存在，便略過其安裝。</span><span class="sxs-lookup"><span data-stu-id="8d08e-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

* **`-Help`**

  <span data-ttu-id="8d08e-180">印出指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="8d08e-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="8d08e-181">範例</span><span class="sxs-lookup"><span data-stu-id="8d08e-181">Examples</span></span>

* <span data-ttu-id="8d08e-182">將最新的長期支援 (LTS) 版本安裝至預設位置︰</span><span class="sxs-lookup"><span data-stu-id="8d08e-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="8d08e-183">Windows：</span><span class="sxs-lookup"><span data-stu-id="8d08e-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="8d08e-184">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="8d08e-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* <span data-ttu-id="8d08e-185">將來自 2.0 通道的最新版本安裝至指定的位置︰</span><span class="sxs-lookup"><span data-stu-id="8d08e-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="8d08e-186">Windows：</span><span class="sxs-lookup"><span data-stu-id="8d08e-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="8d08e-187">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="8d08e-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* <span data-ttu-id="8d08e-188">安裝共用執行階段 1.1.0 版本：</span><span class="sxs-lookup"><span data-stu-id="8d08e-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="8d08e-189">Windows：</span><span class="sxs-lookup"><span data-stu-id="8d08e-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  <span data-ttu-id="8d08e-190">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="8d08e-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* <span data-ttu-id="8d08e-191">取得指令碼並在公司 Proxy 後方安裝 2.1.2 版本 (僅適用於 Windows)：</span><span class="sxs-lookup"><span data-stu-id="8d08e-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* <span data-ttu-id="8d08e-192">取得指令碼並安裝 .NET Core CLI 單行範例：</span><span class="sxs-lookup"><span data-stu-id="8d08e-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="8d08e-193">Windows：</span><span class="sxs-lookup"><span data-stu-id="8d08e-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="8d08e-194">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="8d08e-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="8d08e-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d08e-195">See also</span></span>

- [<span data-ttu-id="8d08e-196">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="8d08e-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="8d08e-197">.NET Core 執行階段和 SDK 下載封存</span><span class="sxs-lookup"><span data-stu-id="8d08e-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
