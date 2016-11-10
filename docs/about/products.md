---
title: ".NET 產品"
description: ".NET 產品"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/23/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: 90deb1903eea6ae1336326ca91f1e7863485dfd1

---

# <a name="net-products"></a>.NET 產品

.NET 是用於建置開發人員產品之極具彈性、一般用途且原本就跨平台的[規格](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)。 所有最熱門的應用程式分類都會用到它，包括傳統型、行動、雲端、遊戲和 IoT。

本文使用下列兩個稍微不同的術語：

- 「.NET 產品」：可讓您建置適用於一或多個目標平台的應用程式。
- 「.NET 實作」：執行階段、架構和工具的一些組合，可在依據的產品上執行「.NET 程式碼」。

## <a name="product-categories"></a>產品分類

.NET 產品可用於下列每個產品分類。

### <a name="desktop"></a>桌面

您可以建置適用於 Windows 和 macOS 的傳統型應用程式。

- 使用 [.NET Native](#net-native) 的[通用 Windows 應用程式](https://developer.microsoft.com/windows)
- 使用 [.NET Framework](#net-framework) 的 [Windows Presentation Foundation (WPF)](https://msdn.microsoft.com/library/ms754130.aspx) (適用於 Windows)
- 使用 [.NET Framework](#net-framework) 的 [Windows Form](https://msdn.microsoft.com/library/dd30h2yb.aspx) (適用於 Windows)
- 使用 [Xamarin](#xamarin-sdk) 的 Cocoa (適用於 macOS)
- 使用 [electron-edge](https://github.com/kexplo/electron-edge) 的 [Electron](http://electron.atom.io/) (適用於跨平台傳統型應用程式)

### <a name="games"></a>遊戲

您可以建置適用於許多傳統型、行動、主控台和虛擬/擴增實境裝置的遊戲。

- 使用 [Mono](#mono) 的 [CRYENGINE](http://docs.cryengine.com/display/CEPROG/CE%23+Programming)
- 使用 [Mono](#mono) 的 [MonoGame](http://www.monogame.net/documentation/?page=main)
- 使用 [Mono](#mono) 的 [Unity](http://docs.unity3d.com/Manual/index.html)

### <a name="iot"></a>IoT

您可以建置適用於 Windows 10 IoT 核心版的 IoT 應用程式，包括 Raspberry Pi 2/3。

- 使用 [.NET Native](#net-native) 的 [Windows 10 IoT 核心版](https://developer.microsoft.com/windows/iot)

### <a name="mobile"></a>行動訊息

您可以建置適用於 iOS、Android 和 Windows 的行動應用程式。

- 使用 [Xamarin](#xamarin-sdk) 的 iOS 應用程式
- 使用 [Xamarin](#xamarin-sdk) 的 Android 應用程式
- 使用 [.NET Native](#net-native) 的[通用 Windows 應用程式](https://developer.microsoft.com/windows)

### <a name="web-and-cloud"></a>Web 和雲端

您可以建置適用於 Windows 和 Linux 的 Web 和雲端應用程式。

- 使用 [.NET Framework](#net-framework) 的 [ASP.NET](http://www.asp.net/) (適用於 Windows)
- 使用 [.NET Core](#net-core) 的 [ASP.NET Core](http://docs.asp.net/) (適用於 Windows、macOS 和 Linux)

## <a name="net-implementations"></a>.NET 實作

以下依字母順序列出主要的商業和開放原始碼 .NET 實作。

### <a name="net-core"></a>.NET 核心

.NET Core 可用來建置裝置、Web、雲端和內嵌/IoT 應用程式。 它是[開放原始碼](https://github.com/dotnet/core)且跨平台，支援 Windows、macOS 和 Linux。 [ASP.NET Core](http://docs.asp.net/) 是最熱門的 .NET Core 工作負載。 您可以使用它來建置 Web 應用程式和服務，以便在內部和雲端進行部署。 您也可以使用 .NET Core 來建置工具、公用程式和雲端背景工作應用程式。

- 了解 [.NET Core](../core/index.md)
- 了解 [ASP.NET Core](http://docs.asp.net/)
- [下載 .NET Core](http://dot.net/core)

.NET Core 的主要特性如下：

**跨平台** - .NET Core 支援三個作業系統系列︰Linux、Windows 和 macOS。 .NET Core 應用程式預設為跨平台。 您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。

**開放原始碼** - [.NET Core](https://github.com/dotnet/core) 可在 GitHub 上取得，並經過 [MIT](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) 和 [Apache 2](https://github.com/dotnet/roslyn/blob/master/License.txt) 授權 (授權是針對每個元件)。 文件是 [CC-BY](https://github.com/dotnet/docs/blob/master/license.txt)。 .NET Core 也會使用 [.NET Core 版本資訊](https://github.com/dotnet/core/releases)中所列之一組重要的開放原始碼業界相依性。 

**自然取得** - .NET Core 有多種發佈形式，以符合特定特定開發人員需求。 您可以透過 [.NET Core SDK](https://dot.net/core) 安裝程式 (或 zip)，或是透過作業系統特定的封裝管理員 (例如 APT 和 Yum)，取得 .NET Core。 [官方 .NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)可在 Docker Hub 上取得。 更高階的 Framework 程式庫和較大型的 .NET 程式庫生態系統可在 [NuGet](http://www.nuget.org/) 上取得。 

**模組化平台** - .NET Core 是透過模組化設計所建置，讓應用程式只包含所需的 .NET Core 程式庫和相依性。 每個應用程式可選擇自己的 .NET Core 版本設定，以避免與共用元件發生衝突。 這種方法使用 Docker 等容器技術，確保與開發軟體的趨勢一致。

### <a name="net-framework"></a>.NET Framework

.NET Framework 可用來建置適用於 Windows 和 Windows Server 的應用程式。 您可以使用它並搭配 Windows Presentation Framework (WPF) 和 Windows Form 來建置豐富的使用者介面。 它也支援搭配 ASP.NET Web Form、ASP.NET MVC 和 Windows Communication Framework (WCF) 來建置伺服器應用程式。 Visual Studio 提供豐富的 .NET Framework 設計工具體驗，讓您輕鬆地建置用戶端和伺服器應用程式。 它是撰寫 Windows 應用程式的最佳選擇。

- 了解 [.NET Framework](https://msdn.microsoft.com/library/w0x726c2.aspx)
- [下載 .NET Framework](https://dot.net)

[Windows Form](https://msdn.microsoft.com/library/dd30h2yb.aspx) 可讓您比任何其他技術更快速地建置的「資料表單」桌面 UI。 它使用可拖放 UI 和非 UI 控制項的設計工具，將大多數開發工作減少成單一手勢和概念模型。

[Windows Presentation Foundation (WPF)](https://msdn.microsoft.com/library/ms754130.aspx) 透過 [XAML](https://msdn.microsoft.com/library/ms752059.aspx) 標記語言描述 UI，以分開考量程式碼和 UI。 WPF 極具彈性，需要更複雜之使用者模型或更簡潔之外觀的 UI 通常會會用到它。

[Windows Communication Foundation (WCF)](https://msdn.microsoft.com/library/ms731082.aspx) 是 SOAP Web 服務的一組程式庫。 它可讓您建立服務，這些服務可透過各種支援的通訊協定使用各種資料格式來進行通訊，並可裝載於您選擇的任何處理序中。 這會引進 WCF 的其中一個主要功能︰您的服務不會繫結至任何特定的裝載策略或方法。

[ASP.NET](http://www.asp.net/) 是 Web 架構。 它分成幾個不同部分，以用來產生現代且高效能的 Web 應用程式。 

- [ASP.NET Web Form](http://www.asp.net/web-forms) 可讓您比大多數其他 Web 技術更快速地建置「資料表單」UI，並提供可拖放 Web 控制項的設計工具。 
- [ASP.NET MVC](http://www.asp.net/mvc) 可讓您進一步控制從 HTTP 層到使用者介面的整個 Web 管線。 
- [ASP.NET WebAPI](http://www.asp.net/web-api) 是用於建立 REST 服務的傳統型架構。 
- [SignalR](http://www.asp.net/signalr) 可讓您使用 [WebSocket](https://en.wikipedia.org/wiki/WebSocket) 通訊協定，提供推播型通訊給 Web 應用程式。

### <a name="net-native"></a>.NET Native

.NET Native 是一組適用於 .NET Core 的原生建置工具。 .NET Native 是預先 (AOT) 編譯工具鏈，藉由將 IL 位元組碼編譯為原生機器碼來產生原生應用程式。 這表示產生的二進位檔即為作業系統執行的檔案，不需要 JIT，也不需要執行階段編譯。 這會導致更佳的啟動效能，並帶來一些安全性好處。

.NET Native 主要是由 .NET [通用 Windows 平台 (UWP)](https://msdn.microsoft.com/library/windows/apps/dn726767.aspx) 應用程式使用。

### <a name="mono"></a>Mono

[Mono](http://www.mono-project.com/docs/about-mono/) 是 [Mono Project](http://mono-project.com) 社群之 .NET 的原始開放原始碼和跨平台實作。 它現在是由 Microsoft 贊助。 它可以視為 .NET Framework 的開放和跨平台版本。 其 API 遵循 .NET Framework 的進度，而不是 .NET Core。

組成 Mono 的元件有幾個：

**C# 編譯器** - Mono 的 C# 編譯器是 C# 6 的完整功能。

**Mono 執行階段** - 此執行階段實作 ECMA 通用語言基礎結構 (CLI)。 此執行階段提供 Just-in-Time (JIT) 編譯器、預先 (AOT) 編譯器、程式庫載入器、記憶體回收行程、執行緒系統和互通性功能。

**基底類別庫** - Mono 平台提供一組完整的類別，作為建置應用程式的穩固基礎。 這些類別與 Microsoft 的 .Net Framework 類別相容。

**Mono 類別庫** - 除了 .NET Framework 所提供的基底類別庫之外，Mono 還提供許多類別。 這些類別提供額外的實用功能，尤其是在建置 Linux 應用程式方面。 一些範例包括 Gtk+、ZIP 檔案、LDAP、OpenGL、Cairo、POSIX等類別。

### <a name="xamarin-sdk"></a>Xamarin SDK

[Xamarin SDK](http://open.xamarin.com) 可用來建置原生行動和裝置應用程式，主要是用於 Apple 與 Google 生態系統。 它以 Mono 為基礎，而且是使用 MIT 授權的開放原始碼。 您可以使用它來建置手機、平板電腦和手錶的 iOS 和 Android 應用程式。 [Xamarin.Forms](https://www.xamarin.com/forms) 是撰寫可跨 Apple、Google 和 Windows 應用程式重複使用之 UI 的熱門方式。

- 了解 [Xamarin SDK](https://developer.xamarin.com/)
- [下載 Xamarin](https://www.xamarin.com/platform)



<!--HONumber=Nov16_HO1-->


