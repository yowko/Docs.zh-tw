---
title: 在 Linux 上手動安裝 .NET-.NET
description: 示範如何在 Linux 上沒有套件管理員的情況下安裝 .NET SDK 和 .NET 執行時間。 使用安裝腳本或手動解壓縮二進位檔。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 5879d4d66aba8bfa00caadbe3c33d6df0d7da59a
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970961"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a><span data-ttu-id="d5d8e-104">手動安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="d5d8e-104">Install the .NET SDK or the .NET Runtime manually</span></span>

<span data-ttu-id="d5d8e-105">Linux 上支援 .NET，本文說明如何使用安裝腳本或解壓縮二進位檔，在 Linux 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-105">.NET is supported on Linux and this article describes how to install .NET on Linux using the install script or by extracting the binaries.</span></span> <span data-ttu-id="d5d8e-106">如需支援內建封裝管理員的發行版本清單，請參閱 [在 Linux 上安裝 .net](linux.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-106">For a list of distributions that support the built-in package manager, see [Install .NET on Linux](linux.md).</span></span>

<span data-ttu-id="d5d8e-107">您也可以使用 [貼齊] 來安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-107">You can also install .NET with snap.</span></span> <span data-ttu-id="d5d8e-108">如需詳細資訊，請參閱 [安裝 .NET SDK 或含 Snap 的 .Net 運行](linux-snap.md)時間。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-108">For more information, see [Install the .NET SDK or the .NET Runtime with Snap](linux-snap.md).</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a><span data-ttu-id="d5d8e-109">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="d5d8e-109">.NET releases</span></span>

<span data-ttu-id="d5d8e-110">下表列出 .NET (和 .NET Core) 版本：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-110">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="d5d8e-111">支援✔️</span><span class="sxs-lookup"><span data-stu-id="d5d8e-111">✔️ Supported</span></span> | <span data-ttu-id="d5d8e-112">❌ 支援</span><span class="sxs-lookup"><span data-stu-id="d5d8e-112">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="d5d8e-113">5.0</span><span class="sxs-lookup"><span data-stu-id="d5d8e-113">5.0</span></span>         | <span data-ttu-id="d5d8e-114">3.0</span><span class="sxs-lookup"><span data-stu-id="d5d8e-114">3.0</span></span>           |
| <span data-ttu-id="d5d8e-115">3.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="d5d8e-115">3.1 (LTS)</span></span>   | <span data-ttu-id="d5d8e-116">2.2</span><span class="sxs-lookup"><span data-stu-id="d5d8e-116">2.2</span></span>           |
| <span data-ttu-id="d5d8e-117">2.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="d5d8e-117">2.1 (LTS)</span></span>   | <span data-ttu-id="d5d8e-118">2.0</span><span class="sxs-lookup"><span data-stu-id="d5d8e-118">2.0</span></span>           |
|             | <span data-ttu-id="d5d8e-119">1.1</span><span class="sxs-lookup"><span data-stu-id="d5d8e-119">1.1</span></span>           |
|             | <span data-ttu-id="d5d8e-120">1.0</span><span class="sxs-lookup"><span data-stu-id="d5d8e-120">1.0</span></span>           |

