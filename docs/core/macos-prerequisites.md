---
title: Mac 上 .NET Core 的先決條件
description: 支援的 macOS 版本和 .NET Core 的相依性，以在 macOS 電腦上開發、部署和執行 .NET Core 應用程式。
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 2644cd491d1d3ba07f48f57fd9416ec84316f7d8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-macos"></a>macOS 上 .NET Core 的先決條件

本文章說明在 macOS 電腦上開發、部署和執行 .NET Core 應用程式，所需之支援的 macOS 版本和 .NET Core 的相依性。 下述支援的 OS 版本與相依性適用於三種在 Mac 上開發 .NET Core 應用程式的方式：透過[命令列搭配您慣用的編輯器](tutorials/using-with-xplat-cli.md)、[Visual Studio Code](https://code.visualstudio.com/) \(英文\)，以及 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。

## <a name="supported-macos-versions"></a>支援的 macOS 版本

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

下列 macOS 版本支援 .NET Core 2.x：

* macOS 10.12 "Sierra" (含) 以上版本

如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

下列 macOS 版本支援 .NET Core 1.x：

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。

---

## <a name="net-core-dependencies"></a>.NET Core 的相依性

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。 如果您在 macOS 上有安裝的問題，請參閱已安裝版本的[已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.x**

.NET Core 1.x 在 macOS 上執行時需要 OpenSSL。 取得 OpenSSL 的其中一個簡單方法是使用適用於 macOS 的 [Homebrew ("brew")](https://brew.sh/) 套件管理員。 安裝 *brew* 之後，在「終端機」(命令) 提示字元執行下列命令，以安裝 OpenSSL：

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

請從 [.NET 下載](https://www.microsoft.com/net/download/core) \(英文\) 下載並安裝 .NET Core SDK。 如果您在 macOS 上有安裝的問題，請參閱 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>增加開啟的檔案上限 (.NET Core SDK 2.0.2 之前的 .NET Core 版本) 

在較舊的 .NET Core 版本中 (.NET Core SDK 2.0.2 之前)，macOS 的預設開啟檔案限制可能對一些 .NET Core 工作負載而言不足，例如還原專案或執行單元測試。

您可以遵循下列步驟來增加此限制：

1. 使用文字編輯器建立新檔案 _/Library/LaunchDaemons/limit.maxfiles.plist_，並儲存含此內容的檔案：

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

2. 在終端機視窗中，執行下列命令：

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. 重新啟動 Mac，以套用這些設定。

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。 不過，如果您想要在整合式開發環境中於 Mac 上開發 .NET Core 應用程式，則可以使用 [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)。 

使用 Visual Studio for Mac 在 macOS 上進行 .NET Core 開發需具備︰

* 支援的 macOS 作業系統版本
* OpenSSL (僅限 .NET Core 1.x；.NET Core 2.x 會使用 macOS 中原生提供的安全性服務)
* 適用於 Mac 的 .NET Core SDK
* [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)
