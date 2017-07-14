---
title: "Mac 上 .NET Core 的先決條件 | Microsoft Docs"
description: "支援的 macOS 版本和 .NET Core 的相依性，以在 macOS 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: 83200e452bccc20bfa82d94899514019e9d05a23
ms.openlocfilehash: 2aa685751fae9fa9771fa1cd86d211f742e06932
ms.contentlocale: zh-tw
ms.lasthandoff: 07/05/2017

---

# Mac 上 .NET Core 的先決條件
<a id="prerequisites-for-net-core-on-mac" class="xliff"></a>

本文章說明在 macOS 電腦上開發、部署和執行 .NET Core 應用程式，所需之支援的 macOS 版本和 .NET Core 的相依性。 下述支援的 OS 版本與相依性適用於三種在 Mac 上開發 .NET Core 應用程式的方式：透過[命令列搭配您慣用的編輯器](tutorials/using-with-xplat-cli.md)、[Visual Studio Code](https://code.visualstudio.com/) \(英文\)，以及 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。

## 支援的 macOS 版本
<a id="supported-macos-versions" class="xliff"></a>

下列 macOS 版本支援 .NET Core：

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

如需完整的支援作業系統清單，請參閱 [.NET Core 版本資訊 (英文)](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)。

## .NET Core 的相依性
<a id="net-core-dependencies" class="xliff"></a>

**.NET Core 1.x**

.NET Core 1.x 在 macOS 上執行時需要 OpenSSL。 取得 OpenSSL 的其中一個簡單方法是使用適用於 macOS 的 [Homebrew ("brew")](https://brew.sh/) 套件管理員。 安裝 *brew* 之後，在「終端機」(命令) 提示字元執行下列命令，以安裝 OpenSSL：

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。 如果您在 macOS 上遇到安裝的問題，請參閱 [Known issues & workarounds](https://github.com/dotnet/core/blob/master/cli/known-issues.md) (已知問題及因應措施) 主題。

**.NET Core 2.x**

請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。 如果您在 macOS 上遇到安裝的問題，請參閱 [Known issues & workarounds](https://github.com/dotnet/core/blob/master/cli/known-issues.md) (已知問題及因應措施) 主題。

## Visual Studio for Mac
<a id="visual-studio-for-mac" class="xliff"></a>

使用 Visual Studio for Mac 在 macOS 上進行 .NET Core 開發需具備︰

* 支援的 macOS 作業系統版本
* OpenSSL (僅限 .NET Core 1.x；.NET Core 2.x 會使用 macOS 中原生提供的安全性服務)
* 適用於 Mac 的 .NET Core SDK
* [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