<span data-ttu-id="d5d8e-121">如需 .NET 版本生命週期的詳細資訊，請參閱 [.Net Core 和 .net 5 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-121">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="dependencies"></a><span data-ttu-id="d5d8e-122">相依性</span><span class="sxs-lookup"><span data-stu-id="d5d8e-122">Dependencies</span></span>

<span data-ttu-id="d5d8e-123">當您安裝 .NET 時，可能不會安裝特定的相依性，例如在 [手動安裝](#manual-install)時。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-123">It's possible that when you install .NET, specific dependencies may not be installed, such as when [manually installing](#manual-install).</span></span> <span data-ttu-id="d5d8e-124">下列清單詳細說明 Microsoft 支援的 Linux 發行版本，以及您可能需要安裝的相依性。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-124">The following list details Linux distributions that are supported by Microsoft and have dependencies you may need to install.</span></span> <span data-ttu-id="d5d8e-125">查看 [散發] 頁面以取得詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-125">Check the distribution page for more information:</span></span>

- [<span data-ttu-id="d5d8e-126">Alpine</span><span class="sxs-lookup"><span data-stu-id="d5d8e-126">Alpine</span></span>](linux-alpine.md#dependencies)
- [<span data-ttu-id="d5d8e-127">Debian</span><span class="sxs-lookup"><span data-stu-id="d5d8e-127">Debian</span></span>](linux-debian.md#dependencies)
- [<span data-ttu-id="d5d8e-128">CentOS</span><span class="sxs-lookup"><span data-stu-id="d5d8e-128">CentOS</span></span>](linux-centos.md#dependencies)
- [<span data-ttu-id="d5d8e-129">Fedora</span><span class="sxs-lookup"><span data-stu-id="d5d8e-129">Fedora</span></span>](linux-fedora.md#dependencies)
- [<span data-ttu-id="d5d8e-130">RHEL</span><span class="sxs-lookup"><span data-stu-id="d5d8e-130">RHEL</span></span>](linux-rhel.md#dependencies)
- [<span data-ttu-id="d5d8e-131">SLES</span><span class="sxs-lookup"><span data-stu-id="d5d8e-131">SLES</span></span>](linux-sles.md#dependencies)
- [<span data-ttu-id="d5d8e-132">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d5d8e-132">Ubuntu</span></span>](linux-ubuntu.md#dependencies)

<span data-ttu-id="d5d8e-133">如需相依性的一般資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-133">For generic information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

### <a name="rpm-dependencies"></a><span data-ttu-id="d5d8e-134">RPM 相依性</span><span class="sxs-lookup"><span data-stu-id="d5d8e-134">RPM dependencies</span></span>

<span data-ttu-id="d5d8e-135">如果之前未列出您的散發套件，而且是以 RPM 為基礎的，您可能需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-135">If your distribution wasn't previously listed, and is RPM-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="d5d8e-136">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="d5d8e-136">krb5-libs</span></span>
- <span data-ttu-id="d5d8e-137">libicu</span><span class="sxs-lookup"><span data-stu-id="d5d8e-137">libicu</span></span>
- <span data-ttu-id="d5d8e-138">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="d5d8e-138">openssl-libs</span></span>

<span data-ttu-id="d5d8e-139">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

### <a name="deb-dependencies"></a><span data-ttu-id="d5d8e-140">DEB 相依性</span><span class="sxs-lookup"><span data-stu-id="d5d8e-140">DEB dependencies</span></span>

<span data-ttu-id="d5d8e-141">如果之前未列出您的散發套件，而且是以 debian 為基礎的，您可能需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-141">If your distribution wasn't previously listed, and is debian-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="d5d8e-142">libc6</span><span class="sxs-lookup"><span data-stu-id="d5d8e-142">libc6</span></span>
- <span data-ttu-id="d5d8e-143">libgcc1</span><span class="sxs-lookup"><span data-stu-id="d5d8e-143">libgcc1</span></span>
- <span data-ttu-id="d5d8e-144">libgssapi-krb5.keytab-2</span><span class="sxs-lookup"><span data-stu-id="d5d8e-144">libgssapi-krb5-2</span></span>
- <span data-ttu-id="d5d8e-145">libicu67</span><span class="sxs-lookup"><span data-stu-id="d5d8e-145">libicu67</span></span>
- <span data-ttu-id="d5d8e-146">libssl1.0.0 1。1</span><span class="sxs-lookup"><span data-stu-id="d5d8e-146">libssl1.1</span></span>
- <span data-ttu-id="d5d8e-147">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="d5d8e-147">libstdc++6</span></span>
- <span data-ttu-id="d5d8e-148">zlib1g</span><span class="sxs-lookup"><span data-stu-id="d5d8e-148">zlib1g</span></span>

### <a name="common-dependencies"></a><span data-ttu-id="d5d8e-149">常見的相依性</span><span class="sxs-lookup"><span data-stu-id="d5d8e-149">Common dependencies</span></span>

<span data-ttu-id="d5d8e-150">若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-150">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="d5d8e-151">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="d5d8e-151">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="d5d8e-152">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-152">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="d5d8e-153">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-153">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="d5d8e-154">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="d5d8e-154">Scripted install</span></span>

<span data-ttu-id="d5d8e-155">[Dotnet 安裝腳本](../tools/dotnet-install-script.md)用於自動化和非系統管理員安裝的 **SDK** 和 **運行** 時間。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="d5d8e-156">您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-156">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="d5d8e-157">腳本預設會安裝最新的 SDK [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-157">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="d5d8e-158">若要安裝目前版本，這可能不是 (LTS) 版本，請使用 `-c Current` 參數。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-158">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="d5d8e-159">若要安裝 .NET 執行時間，而不是 SDK，請使用 `--runtime` 參數。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-159">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="d5d8e-160">您可以藉由修改 `-c` 參數來指定特定版本，以安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-160">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="d5d8e-161">下列命令會安裝 .NET SDK 5.0。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-161">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="d5d8e-162">如需詳細資訊，請參閱 [dotnet-安裝腳本參考](../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-162">For more information, see [dotnet-install scripts reference](../tools/dotnet-install-script.md).</span></span>

## <a name="manual-install"></a><span data-ttu-id="d5d8e-163">手動安裝</span><span class="sxs-lookup"><span data-stu-id="d5d8e-163">Manual install</span></span>

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="d5d8e-164">您也可以下載並手動安裝 SDK 和執行時間，作為套件管理員的替代方案。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-164">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="d5d8e-165">手動安裝通常用來做為持續整合測試的一部分，或在不受支援的 Linux 發行版本上。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-165">Manual install is commonly used as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="d5d8e-166">針對開發人員或使用者，最好使用套件管理員。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-166">For a developer or user, it's better to use a package manager.</span></span>

<span data-ttu-id="d5d8e-167">如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-167">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="d5d8e-168">首先，從下列其中一個網站下載 SDK 或執行時間的 **二進位** 版本：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-168">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="d5d8e-169">✔️ [.net 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="d5d8e-169">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="d5d8e-170">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="d5d8e-170">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="d5d8e-171">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="d5d8e-171">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="d5d8e-172">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="d5d8e-172">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="d5d8e-173">接下來，將下載的檔案解壓縮，並使用 `export` 命令設定 .net 所使用的變數，然後確定 .net 是在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-173">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="d5d8e-174">若要將執行時間解壓縮，並讓 .NET CLI 命令可在終端機上使用，請先下載 .NET 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-174">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="d5d8e-175">然後，開啟終端機，並從儲存檔案的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-175">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="d5d8e-176">保存檔案名稱可能會因您所下載的內容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-176">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="d5d8e-177">**使用下列命令，將執行時間解壓縮**：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-177">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="d5d8e-178">**使用下列命令將 SDK 解壓縮**：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-178">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="d5d8e-179">上述 `export` 命令只會讓執行的終端機會話提供 .NET CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-179">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="d5d8e-180">您可以編輯 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-180">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="d5d8e-181">Linux 有一些不同的 shell 可用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-181">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="d5d8e-182">例如：</span><span class="sxs-lookup"><span data-stu-id="d5d8e-182">For example:</span></span>
>
> - <span data-ttu-id="d5d8e-183">**Bash Shell**： *~/.bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="d5d8e-183">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="d5d8e-184">**Korn Shell**： *~/.kshrc* 或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="d5d8e-184">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="d5d8e-185">**Z Shell**： *~/.zshrc* 或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="d5d8e-185">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="d5d8e-186">編輯您 shell 的適當原始程式檔，並新增 `:$HOME/dotnet` 至現有語句的結尾 `PATH` 。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-186">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="d5d8e-187">如果未 `PATH` 包含任何語句，請使用加入新的一行 `export PATH=$PATH:$HOME/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-187">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="d5d8e-188">此外，新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-188">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="d5d8e-189">這種方法可讓您將不同的版本安裝到不同的位置，並明確地選擇哪個應用程式要使用哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="d5d8e-189">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d5d8e-190">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d5d8e-190">Next steps</span></span>

- [<span data-ttu-id="d5d8e-191">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="d5d8e-191">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="d5d8e-192">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d5d8e-192">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
