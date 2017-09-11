---
title: "Mac 上 .NET Core 的先決條件"
description: "支援的 macOS 版本和 .NET Core 的相依性，以在 macOS 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 07/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8feaee2cbfa55e23bd49c0ab76d995f15be343b4
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a><span data-ttu-id="f5239-104">Mac 上 .NET Core 的先決條件</span><span class="sxs-lookup"><span data-stu-id="f5239-104">Prerequisites for .NET Core on Mac</span></span>

<span data-ttu-id="f5239-105">本文章說明在 macOS 電腦上開發、部署和執行 .NET Core 應用程式，所需之支援的 macOS 版本和 .NET Core 的相依性。</span><span class="sxs-lookup"><span data-stu-id="f5239-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="f5239-106">下述支援的 OS 版本與相依性適用於三種在 Mac 上開發 .NET Core 應用程式的方式：透過[命令列搭配您慣用的編輯器](tutorials/using-with-xplat-cli.md)、[Visual Studio Code](https://code.visualstudio.com/) \(英文\)，以及 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。</span><span class="sxs-lookup"><span data-stu-id="f5239-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="f5239-107">支援的 macOS 版本</span><span class="sxs-lookup"><span data-stu-id="f5239-107">Supported macOS versions</span></span>

<span data-ttu-id="f5239-108">下列 macOS 版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="f5239-108">.NET Core is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="f5239-109">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="f5239-109">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="f5239-110">macOS 10.11 "El Capitan" (僅支援 .NET Core 1.x)</span><span class="sxs-lookup"><span data-stu-id="f5239-110">macOS 10.11 "El Capitan" (.NET Core 1.x only)</span></span>

<span data-ttu-id="f5239-111">如需支援的作業系統完整清單，請參閱[支援的 OS 版本](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions)。</span><span class="sxs-lookup"><span data-stu-id="f5239-111">See [Supported OS Versions](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) for the complete list of supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="f5239-112">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="f5239-112">.NET Core dependencies</span></span>

<span data-ttu-id="f5239-113">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="f5239-113">**.NET Core 1.x**</span></span>

<span data-ttu-id="f5239-114">.NET Core 1.x 在 macOS 上執行時需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="f5239-114">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="f5239-115">取得 OpenSSL 的其中一個簡單方法是使用適用於 macOS 的 [Homebrew ("brew")](https://brew.sh/) 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="f5239-115">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="f5239-116">安裝 *brew* 之後，在「終端機」(命令) 提示字元執行下列命令，以安裝 OpenSSL：</span><span class="sxs-lookup"><span data-stu-id="f5239-116">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="f5239-117">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f5239-117">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="f5239-118">如果您在 macOS 上有安裝的問題，請參閱 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。</span><span class="sxs-lookup"><span data-stu-id="f5239-118">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

<span data-ttu-id="f5239-119">**.NET Core 2.x**</span><span class="sxs-lookup"><span data-stu-id="f5239-119">**.NET Core 2.x**</span></span>

<span data-ttu-id="f5239-120">請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f5239-120">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="f5239-121">如果您在 macOS 上有安裝的問題，請參閱已安裝版本的[已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。</span><span class="sxs-lookup"><span data-stu-id="f5239-121">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="f5239-122">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="f5239-122">Visual Studio for Mac</span></span>

<span data-ttu-id="f5239-123">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5239-123">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="f5239-124">不過，如果您想要在整合式開發環境中於 Mac 上開發 .NET Core 應用程式，則可以使用 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。</span><span class="sxs-lookup"><span data-stu-id="f5239-124">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="f5239-125">使用 Visual Studio for Mac 在 macOS 上進行 .NET Core 開發需具備︰</span><span class="sxs-lookup"><span data-stu-id="f5239-125">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="f5239-126">支援的 macOS 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="f5239-126">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="f5239-127">OpenSSL (僅限 .NET Core 1.x；.NET Core 2.x 會使用 macOS 中原生提供的安全性服務)</span><span class="sxs-lookup"><span data-stu-id="f5239-127">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="f5239-128">適用於 Mac 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f5239-128">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="f5239-129">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="f5239-129">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

