---
title: Mac 上 .NET Core 的先決條件
description: 支援的 macOS 版本和 .NET Core 的相依性，以在 macOS 電腦上開發、部署和執行 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318313"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="a761a-103">macOS 上 .NET Core 的先決條件</span><span class="sxs-lookup"><span data-stu-id="a761a-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="a761a-104">本文章說明在 macOS 電腦上開發、部署和執行 .NET Core 應用程式，所需之支援的 macOS 版本和 .NET Core 的相依性。</span><span class="sxs-lookup"><span data-stu-id="a761a-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="a761a-105">下述支援的 OS 版本與相依性適用於三種在 Mac 上開發 .NET Core 應用程式的方式：透過[命令列搭配您慣用的編輯器](tutorials/using-with-xplat-cli.md)、[Visual Studio Code](https://code.visualstudio.com/) \(英文\)，以及 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="a761a-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="downloads-and-dependencies"></a><span data-ttu-id="a761a-106">下載和相依性</span><span class="sxs-lookup"><span data-stu-id="a761a-106">Downloads and dependencies</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="a761a-107">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a761a-107">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="a761a-108">**MacOS 高塞拉里昂（版本10.13）** 和更新版本支援 .net Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="a761a-108">.NET Core 3.0 is supported on **macOS High Sierra (version 10.13)** and later versions.</span></span> <span data-ttu-id="a761a-109">需要**x64** CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="a761a-109">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="a761a-110">從[.Net Core 3.0 下載](https://dotnet.microsoft.com/download/dotnet-core/3.0)頁面下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a761a-110">Download and install the .NET Core SDK from the [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) page.</span></span> <span data-ttu-id="a761a-111">[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)，可取得 .net core 3.0 支援的作業系統完整清單、發行版本與版本、不支援的作業系統版本，以及生命週期原則連結。</span><span class="sxs-lookup"><span data-stu-id="a761a-111">[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="a761a-112">如需已知問題的清單，請參閱[.Net Core 已知問題](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a761a-112">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="a761a-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="a761a-113">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="a761a-114">**MacOS Sierra （版本10.12）** 和更新版本都支援 .net Core 2.2。</span><span class="sxs-lookup"><span data-stu-id="a761a-114">.NET Core 2.2 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="a761a-115">需要**x64** CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="a761a-115">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="a761a-116">從[.Net Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)頁面下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a761a-116">Download and install the .NET Core SDK from the [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) page.</span></span> <span data-ttu-id="a761a-117">[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)，可取得 .net core 2.2 支援的作業系統完整清單、發行版本與版本、不支援的作業系統版本，以及生命週期原則連結。</span><span class="sxs-lookup"><span data-stu-id="a761a-117">[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="a761a-118">如需已知問題的清單，請參閱[.Net Core 已知問題](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a761a-118">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a761a-119">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a761a-119">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a761a-120">**MacOS Sierra （版本10.12）** 和更新版本都支援 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="a761a-120">.NET Core 2.1 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="a761a-121">需要**x64** CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="a761a-121">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="a761a-122">從[.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)頁面下載並安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a761a-122">Download and install the .NET Core SDK from the [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1) page.</span></span> <span data-ttu-id="a761a-123">[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)，可取得 .net core 2.1 支援的作業系統完整清單、發行版本與版本、不支援的作業系統版本，以及生命週期原則連結。</span><span class="sxs-lookup"><span data-stu-id="a761a-123">[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="a761a-124">如需已知問題的清單，請參閱[.Net Core 已知問題](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a761a-124">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span></span>

---

## <a name="libgdiplus"></a><span data-ttu-id="a761a-125">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="a761a-125">libgdiplus</span></span>

<span data-ttu-id="a761a-126">使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="a761a-126">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="a761a-127">取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。</span><span class="sxs-lookup"><span data-stu-id="a761a-127">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="a761a-128">安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="a761a-128">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a><span data-ttu-id="a761a-129">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="a761a-129">Visual Studio for Mac</span></span>

<span data-ttu-id="a761a-130">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a761a-130">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="a761a-131">不過，如果您想要在整合式開發環境中於 Mac 上開發 .NET Core 應用程式，則可以使用 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="a761a-131">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>
