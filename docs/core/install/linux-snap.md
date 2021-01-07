---
title: 在 Linux 上使用嵌入式管理單元安裝 .NET
description: 示範如何在 Linux 上使用貼齊來安裝 .NET SDK 或 .NET 執行時間。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970960"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="70f95-103">安裝具有嵌入式管理單元的 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="70f95-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="70f95-104">使用嵌入式管理套件來安裝 .NET SDK 或 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="70f95-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="70f95-105">快照是內建于您的 Linux 散發套件管理員的絕佳替代方案。</span><span class="sxs-lookup"><span data-stu-id="70f95-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="70f95-106">本文說明如何透過 [ [貼齊](https://snapcraft.io/dotnet-sdk)] 來安裝 .net。</span><span class="sxs-lookup"><span data-stu-id="70f95-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="70f95-107">「貼齊」是應用程式及其相依性的組合，可在不需要跨多個不同 Linux 發行版本進行修改的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="70f95-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="70f95-108">快照可從貼齊存放區中探索並安裝。</span><span class="sxs-lookup"><span data-stu-id="70f95-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="70f95-109">如需貼齊的詳細資訊，請參閱 [開始使用嵌入式管理單元](https://snapcraft.io/docs/getting-started)。</span><span class="sxs-lookup"><span data-stu-id="70f95-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="70f95-110">Windows 10 上的 WSL2 不支援嵌入式管理套件。</span><span class="sxs-lookup"><span data-stu-id="70f95-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="70f95-111">或者，您也可使用[ `dotnet-install` 腳本](linux-scripted-manual.md#scripted-install)或封裝管理員來進行特定的 WSL2 散發。</span><span class="sxs-lookup"><span data-stu-id="70f95-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="70f95-112">不建議您這麼做，但您可以嘗試 [從 snapcraft 論壇](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)啟用貼齊不支援的因應措施。</span><span class="sxs-lookup"><span data-stu-id="70f95-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="70f95-113">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="70f95-113">.NET releases</span></span>

<span data-ttu-id="70f95-114">只有✔️支援的 .NET SDK 版本可透過 [貼齊] 使用。</span><span class="sxs-lookup"><span data-stu-id="70f95-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="70f95-115">所有版本的 .NET 執行時間都可透過從2.1 版開始的貼齊來取得。</span><span class="sxs-lookup"><span data-stu-id="70f95-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="70f95-116">下表列出 .NET (和 .NET Core) 版本：</span><span class="sxs-lookup"><span data-stu-id="70f95-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="70f95-117">支援✔️</span><span class="sxs-lookup"><span data-stu-id="70f95-117">✔️ Supported</span></span> | <span data-ttu-id="70f95-118">❌ 支援</span><span class="sxs-lookup"><span data-stu-id="70f95-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="70f95-119">5.0</span><span class="sxs-lookup"><span data-stu-id="70f95-119">5.0</span></span>         | <span data-ttu-id="70f95-120">3.0</span><span class="sxs-lookup"><span data-stu-id="70f95-120">3.0</span></span>           |
| <span data-ttu-id="70f95-121">3.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="70f95-121">3.1 (LTS)</span></span>   | <span data-ttu-id="70f95-122">2.2</span><span class="sxs-lookup"><span data-stu-id="70f95-122">2.2</span></span>           |
| <span data-ttu-id="70f95-123">2.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="70f95-123">2.1 (LTS)</span></span>   | <span data-ttu-id="70f95-124">2.0</span><span class="sxs-lookup"><span data-stu-id="70f95-124">2.0</span></span>           |
|             | <span data-ttu-id="70f95-125">1.1</span><span class="sxs-lookup"><span data-stu-id="70f95-125">1.1</span></span>           |
|             | <span data-ttu-id="70f95-126">1.0</span><span class="sxs-lookup"><span data-stu-id="70f95-126">1.0</span></span>           |

<span data-ttu-id="70f95-127">如需 .NET 版本生命週期的詳細資訊，請參閱 [.Net Core 和 .net 5 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="70f95-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="70f95-128">SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="70f95-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="70f95-129">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="70f95-129">Install the SDK</span></span>

<span data-ttu-id="70f95-130">.NET SDK 的貼齊套件都是在相同的識別碼下發布： `dotnet-sdk` 。</span><span class="sxs-lookup"><span data-stu-id="70f95-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="70f95-131">您可以藉由指定通道來安裝特定版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="70f95-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="70f95-132">SDK 包含對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="70f95-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="70f95-133">下表列出這些通道：</span><span class="sxs-lookup"><span data-stu-id="70f95-133">The following table lists the channels:</span></span>

| <span data-ttu-id="70f95-134">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="70f95-134">.NET version</span></span> | <span data-ttu-id="70f95-135">貼齊套件或頻道</span><span class="sxs-lookup"><span data-stu-id="70f95-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="70f95-136">5.0</span><span class="sxs-lookup"><span data-stu-id="70f95-136">5.0</span></span>          | <span data-ttu-id="70f95-137">`5.0` 或 `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="70f95-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="70f95-138">3.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="70f95-138">3.1 (LTS)</span></span>    | <span data-ttu-id="70f95-139">`3.1` 或 `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="70f95-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="70f95-140">2.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="70f95-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="70f95-141">使用 `snap install` 命令來安裝 .NET SDK 嵌入式管理套件。</span><span class="sxs-lookup"><span data-stu-id="70f95-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="70f95-142">使用 `--channel` 參數來指出要安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="70f95-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="70f95-143">如果省略此參數， `latest/stable` 則會使用。</span><span class="sxs-lookup"><span data-stu-id="70f95-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="70f95-144">在此範例中， `5.0` 指定了：</span><span class="sxs-lookup"><span data-stu-id="70f95-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="70f95-145">接下來， `dotnet` 使用下列命令註冊系統的命令 `snap alias` ：</span><span class="sxs-lookup"><span data-stu-id="70f95-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="70f95-146">此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。</span><span class="sxs-lookup"><span data-stu-id="70f95-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="70f95-147">您可以選擇任何想要 `{alias}` 的名稱。</span><span class="sxs-lookup"><span data-stu-id="70f95-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="70f95-148">例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-sdk.dotnet dotnet50` 。</span><span class="sxs-lookup"><span data-stu-id="70f95-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="70f95-149">當您使用命令時 `dotnet50` ，將會叫用這個特定的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="70f95-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="70f95-150">但是，選擇不同的別名與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會使用命令。</span><span class="sxs-lookup"><span data-stu-id="70f95-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="70f95-151">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="70f95-151">Install the runtime</span></span>

<span data-ttu-id="70f95-152">.NET 執行時間的貼齊套件會各自以自己的套件識別碼發佈。</span><span class="sxs-lookup"><span data-stu-id="70f95-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="70f95-153">下表列出封裝識別碼：</span><span class="sxs-lookup"><span data-stu-id="70f95-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="70f95-154">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="70f95-154">.NET version</span></span>      | <span data-ttu-id="70f95-155">貼齊套件</span><span class="sxs-lookup"><span data-stu-id="70f95-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="70f95-156">5.0</span><span class="sxs-lookup"><span data-stu-id="70f95-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="70f95-157">3.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="70f95-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="70f95-158">3.0</span><span class="sxs-lookup"><span data-stu-id="70f95-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="70f95-159">2.2</span><span class="sxs-lookup"><span data-stu-id="70f95-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="70f95-160">2.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="70f95-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="70f95-161">使用 `snap install` 命令來安裝 .Net 執行時間嵌入式管理套件。</span><span class="sxs-lookup"><span data-stu-id="70f95-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="70f95-162">在此範例中，會安裝 .NET 5.0：</span><span class="sxs-lookup"><span data-stu-id="70f95-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="70f95-163">接下來， `dotnet` 使用下列命令註冊系統的命令 `snap alias` ：</span><span class="sxs-lookup"><span data-stu-id="70f95-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="70f95-164">此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。</span><span class="sxs-lookup"><span data-stu-id="70f95-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="70f95-165">您可以選擇任何想要 `{alias}` 的名稱。</span><span class="sxs-lookup"><span data-stu-id="70f95-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="70f95-166">例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-runtime-50.dotnet dotnet50` 。</span><span class="sxs-lookup"><span data-stu-id="70f95-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="70f95-167">當您使用命令時 `dotnet50` ，將會叫用特定版本的 .net。</span><span class="sxs-lookup"><span data-stu-id="70f95-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="70f95-168">但是，選擇不同的別名與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會有命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="70f95-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="70f95-169">TLS/SSL 憑證錯誤</span><span class="sxs-lookup"><span data-stu-id="70f95-169">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="70f95-170">透過 Snap 安裝 .NET 時，可能會在某些散發版本上找不到 .NET TLS/SSL 憑證，而且您可能會在下列情況收到錯誤 `restore` ：</span><span class="sxs-lookup"><span data-stu-id="70f95-170">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="70f95-171">若要解決此問題，請設定幾個環境變數：</span><span class="sxs-lookup"><span data-stu-id="70f95-171">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="70f95-172">憑證位置會因發行版本而異。</span><span class="sxs-lookup"><span data-stu-id="70f95-172">The certificate location will vary by distro.</span></span> <span data-ttu-id="70f95-173">以下是已遇到問題的散發版本位置。</span><span class="sxs-lookup"><span data-stu-id="70f95-173">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="70f95-174">散發</span><span class="sxs-lookup"><span data-stu-id="70f95-174">Distribution</span></span> | <span data-ttu-id="70f95-175">位置</span><span class="sxs-lookup"><span data-stu-id="70f95-175">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="70f95-176">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="70f95-176">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="70f95-177">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="70f95-177">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="70f95-178">**Solus**</span><span class="sxs-lookup"><span data-stu-id="70f95-178">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="70f95-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="70f95-179">Next steps</span></span>

- [<span data-ttu-id="70f95-180">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="70f95-180">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="70f95-181">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="70f95-181">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
