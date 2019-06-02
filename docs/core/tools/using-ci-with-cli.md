---
title: 在持續整合 (CI) 中使用 .NET Core SDK 和工具
description: 如何在組建伺服器上使用 .NET Core SDK 和其工具的相關資訊。
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 629b7a9e1f2b59981adb77ab4d3125be7036ff02
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299976"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="754ef-103">在持續整合 (CI) 中使用 .NET Core SDK 和工具</span><span class="sxs-lookup"><span data-stu-id="754ef-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="754ef-104">本文件概述如何在組建伺服器上使用 .NET Core SDK 和其工具。</span><span class="sxs-lookup"><span data-stu-id="754ef-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="754ef-105">.NET Core 工具組可透過互動的方式運作 (開發人員在命令提示字元中輸入命令)，也可透過自動的方式運作 (持續整合 (CI) 伺服器執行建置指令碼)。</span><span class="sxs-lookup"><span data-stu-id="754ef-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="754ef-106">命令、選項、輸入和輸出都是相同的，您只需要提供取得工具的方式和建置應用程式的系統。</span><span class="sxs-lookup"><span data-stu-id="754ef-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="754ef-107">本文件著重於 CI 的工具取得案例，並包含設計建置指令碼並建立其結構的相關建議。</span><span class="sxs-lookup"><span data-stu-id="754ef-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="754ef-108">CI 組建伺服器的安裝選項</span><span class="sxs-lookup"><span data-stu-id="754ef-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="754ef-109">使用原生安裝程式</span><span class="sxs-lookup"><span data-stu-id="754ef-109">Using the native installers</span></span>

