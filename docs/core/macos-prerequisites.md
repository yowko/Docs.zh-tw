---
title: Mac 上 .NET Core 的先決條件
description: 支援的 macOS 版本和 .NET Core 的相依性，以在 macOS 電腦上開發、部署和執行 .NET Core 應用程式。
author: guardrex
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: bc6e0b20c61c474c7069b757528dbc1ea38354e3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656306"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="a214f-103">macOS 上 .NET Core 的先決條件</span><span class="sxs-lookup"><span data-stu-id="a214f-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="a214f-104">本文章說明在 macOS 電腦上開發、部署和執行 .NET Core 應用程式，所需之支援的 macOS 版本和 .NET Core 的相依性。</span><span class="sxs-lookup"><span data-stu-id="a214f-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="a214f-105">下述支援的 OS 版本與相依性適用於三種在 Mac 上開發 .NET Core 應用程式的方式：透過[命令列搭配您慣用的編輯器](tutorials/using-with-xplat-cli.md)、[Visual Studio Code](https://code.visualstudio.com/) \(英文\)，以及 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)。</span><span class="sxs-lookup"><span data-stu-id="a214f-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="a214f-106">支援的 macOS 版本</span><span class="sxs-lookup"><span data-stu-id="a214f-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a214f-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a214f-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="a214f-108">下列 macOS 版本支援 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="a214f-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="a214f-109">macOS 10.12 "Sierra" (含) 以上版本</span><span class="sxs-lookup"><span data-stu-id="a214f-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="a214f-110">如需 .NET Core 2.1 和 .NET Core 2.2 支援的作業系統完整清單、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結，請參閱 [.NET Core 2.1 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)和 [.NET Core 2.2 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a214f-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="a214f-111">如需下載連結和詳細資訊，請參閱 [.NET Core 2.2 下載](https://www.microsoft.com/net/download/dotnet-core/2.2)或 [.NET Core 2.1 下載](https://www.microsoft.com/net/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="a214f-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a214f-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a214f-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="a214f-113">下列 macOS 版本支援 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="a214f-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="a214f-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="a214f-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="a214f-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="a214f-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="a214f-116">如需 .NET Core 1.1 和 .NET Core 1.0 支援的作業系統完整清單、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結，請參閱 [.NET Core 1.1 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)和 [.NET Core 1.0 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a214f-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="a214f-117">如需下載連結和詳細資訊，請參閱 [.NET Core 1.1 下載](https://www.microsoft.com/net/download/dotnet-core/1.1)或 [.NET Core 1.0 下載](https://www.microsoft.com/net/download/dotnet-core/1.0)。</span><span class="sxs-lookup"><span data-stu-id="a214f-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="a214f-118">.NET Core 3.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="a214f-118">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="a214f-119">下列 macOS 版本支援 .NET Core 3.0 Preview 1：</span><span class="sxs-lookup"><span data-stu-id="a214f-119">.NET Core 3.0 Preview 1 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="a214f-120">macOS 10.12 "Sierra" (含) 以上版本</span><span class="sxs-lookup"><span data-stu-id="a214f-120">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="a214f-121">如需 .NET Core 3.0 支援的作業系統、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結完整清單，請參閱 [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) (.NET Core 3.0 支援的 OS 版本)。</span><span class="sxs-lookup"><span data-stu-id="a214f-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="a214f-122">如需下載連結和詳細資訊，請參閱 [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0) (.NET Core 3.0 下載)。</span><span class="sxs-lookup"><span data-stu-id="a214f-122">For download links and more information, see [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="a214f-123">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="a214f-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a214f-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a214f-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="a214f-125">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a214f-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="a214f-126">如果您在 macOS 上有安裝的問題，請參閱已安裝版本的[已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.1)主題。</span><span class="sxs-lookup"><span data-stu-id="a214f-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a214f-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a214f-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="a214f-128">.NET Core 1.x 在 macOS 上執行時需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="a214f-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="a214f-129">取得 OpenSSL 的其中一個簡單方法是使用適用於 macOS 的 [Homebrew ("brew")](https://brew.sh/) 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="a214f-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="a214f-130">安裝 *brew* 之後，在「終端機」(命令) 提示字元執行下列命令，以安裝 OpenSSL：</span><span class="sxs-lookup"><span data-stu-id="a214f-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="a214f-131">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a214f-131">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="a214f-132">如果您在 macOS 上有安裝的問題，請參閱 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a214f-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="a214f-133">.NET Core 3.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="a214f-133">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="a214f-134">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a214f-134">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="a214f-135">如果您在 macOS 上有安裝的問題，請參閱已安裝版本的[版本資訊](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a214f-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="a214f-136">增加開啟的檔案上限 (.NET Core SDK 2.0.2 之前的 .NET Core 版本)</span><span class="sxs-lookup"><span data-stu-id="a214f-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="a214f-137">在較舊的 .NET Core 版本中 (.NET Core SDK 2.0.2 之前)，macOS 的預設開啟檔案限制可能對一些 .NET Core 工作負載而言不足，例如還原專案或執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="a214f-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="a214f-138">您可以遵循下列步驟來增加此限制：</span><span class="sxs-lookup"><span data-stu-id="a214f-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="a214f-139">使用文字編輯器建立新檔案 _/Library/LaunchDaemons/limit.maxfiles.plist_，並儲存含此內容的檔案：</span><span class="sxs-lookup"><span data-stu-id="a214f-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. <span data-ttu-id="a214f-140">在終端機視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a214f-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="a214f-141">重新啟動 Mac，以套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="a214f-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="a214f-142">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="a214f-142">Visual Studio for Mac</span></span>

<span data-ttu-id="a214f-143">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a214f-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="a214f-144">不過，如果您想要在整合式開發環境中於 Mac 上開發 .NET Core 應用程式，則可以使用 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)。</span><span class="sxs-lookup"><span data-stu-id="a214f-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="a214f-145">使用 Visual Studio for Mac 在 macOS 上進行 .NET Core 開發需具備︰</span><span class="sxs-lookup"><span data-stu-id="a214f-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="a214f-146">支援的 macOS 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="a214f-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="a214f-147">OpenSSL (僅限 .NET Core 1.x；.NET Core 2.x 會使用 macOS 中原生提供的安全性服務)</span><span class="sxs-lookup"><span data-stu-id="a214f-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="a214f-148">適用於 Mac 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a214f-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="a214f-149">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="a214f-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
