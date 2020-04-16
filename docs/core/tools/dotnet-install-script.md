---
title: dotnet-install 指令碼
description: 瞭解用於安裝 .NET 核心 SDK 和共用執行時的 dotnet 安裝文稿。
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463681"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="2b65c-103">dotnet-install 指令碼參考</span><span class="sxs-lookup"><span data-stu-id="2b65c-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="2b65c-104">名稱</span><span class="sxs-lookup"><span data-stu-id="2b65c-104">Name</span></span>

<span data-ttu-id="2b65c-105">`dotnet-install.ps1` | `dotnet-install.sh`- 用於安裝 .NET 核心 SDK 和共用執行時的文稿。</span><span class="sxs-lookup"><span data-stu-id="2b65c-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2b65c-106">概要</span><span class="sxs-lookup"><span data-stu-id="2b65c-106">Synopsis</span></span>

<span data-ttu-id="2b65c-107">Windows：</span><span class="sxs-lookup"><span data-stu-id="2b65c-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

<span data-ttu-id="2b65c-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="2b65c-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="2b65c-109">描述</span><span class="sxs-lookup"><span data-stu-id="2b65c-109">Description</span></span>

<span data-ttu-id="2b65c-110">這些`dotnet-install`文稿用於執行 .NET 核心 SDK 的非管理員安裝,其中包括 .NET Core CLI 和共用執行時。</span><span class="sxs-lookup"><span data-stu-id="2b65c-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="2b65c-111">我們建議您使用文稿的穩定版本:</span><span class="sxs-lookup"><span data-stu-id="2b65c-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="2b65c-112">Bash(Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="2b65c-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="2b65c-113">電源外殼(視窗):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="2b65c-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="2b65c-114">這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="2b65c-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="2b65c-115">有兩個指令碼：一個是在 Windows 上運作的 PowerShell 指令碼，另一個是在 Linux/macOS 上運作的 Bash 指令碼。</span><span class="sxs-lookup"><span data-stu-id="2b65c-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="2b65c-116">這兩個指令碼有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="2b65c-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="2b65c-117">Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。</span><span class="sxs-lookup"><span data-stu-id="2b65c-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="2b65c-118">安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="2b65c-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="2b65c-119">根據預設，安裝指令碼會下載並安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="2b65c-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="2b65c-120">如果您想要只取得共用執行階段，請指定 `-Runtime|--runtime` 引數。</span><span class="sxs-lookup"><span data-stu-id="2b65c-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="2b65c-121">根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。</span><span class="sxs-lookup"><span data-stu-id="2b65c-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="2b65c-122">指定 `-NoPath|--no-path` 引數可以覆寫此預設行為。</span><span class="sxs-lookup"><span data-stu-id="2b65c-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="2b65c-123">執行指令碼之前，請安裝所有必要的[相依性 (英文)](../install/dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="2b65c-124">您可以使用 `-Version|--version` 引數安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="2b65c-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="2b65c-125">版本必須指定為三部分版本(例如。 `2.1.0`</span><span class="sxs-lookup"><span data-stu-id="2b65c-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="2b65c-126">如果未提供，就會使用 `latest` 版本。</span><span class="sxs-lookup"><span data-stu-id="2b65c-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="2b65c-127">選項。</span><span class="sxs-lookup"><span data-stu-id="2b65c-127">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="2b65c-128">要安裝的 .NET Core 二進位檔的架構。</span><span class="sxs-lookup"><span data-stu-id="2b65c-128">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="2b65c-129">可能的值為 `<auto>`、`amd64`、`x64`、`x86`、`arm64` 和 `arm`。</span><span class="sxs-lookup"><span data-stu-id="2b65c-129">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="2b65c-130">預設值為 `<auto>`，代表目前正在執行的 OS 架構。</span><span class="sxs-lookup"><span data-stu-id="2b65c-130">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="2b65c-131">指定給安裝程式的 Azure 摘要 URL。</span><span class="sxs-lookup"><span data-stu-id="2b65c-131">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="2b65c-132">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="2b65c-132">We recommended that you don't change this value.</span></span> <span data-ttu-id="2b65c-133">預設值是 `https://dotnetcli.azureedge.net/dotnet`。</span><span class="sxs-lookup"><span data-stu-id="2b65c-133">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="2b65c-134">指定安裝的來源通道。</span><span class="sxs-lookup"><span data-stu-id="2b65c-134">Specifies the source channel for the installation.</span></span> <span data-ttu-id="2b65c-135">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="2b65c-135">The possible values are:</span></span>

  - <span data-ttu-id="2b65c-136">`Current` - 最新版本。</span><span class="sxs-lookup"><span data-stu-id="2b65c-136">`Current` - Most current release.</span></span>
  - <span data-ttu-id="2b65c-137">`LTS` - 長期支援通道 (最新的支援版本)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-137">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="2b65c-138">代表特定版本的 X.Y 格式兩段式版本 (例如 `2.1` 或 `3.0`)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-138">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="2b65c-139">分支名稱:例如,`release/3.1.1xx``master`或 (用於夜間發佈)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-139">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="2b65c-140">使用此選項可以從預覽頻道安裝版本。</span><span class="sxs-lookup"><span data-stu-id="2b65c-140">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="2b65c-141">使用[安裝程式和二進位檔案](https://github.com/dotnet/core-sdk#installers-and-binaries)中列出的通道的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b65c-141">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="2b65c-142">預設值是 `LTS`。</span><span class="sxs-lookup"><span data-stu-id="2b65c-142">The default value is `LTS`.</span></span> <span data-ttu-id="2b65c-143">如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援政策](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) \(英文\) 頁面。</span><span class="sxs-lookup"><span data-stu-id="2b65c-143">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="2b65c-144">如果設定，指令碼將不會執行安裝。</span><span class="sxs-lookup"><span data-stu-id="2b65c-144">If set, the script won't perform the installation.</span></span> <span data-ttu-id="2b65c-145">取而代之的是，會顯示以一致方式安裝目前所要求的 .NET Core CLI 版本時，所要使用的命令列。</span><span class="sxs-lookup"><span data-stu-id="2b65c-145">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="2b65c-146">例如，如果您指定 `latest` 版本，就會顯示特定版本的連結，以便在建置指令碼中以決定性方式使用此命令。</span><span class="sxs-lookup"><span data-stu-id="2b65c-146">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="2b65c-147">如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。</span><span class="sxs-lookup"><span data-stu-id="2b65c-147">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="2b65c-148">用來作為要附加至 Azure 摘要的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="2b65c-148">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="2b65c-149">這可允許變更 URL 以使用非公用 Blob 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2b65c-149">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="2b65c-150">印出指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="2b65c-150">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="2b65c-151">指定安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="2b65c-151">Specifies the installation path.</span></span> <span data-ttu-id="2b65c-152">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="2b65c-152">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="2b65c-153">預設值是 *%LocalAppData%\Microsoft\dotnet*。</span><span class="sxs-lookup"><span data-stu-id="2b65c-153">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="2b65c-154">二進位檔會直接放在此目錄中。</span><span class="sxs-lookup"><span data-stu-id="2b65c-154">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="2b65c-155">指定用於確定 SDK 版本的[global.json](global-json.md)檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="2b65c-155">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="2b65c-156">*全域.json*檔必須具有的值`sdk:version`。</span><span class="sxs-lookup"><span data-stu-id="2b65c-156">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="2b65c-157">不允許從 [Azure 內容傳遞網路 (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) 下載，而直接使用未快取的摘要。</span><span class="sxs-lookup"><span data-stu-id="2b65c-157">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="2b65c-158">如果設定，就不會將安裝資料夾匯出至目前工作階段的路徑。</span><span class="sxs-lookup"><span data-stu-id="2b65c-158">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="2b65c-159">默認情況下,指令稿修改 PATH,使 .NET 核心 CLI 在安裝後立即可用。</span><span class="sxs-lookup"><span data-stu-id="2b65c-159">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="2b65c-160">如果設定，安裝程式會使用此 Proxy 進行 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="2b65c-160">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="2b65c-161">(僅適用於 Windows。</span><span class="sxs-lookup"><span data-stu-id="2b65c-161">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="2b65c-162">如果設定，當使用 Proxy 位址時，安裝程式會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="2b65c-162">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="2b65c-163">(僅適用於 Windows。</span><span class="sxs-lookup"><span data-stu-id="2b65c-163">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="2b65c-164">只安裝共用執行階段，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="2b65c-164">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="2b65c-165">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="2b65c-165">The possible values are:</span></span>

  - <span data-ttu-id="2b65c-166">`dotnet` - `Microsoft.NETCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="2b65c-166">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="2b65c-167">`aspnetcore` - `Microsoft.AspNetCore.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="2b65c-167">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="2b65c-168">`windowsdesktop` - `Microsoft.WindowsDesktop.App` 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="2b65c-168">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="2b65c-169">指定要安裝工具的[執行時識別碼](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-169">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="2b65c-170">用於`linux-x64`攜帶型 Linux。</span><span class="sxs-lookup"><span data-stu-id="2b65c-170">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="2b65c-171">(僅適用於 Linux/macOS。</span><span class="sxs-lookup"><span data-stu-id="2b65c-171">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="2b65c-172">此參數已被淘汰，在未來的指令碼版本中可能會將其移除。</span><span class="sxs-lookup"><span data-stu-id="2b65c-172">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="2b65c-173">建議的替代方案是 `-Runtime|--runtime` 選項。</span><span class="sxs-lookup"><span data-stu-id="2b65c-173">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="2b65c-174">只安裝共用執行階段位元，而不是整個 SDK。</span><span class="sxs-lookup"><span data-stu-id="2b65c-174">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="2b65c-175">這個選項等效於指定`-Runtime|--runtime dotnet`。</span><span class="sxs-lookup"><span data-stu-id="2b65c-175">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="2b65c-176">如果已經有非版本控制的檔案 (例如 *dotnet.exe*) 存在，便略過其安裝。</span><span class="sxs-lookup"><span data-stu-id="2b65c-176">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="2b65c-177">允許變更此安裝程式所使用之未快取摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="2b65c-177">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="2b65c-178">建議您不要變更這個值。</span><span class="sxs-lookup"><span data-stu-id="2b65c-178">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="2b65c-179">顯示診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="2b65c-179">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="2b65c-180">代表特定的組建版本。</span><span class="sxs-lookup"><span data-stu-id="2b65c-180">Represents a specific build version.</span></span> <span data-ttu-id="2b65c-181">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="2b65c-181">The possible values are:</span></span>

  - <span data-ttu-id="2b65c-182">`latest` - 通道上的最新組建 (與 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-182">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="2b65c-183">`coherent` - 通道上的最新一致性組建；使用最新的穩定套件組合 (與分支名稱 `-Channel` 選項搭配使用)。</span><span class="sxs-lookup"><span data-stu-id="2b65c-183">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="2b65c-184">代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。</span><span class="sxs-lookup"><span data-stu-id="2b65c-184">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="2b65c-185">例如： `2.0.0-preview2-006120` 。</span><span class="sxs-lookup"><span data-stu-id="2b65c-185">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="2b65c-186">如果未指定，`-Version` 會預設為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="2b65c-186">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="2b65c-187">範例</span><span class="sxs-lookup"><span data-stu-id="2b65c-187">Examples</span></span>

- <span data-ttu-id="2b65c-188">將最新的長期支援 (LTS) 版本安裝至預設位置︰</span><span class="sxs-lookup"><span data-stu-id="2b65c-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="2b65c-189">Windows：</span><span class="sxs-lookup"><span data-stu-id="2b65c-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="2b65c-190">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="2b65c-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="2b65c-191">將最新版本從 3.1 通道安裝到指定位置:</span><span class="sxs-lookup"><span data-stu-id="2b65c-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="2b65c-192">Windows：</span><span class="sxs-lookup"><span data-stu-id="2b65c-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="2b65c-193">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="2b65c-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="2b65c-194">安裝共享執行時的 3.0.0 版本:</span><span class="sxs-lookup"><span data-stu-id="2b65c-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="2b65c-195">Windows：</span><span class="sxs-lookup"><span data-stu-id="2b65c-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="2b65c-196">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="2b65c-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="2b65c-197">取得指令碼並在公司 Proxy 後方安裝 2.1.2 版本 (僅適用於 Windows)：</span><span class="sxs-lookup"><span data-stu-id="2b65c-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="2b65c-198">取得指令碼並安裝 .NET Core CLI 單行範例：</span><span class="sxs-lookup"><span data-stu-id="2b65c-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="2b65c-199">Windows：</span><span class="sxs-lookup"><span data-stu-id="2b65c-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="2b65c-200">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="2b65c-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="2b65c-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b65c-201">See also</span></span>

- [<span data-ttu-id="2b65c-202">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="2b65c-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="2b65c-203">.NET Core 執行階段和 SDK 下載封存</span><span class="sxs-lookup"><span data-stu-id="2b65c-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
