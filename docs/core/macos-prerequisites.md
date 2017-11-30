---
title: "Mac 上 .NET Core 的先決條件"
description: "支援的 macOS 版本和 .NET Core 的相依性，以在 macOS 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 16f3cfd482bddfff1b9ad56e7ffe58ae2aed4980
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="18121-104">適用於.NET Core macOS 上的必要條件</span><span class="sxs-lookup"><span data-stu-id="18121-104">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="18121-105">本文章說明在 macOS 電腦上開發、部署和執行 .NET Core 應用程式，所需之支援的 macOS 版本和 .NET Core 的相依性。</span><span class="sxs-lookup"><span data-stu-id="18121-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="18121-106">下述支援的 OS 版本與相依性適用於三種在 Mac 上開發 .NET Core 應用程式的方式：透過[命令列搭配您慣用的編輯器](tutorials/using-with-xplat-cli.md)、[Visual Studio Code](https://code.visualstudio.com/) \(英文\)，以及 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。</span><span class="sxs-lookup"><span data-stu-id="18121-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="18121-107">支援的 macOS 版本</span><span class="sxs-lookup"><span data-stu-id="18121-107">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18121-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18121-108">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="18121-109">.NET core 2.x 支援下列版本的 macOS:</span><span class="sxs-lookup"><span data-stu-id="18121-109">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="18121-110">macOS 10.12"利也"和更新版本</span><span class="sxs-lookup"><span data-stu-id="18121-110">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="18121-111">如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="18121-111">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18121-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18121-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="18121-113">.NET core 1.x 支援 macOS 下列版本：</span><span class="sxs-lookup"><span data-stu-id="18121-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="18121-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="18121-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="18121-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="18121-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="18121-116">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="18121-116">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="18121-117">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="18121-117">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18121-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18121-118">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="18121-119">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="18121-119">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="18121-120">如果您在 macOS 上有安裝的問題，請參閱已安裝版本的[已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。</span><span class="sxs-lookup"><span data-stu-id="18121-120">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18121-121">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18121-121">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="18121-122">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="18121-122">**.NET Core 1.x**</span></span>

<span data-ttu-id="18121-123">.NET Core 1.x 在 macOS 上執行時需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="18121-123">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="18121-124">取得 OpenSSL 的其中一個簡單方法是使用適用於 macOS 的 [Homebrew ("brew")](https://brew.sh/) 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="18121-124">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="18121-125">安裝 *brew* 之後，在「終端機」(命令) 提示字元執行下列命令，以安裝 OpenSSL：</span><span class="sxs-lookup"><span data-stu-id="18121-125">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="18121-126">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="18121-126">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="18121-127">如果您在 macOS 上有安裝的問題，請參閱 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。</span><span class="sxs-lookup"><span data-stu-id="18121-127">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit"></a><span data-ttu-id="18121-128">增加開啟檔案上限</span><span class="sxs-lookup"><span data-stu-id="18121-128">Increase the maximum open file limit</span></span>

<span data-ttu-id="18121-129">MacOS 的預設開啟的檔案限制可能無法完全針對.NET 核心工作負載，例如還原專案或執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="18121-129">The default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="18121-130">您可以增加此限制，依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="18121-130">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="18121-131">使用文字編輯器中，建立新的檔案_/Library/LaunchDaemons/limit.maxfiles.plist_，此內容中儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="18121-131">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="18121-132">在終端機視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="18121-132">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="18121-133">重新啟動才能套用這些設定 Mac。</span><span class="sxs-lookup"><span data-stu-id="18121-133">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="18121-134">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="18121-134">Visual Studio for Mac</span></span>

<span data-ttu-id="18121-135">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="18121-135">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="18121-136">不過，如果您想要在整合式開發環境中於 Mac 上開發 .NET Core 應用程式，則可以使用 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。</span><span class="sxs-lookup"><span data-stu-id="18121-136">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="18121-137">使用 Visual Studio for Mac 在 macOS 上進行 .NET Core 開發需具備︰</span><span class="sxs-lookup"><span data-stu-id="18121-137">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="18121-138">支援的 macOS 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="18121-138">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="18121-139">OpenSSL (僅限 .NET Core 1.x；.NET Core 2.x 會使用 macOS 中原生提供的安全性服務)</span><span class="sxs-lookup"><span data-stu-id="18121-139">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="18121-140">適用於 Mac 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="18121-140">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="18121-141">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="18121-141">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)