<span data-ttu-id="754ef-110">有針對 macOS、Linux 及 Windows 提供原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="754ef-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="754ef-111">安裝程式需要組建伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="754ef-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="754ef-112">使用原生安裝程式的優點在於它會安裝工具執行時所需的所有原生相依性。</span><span class="sxs-lookup"><span data-stu-id="754ef-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="754ef-113">原生安裝程式也提供 SDK 的全系統安裝。</span><span class="sxs-lookup"><span data-stu-id="754ef-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="754ef-114">macOS 使用者應使用 PKG 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="754ef-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="754ef-115">在 Linux 上，您可以選擇使用摘要套件管理員 (例如適用於 Ubuntu 的 apt-get 或適用於 CentOS 的 yum)，或使用套件本身 (DEB 或 RPM)。</span><span class="sxs-lookup"><span data-stu-id="754ef-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="754ef-116">在 Windows 上請使用 MSI 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="754ef-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="754ef-117">您可以在 [.NET Core 下載](https://dotnet.microsoft.com/download) \(英文\) 找到最新的穩定二進位檔。</span><span class="sxs-lookup"><span data-stu-id="754ef-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="754ef-118">如果您想要使用最新 (但可能不穩定) 的發行前版本工具，請使用 [dotnet/core-sdk GitHub 存放庫](https://github.com/dotnet/core-sdk#installers-and-binaries) \(英文\) 所提供的連結。</span><span class="sxs-lookup"><span data-stu-id="754ef-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="754ef-119">針對 Linux 發行版本，有提供 `tar.gz` 封存 (也稱為 `tarballs`)；請使用封存內的安裝指令碼來安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="754ef-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="754ef-120">使用安裝程式指令碼</span><span class="sxs-lookup"><span data-stu-id="754ef-120">Using the installer script</span></span>

<span data-ttu-id="754ef-121">使用安裝程式指令碼可以在您的組建伺服器上進行非系統管理安裝，以及輕鬆地將取得工具的作業自動化。</span><span class="sxs-lookup"><span data-stu-id="754ef-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="754ef-122">指令碼會負責下載工具，然後將工具解壓縮至預設或指定位置以供使用。</span><span class="sxs-lookup"><span data-stu-id="754ef-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="754ef-123">您也可以指定要安裝的工具版本，以及指定要安裝整個 SDK 或只安裝共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="754ef-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="754ef-124">在建置開始時，安裝程式指令碼會自動執行，以擷取和安裝所需的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="754ef-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="754ef-125">「所需版本」  是您專案所需建置的任何 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="754ef-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="754ef-126">指令碼可讓您將 SDK 安裝在伺服器上的本機目錄中，從安裝位置執行工具，然後在建置之後清除 (或讓 CI 服務清除)。</span><span class="sxs-lookup"><span data-stu-id="754ef-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="754ef-127">這可以為整個建置程序提供封裝和隔離。</span><span class="sxs-lookup"><span data-stu-id="754ef-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="754ef-128">您可以在 [dotnet-install](dotnet-install-script.md) 一文中找到安裝指令碼參考。</span><span class="sxs-lookup"><span data-stu-id="754ef-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="754ef-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="754ef-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="754ef-130">使用安裝程式指令碼時，不會自動安裝原生相依性。</span><span class="sxs-lookup"><span data-stu-id="754ef-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="754ef-131">如果作業系統沒有原生相依性，您必須加以安裝。</span><span class="sxs-lookup"><span data-stu-id="754ef-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="754ef-132">如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](../linux-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="754ef-132">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="754ef-133">CI 設定範例</span><span class="sxs-lookup"><span data-stu-id="754ef-133">CI setup examples</span></span>

<span data-ttu-id="754ef-134">本節描述如何使用 PowerShell 或 Bash 指令碼進行手動設定，以及描述幾個軟體即服務 (SaaS) CI 解決方案。</span><span class="sxs-lookup"><span data-stu-id="754ef-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="754ef-135">涵蓋的 SaaS CI 解決方案包括 [Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/) 及 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)。</span><span class="sxs-lookup"><span data-stu-id="754ef-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="754ef-136">手動設定</span><span class="sxs-lookup"><span data-stu-id="754ef-136">Manual setup</span></span>

<span data-ttu-id="754ef-137">每個 SaaS 服務都有自己用於建立及設定建置程序的方法。</span><span class="sxs-lookup"><span data-stu-id="754ef-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="754ef-138">如果您使用上面未列出的其他 SaaS 解決方案，或需要進行超出預先封裝支援的自訂作業，就必須至少執行一些手動設定。</span><span class="sxs-lookup"><span data-stu-id="754ef-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="754ef-139">在一般情況下，手動設定需要您取得某一版本的工具 (或該工具的最新每晚組建)，然後執行您的建置指令碼。</span><span class="sxs-lookup"><span data-stu-id="754ef-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="754ef-140">您可以使用 PowerShell 或 Bash 指令碼協調 .NET Core 命令，或使用概述建置程序的專案檔。</span><span class="sxs-lookup"><span data-stu-id="754ef-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="754ef-141">[協調流程小節](#orchestrating-the-build)能提供這些選項的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="754ef-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="754ef-142">在您建立執行手動 CI 組建伺服器設定的指令碼之後，請在您的開發電腦上使用該指令碼，以在本機針對測試目的建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="754ef-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="754ef-143">一旦您確認指令碼可在本機正常執行之後，請將它部署到 CI 組建伺服器。</span><span class="sxs-lookup"><span data-stu-id="754ef-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="754ef-144">一個相對簡單的 PowerShell 指令碼能示範如何取得 .NET Core SDK，並將它安裝在 Windows 組建伺服器上：</span><span class="sxs-lookup"><span data-stu-id="754ef-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="754ef-145">您可以在指令碼結尾處提供建置程序的實作。</span><span class="sxs-lookup"><span data-stu-id="754ef-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="754ef-146">指令碼會取得工具，然後執行您的建置程序。</span><span class="sxs-lookup"><span data-stu-id="754ef-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="754ef-147">針對 UNIX 電腦，以下 Bash 指令碼會以類似的方式執行 PowerShell 指令碼中描述的動作：</span><span class="sxs-lookup"><span data-stu-id="754ef-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="754ef-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="754ef-148">Travis CI</span></span>

<span data-ttu-id="754ef-149">您可以將 [Travis CI](https://travis-ci.org/) \(英文\) 設定成使用 `csharp` 語言和 `dotnet` 索引鍵來安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="754ef-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="754ef-150">如需詳細資訊，請參閱有關[建置 C#、F# 或 Visual Basic 專案](https://docs.travis-ci.com/user/languages/csharp/) \(英文\) 的官方 Travis CI 文件。</span><span class="sxs-lookup"><span data-stu-id="754ef-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="754ef-151">在您存取 Travis CI 資訊時，請留意這個由社群維護的 `language: csharp` 語言識別碼可適用於所有 .NET 語言，包括 F# 和 Mono。</span><span class="sxs-lookup"><span data-stu-id="754ef-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="754ef-152">Travis CI 會在「建置矩陣」  中執行 macOS 和 Linux 作業，您可以在該矩陣中指定執行階段、環境及排除項/包含項的組合，以涵蓋應用程式的組建組合。</span><span class="sxs-lookup"><span data-stu-id="754ef-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="754ef-153">如需詳細資訊，請參閱 Travis CI 文件中的 [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) (自訂組建) 一文。</span><span class="sxs-lookup"><span data-stu-id="754ef-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="754ef-154">MSBuild 型工具會在套件中包含 LTS (1.0.x) 和目前 (1.1.x) 執行階段，所以透過安裝 SDK，您就能獲得進行建置所需的一切項目。</span><span class="sxs-lookup"><span data-stu-id="754ef-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="754ef-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="754ef-155">AppVeyor</span></span>

<span data-ttu-id="754ef-156">[AppVeyor](https://www.appveyor.com/) \(英文\) 會搭配 `Visual Studio 2017` 組建背景工作角色映像安裝 .NET Core 1.0.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="754ef-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="754ef-157">還有其他具有不同 .NET Core SDK 版本的組建映像可供使用。</span><span class="sxs-lookup"><span data-stu-id="754ef-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="754ef-158">如需詳細資訊，請參閱 AppVeyor 文件中的 [appveyor.yml 範例](https://github.com/dotnet/docs/blob/master/appveyor.yml) \(英文\) 和 [組建背景工作角色映像](https://www.appveyor.com/docs/build-environment/#build-worker-images) \(英文\) 文章。</span><span class="sxs-lookup"><span data-stu-id="754ef-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="754ef-159">系統會使用安裝指令碼將 .NET Core SDK 二進位檔下載至子目錄並加以解壓縮，然後將它們新增至 `PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="754ef-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="754ef-160">新增一個建置矩陣，以執行與多個 .NET Core SDK 版本的整合測試：</span><span class="sxs-lookup"><span data-stu-id="754ef-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="754ef-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="754ef-161">Azure DevOps Services</span></span>

<span data-ttu-id="754ef-162">設定 Azure DevOps Services 使用以下其中一種方式建置 .NET Core 專案：</span><span class="sxs-lookup"><span data-stu-id="754ef-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="754ef-163">使用您的命令從[手動設定步驟](#manual-setup)執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="754ef-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="754ef-164">建立由數個設定為使用 .NET Core 工具的 Azure DevOps Services 內建建置工作所組成的組建。</span><span class="sxs-lookup"><span data-stu-id="754ef-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="754ef-165">這兩種解決方案都是可行的。</span><span class="sxs-lookup"><span data-stu-id="754ef-165">Both solutions are valid.</span></span> <span data-ttu-id="754ef-166">您可以使用手動設定指令碼來控制接收到的工具版本，因為那些工具是以組建之一部分的形式下載的。</span><span class="sxs-lookup"><span data-stu-id="754ef-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="754ef-167">組建會從您必須建立的指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="754ef-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="754ef-168">本文僅涵蓋手動選項。</span><span class="sxs-lookup"><span data-stu-id="754ef-168">This article only covers the manual option.</span></span> <span data-ttu-id="754ef-169">如需有關使用 Azure DevOps Services 建置工作來組成組建的詳細資訊，請參閱 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)\(英文\) 文件。</span><span class="sxs-lookup"><span data-stu-id="754ef-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="754ef-170">若要在 Azure DevOps Services 中使用手動設定指令碼，請建立新的組建定義，並指定要針對建置步驟執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="754ef-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="754ef-171">這可使用 Azure DevOps Services 使用者介面來完成：</span><span class="sxs-lookup"><span data-stu-id="754ef-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="754ef-172">從建立新的組建定義開始。</span><span class="sxs-lookup"><span data-stu-id="754ef-172">Start by creating a new build definition.</span></span> <span data-ttu-id="754ef-173">當您抵達會提供選項以定義要建立哪一種組建的畫面時，請選取 [空]  選項。</span><span class="sxs-lookup"><span data-stu-id="754ef-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![選取空的組建定義](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="754ef-175">設定要建置的存放庫之後，系統就會將您導向至組建定義。</span><span class="sxs-lookup"><span data-stu-id="754ef-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="754ef-176">選取 [加入建置步驟]  ：</span><span class="sxs-lookup"><span data-stu-id="754ef-176">Select **Add build step**:</span></span>

   ![加入建置步驟](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="754ef-178">系統會向您顯示 [工作目錄]  。</span><span class="sxs-lookup"><span data-stu-id="754ef-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="754ef-179">目錄中包含您在組建中使用的工作。</span><span class="sxs-lookup"><span data-stu-id="754ef-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="754ef-180">因為您有指令碼，請選取 [PowerShell: 執行 PowerShell 指令碼]  的 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="754ef-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![新增 PowerShell 指令碼步驟](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="754ef-182">設定建置步驟。</span><span class="sxs-lookup"><span data-stu-id="754ef-182">Configure the build step.</span></span> <span data-ttu-id="754ef-183">從您正在建置的存放庫加入指令碼：</span><span class="sxs-lookup"><span data-stu-id="754ef-183">Add the script from the repository that you're building:</span></span>

   ![指定要執行的 PowerShell 指令碼](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="754ef-185">協調組建</span><span class="sxs-lookup"><span data-stu-id="754ef-185">Orchestrating the build</span></span>

<span data-ttu-id="754ef-186">本文件大部分內容為描述如何取得 .NET Core 工具及設定各種 CI 服務，並沒有提供如何使用 .NET Core 來協調或「實際建置」  程式碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="754ef-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="754ef-187">建置程序的結構方式取決於許多因素，無法在這裡以一一涵蓋。</span><span class="sxs-lookup"><span data-stu-id="754ef-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="754ef-188">如需有關使用各項技術來協調組建的詳細資訊，請探索 [Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/) 及 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) 文件集內所提供的資源與範例。</span><span class="sxs-lookup"><span data-stu-id="754ef-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="754ef-189">使用 .NET Core 工具建立 .NET Core 程式碼建置程序的結構時，可以採取兩種方法：直接使用 MSBuild，或使用 .NET Core 命令列命令。</span><span class="sxs-lookup"><span data-stu-id="754ef-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="754ef-190">您可以視自己對特定方法的熟悉程度並權衡其複雜度，來選擇要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="754ef-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="754ef-191">MSBuild 可讓您以工作和目標的形式表示建置程序，但使用此方法必須額外學習 MSBuild 專案檔語法。</span><span class="sxs-lookup"><span data-stu-id="754ef-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="754ef-192">使用 .NET Core 命令列工具或許比較簡單，但您必須使用如 `bash` 或 PowerShell 之類的指令碼語言撰寫協調流程邏輯。</span><span class="sxs-lookup"><span data-stu-id="754ef-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="754ef-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="754ef-193">See also</span></span>

- <span data-ttu-id="754ef-194">[.NET 下載 - Linux](https://dotnet.microsoft.com/download?initial-os=linux) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="754ef-194">[.NET downloads - Linux](https://dotnet.microsoft.com/download?initial-os=linux)</span></span>
