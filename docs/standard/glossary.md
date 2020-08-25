---
title: .NET 字彙表
description: 了解 .NET 文件中所使用之特定詞彙的意義。
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: c984a29208d8680de3c04f6b4d16c6f41afedc71
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812337"
---
# <a name="net-glossary"></a>.NET 字彙表

此字彙表的主要目標是釐清經常出現在 .NET 文件中但沒有定義之特定詞彙和縮略字的意義。

## <a name="aot"></a>AOT

預先編譯器。

此編譯器類似於 [JIT](#jit)，也會將 [IL](#il) 轉譯成機器碼。 相較於 JIT 編譯，AOT 編譯會在執行應用程式之前發生，而且通常會在不同的電腦上執行。 因為 AOT 工具鏈不會在執行時間編譯，所以不需要將編譯花費的時間降到最低。 這表示它們可以花更多的時間在最佳化。 由於 AOT 的內容是整個應用程式，因此 AOT 編譯器也會執行跨模組連結和整個程式分析，這表示會追蹤所有參考並產生單一可執行檔。

請參閱 [CoreRT](#corert) 及 [.NET Native](#net-native)。

## <a name="aspnet"></a>ASP.NET

隨附於 .NET Framework 的原始 ASP.NET 實作。

有時 ASP.NET 是指包括 ASP.NET Core 在內之兩個 ASP.NET 實作的籠統名詞。 該詞彙在任何指定的執行個體中所代表的意義取決於內容。 如果您想要清楚說您不是使用 ASP.NET 來表示這兩個執行，請參閱 ASP.NET 4.x。

請參閱 [ASP.NET 文件](/aspnet/#pivot=aspnet)。

## <a name="aspnet-core"></a>ASP.NET Core

ASP.NET 的跨平臺、高效能、開放原始碼的實作為。

請參閱 [ASP.NET Core 文件](/aspnet/#pivot=core)。

## <a name="assembly"></a>組件 (assembly)

*.Dll* / *.exe*檔，可包含可由應用程式或其他元件呼叫的 api 集合。

一個組件可以包含介面、類別、結構、列舉和委派等類型。 專案的 *bin* 資料夾中的組件有時稱為「二進位檔」**。 另請參閱[程式庫](#library)。

## <a name="bcl"></a>B c l

基類庫。 也稱為 *架構程式庫*。

組成系統的一組程式庫。 \* (以及 Microsoft 的範圍有限。 \*) 命名空間。 BCL 是 ASP.NET Core 等較高層級的應用程式架構建置所在之較低層級的一般目的架構。

.Net [5 和更新版本的 BCL 原始程式碼 (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions) 包含在 [.net 運行](https://github.com/dotnet/runtime)時間存放庫中。 這項較新的 .NET 執行的 BCL Api 大部分也都可在 .NET Framework 中使用，因此您可以將此原始程式碼視為 .NET Framework BCL 原始程式碼的分支。

## <a name="clr"></a>CLR

Common Language Runtime。

確切的意義取決於內容。 Common Language Runtime 通常是指 [.NET Framework](#net-framework) 的執行時間或 [.net 5 和更新版本的執行時間 (包括 .net Core 2.1-3.1) ](#net-5-and-later-versions)。

CLR 會處理記憶體配置和管理。 CLR 也是虛擬機器，不僅可執行應用程式，也會使用 [JIT](#jit) 編譯器來即時產生和編譯器代碼。

.NET Framework 的 CLR 實作為僅限 Windows。

適用于 .NET 5 和更新版本的 CLR 實 (也稱為核心 CLR) 是從與 .NET Framework CLR 相同的程式碼基底所建立。 核心 CLR 原本是 Silverlight 的執行時間，其設計目的是要在多個平臺上執行，特別是 Windows 和 OS X。它仍然是一種 [跨平臺](#cross-platform) 的執行時間，現在包含許多 Linux 發行版本的支援。

另請參閱 [運行](#runtime)時間。

## <a name="core-clr"></a>核心 CLR

適用于 [.net 5 和更新版本的 Common Language Runtime (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions)。

請參閱 [CLR](#clr)

## <a name="corert"></a>CoreRT

相較于 [CLR](#clr)，CoreRT 不是虛擬機器，這表示它不包含可即時產生和執行程式碼的功能，因為它不包含 [JIT](#jit)。 不過，它確實包含 [GC](#gc) ，以及執行時間類型識別 (RTTI) 和反映的能力。 不過，其型別系統已設計成不需要反映的中繼資料。 不需要中繼資料可讓 [AOT](#aot) 工具鏈連結到多餘的中繼資料， (更重要的是) 識別應用程式未使用的程式碼。 CoreRT 正在開發中。

請參閱 [.NET Native 和 CoreRT 簡介](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)。

## <a name="cross-platform"></a>跨平台

開發和執行應用程式的能力，可用於多個不同的作業系統（例如 Linux、Windows 和 iOS），而不需要特別針對每個作業系統進行重寫。 這可讓您在不同平臺上的應用程式之間重複使用程式碼和一致性。

## <a name="ecosystem"></a>生態系統

用來建置及執行適用於指定技術之應用程式的所有執行階段軟體、開發工具和社群資源。

「.NET 生態系統」一詞與「.NET 堆疊」等類似詞彙的不同之處在於，前者包含協力廠商應用程式和程式庫。 以下是用於句子中的範例：

- 「[.NET Standard](#net-standard) 背後的動機是在 .NET 生態系統中建立更高的一致性。」

## <a name="framework"></a>架構

一般而言，一組功能齊全的 API 可加快開發和部署以特定技術為基礎的應用程式。 ASP.NET Core 和 Windows Forms 即為此一般意義的應用程式架構範例。 另請參閱[程式庫](#library)。

"Framework" 這個字在下列詞彙中有不同的意義：

- [.NET Framework](#net-framework)
- [目標 framework](#target-framework)
- [TFM (目標 Framework Moniker)](#tfm)
- [與 framework 相依的應用程式](../core/deploying/index.md#publish-framework-dependent)

在舊版 .NET 檔中，「架構」有時是指 [.net 的實](#implementation-of-net)。 例如，文章可能會呼叫 .NET 5 架構。

## <a name="gc"></a>GC

記憶體回收行程。

記憶體回收行程是自動記憶體管理的實作。  GC 會釋放不再使用之物件所佔用的記憶體。

請參閱[記憶體回收](garbage-collection/index.md)。

## <a name="il"></a>IL

中繼語言。

較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。 IL 有時稱為 MSIL (Microsoft IL) 或 CIL (Common IL)。

## <a name="jit"></a>JIT

Just-in-Time 編譯器。

此編譯器類似於 [AOT](#aot)，會將 [IL](#il) 轉譯成處理器了解的機器碼。 不同於 AOT，JIT 編譯會視需要發生，而且會在必須執行程式碼的相同電腦上執行。 由於 JIT 編譯會在應用程式執行期間發生，因此編譯時間會是執行階段的一部分。 因此，JIT 編譯器必須在最佳化程式碼所花費的時間與結果程式碼可能省下的時間之間取得平衡。 但 JIT 知道實際硬體，因此開發人員不需要提供不同的實作。

## <a name="implementation-of-net"></a>.NET 實作

.NET 的執行包括：

- 一或多個執行階段。 範例： [CLR](#clr)、 [CoreRT](#corert)。
- 實作 .NET Standard 版本並可能包含其他 API 的類別庫。 範例：適用于[.NET Framework](#net-framework)的[BCLs](#bcl)和[.net 5 和更新版本 (包括 .net Core 2.1-3.1) ](#net-5-and-later-versions)。
- (選擇性) 一或多個應用程式架構。 範例： [ASP.NET](#aspnet)、WINDOWS FORMS 和 WPF 包含在 .NET FRAMEWORK 和 .net 5 中。
- (選擇性) 開發工具。 某些開發工具可在多個實作之間共用。

.NET 實作的範例：

- [.NET Framework](#net-framework)
- [.NET 5 和更新版本 (包括 .NET Core 2.1-3。1](#net-5-and-later-versions)
- [通用 Windows 平台 (UWP)](#uwp)
- [Mono](#mono)

## <a name="library"></a>圖書館

可由應用程式或其他程式庫呼叫的 API 集合。 .NET 程式庫是由一或多個[組件](#assembly)組成。

程式庫和[架構](#framework)等字在使用時通常同義。

## <a name="mono"></a>Mono

Mono 是開放原始碼、[跨平台](#cross-platform)的 .NET 實作，主要用於需要小型執行階段時。 它是在 Android、Mac、iOS、tvOS 和 watchOS 上提供 Xamarin 應用程式的執行時間，主要著重于需要少量資源的應用程式。

它支援目前發行的所有 .NET Standard 版本。

在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。 它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。

Mono 通常與 [即時編譯器](#jit)搭配使用，但也提供完整的 [靜態編譯器 (預先編譯) ](#aot) ，可在 iOS 等平臺上使用。

請參閱 [Mono 檔](https://www.mono-project.com/docs/)。

## <a name="net"></a>.NET

[.NET Standard](#net-standard) 以及所有 [.NET 實作](#implementation-of-net)和工作負載的籠統詞彙。 一律為完全大寫，絕對不會是 ".Net"。

當 [.net 5](#net-5-and-later-versions) (目前處於) 預覽狀態時，系統會針對所有新的 .net 開發建議使用 .net，因此在某些內容中，".net" 將表示「.net 5 和更新版本」。

請參閱 [.net 指南](index.yml)

## <a name="net-5-and-later-versions"></a>.NET 5 和更新版本

.NET 的跨平臺、高效能、開放原始碼的實作為。 包括 Common Language Runtime ([CLR](#clr)) 、 ([CoreRT](#corert)的[AOT](#aot)執行時間、開發) 、基類庫 ([BCL](#bcl)) 和[.net SDK](#net-sdk)。

此 .NET 實作為較早的版本，稱為 .NET Core。 .NET 5.0 是 .NET Core 3.1 之後的下一版。 已略過第4版，以避免使用較舊的實作為（稱為 [.NET Framework](#net-framework)）來混淆這項較新的 .net 執行。 .NET Framework 目前的版本為4.8。

請參閱 [.net](../core/index.yml)。

## <a name="net-cli"></a>.NET CLI

適用于開發 .Net 5 和更新版本之應用程式和程式庫的跨平臺工具鏈， [ (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions)。 也稱為 .NET Core CLI。

請參閱 [.NET CLI](../core/tools/index.md)。

## <a name="net-core"></a>.NET Core

請參閱 [.net 5 和更新版本](#net-5-and-later-versions)。

## <a name="net-framework"></a>.NET Framework

只會在 Windows 上執行的 .NET 實作。 包括 Common Language Runtime ([CLR](#clr)) 、基類庫 ([BCL](#bcl)) 和應用程式架構程式庫（例如 [ASP.NET](#aspnet)、Windows Forms 和 WPF）。

請參閱 [.NET Framework 指南](../framework/index.yml)。

## <a name="net-native"></a>.NET Native

產生原生程式碼提前 ([AOT](#aot)) 的編譯器工具鏈，而非即時 ([JIT](#jit)) 。

編譯會在開發人員的電腦上發生，其運作方式類似於 C++ 編譯器和連結器。 它會移除未使用的程式碼，並花更多時間在最佳化。 它會從程式庫擷取程式碼，並將其合併成可執行檔。 結果會是代表整個應用程式的單一模組。

UWP 是 .NET Native 第一個支援的應用程式架構。 現在，我們支援建置適用於 Windows、macOS 和 Linux 的原生主控台應用程式。

請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)

## <a name="net-sdk"></a>.NET SDK

一組程式庫和工具，可讓開發人員建立 .net 5 和更新版本的 .NET 應用程式和程式庫 [ (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions)。 也稱為 .NET Core SDK。

包含用來建立應用程式的 [.NET CLI](#net-cli) 、用來建立和執行應用程式的 .net 程式庫和執行時間，以及 dotnet 可執行檔 (*dotnet.exe* 執行 CLI 命令和執行應用程式的) 。

請參閱 [.NET SDK 總覽](../core/sdk.md)。

## <a name="net-standard"></a>.NET Standard

可用於每個 .NET 實作之 .NET API 的型式規格。

.NET Standard 規格在文件中有時稱為程式庫。 由於程式庫不只包含規格 (介面)，還包含 API 實作，因此將 .NET Standard 稱為「程式庫」會造成誤導。

請參閱 [.NET Standard](net-standard.md)。

## <a name="ngen"></a>NGEN

原生 (映像) 產生。

您可以將這項技術視為持續性 [JIT](#jit) 編譯器。 它通常會在執行程式碼的電腦上編譯程式碼，但編譯通常會發生在安裝期間。

## <a name="package"></a>套件

NuGet 套件 (簡稱套件) 是 *.zip* 檔案，其中包含一或多個同名組件及其他中繼資料 (例如作者名稱)。

*.zip* 檔案包含一個 *.nupkg* 延伸模組和許多特定資產 (例如 *.dll* 檔案和 *.xml* 檔案)，可搭配多個架構和版本使用。 安裝於應用程式或程式庫時，會根據應用程式或程式庫所指定的目標 Framework 來選取適當的資產。 定義介面的資產位於 *ref* 資料夾中，而定義實作的資產則位於 *lib* 資料夾中。

## <a name="platform"></a>平台

作業系統及其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。

以下是用於句子中的範例：

- 「.NET Core 是 .NET 的跨平台實作。」
- 「PCL 設定檔代表 Microsoft 平台，而 .NET Standard 則無從驗證平台。」

舊版 .NET 檔有時會使用 ".NET platform" 來表示 .NET 或 .NET [stack](#stack)的執行，包括所有[的實](#implementation-of-net)作為。 這兩種使用方式通常會與主要 (作業系統/硬體) 含意混淆，因此我們會嘗試避免這些使用方式。

「平臺」在「開發人員平臺」一詞中有不同的意義，這是指提供建立和執行應用程式之工具和程式庫的軟體。 .NET 是一種跨平臺的開放原始碼開發人員平臺，可用於建立許多不同類型的應用程式。

## <a name="runtime"></a>執行階段

一般情況下，受管理程式的執行環境。 OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。 以下是 .NET 執行時間的一些範例：

- Common Language Runtime ([CLR](#clr)) 
- .NET Native (適用於 UWP)
- Mono 執行階段

"Runtime" 這個字在下列內容中有不同的意義：

* [.Net 下載頁面](https://dotnet.microsoft.com/download)。

  此處的「執行時間」表示 [CLR](#clr) 與 [BCL](#bcl) (framework 程式庫) ，您可以在電腦上下載並安裝該程式庫，讓您可以在電腦上執行與 [framework 相依](../core/deploying/index.md#publish-framework-dependent) 的應用程式。

* [.Net 5 和更新版本 (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions) [ (RID) 的執行時間識別碼](../core/rid-catalog.md)。

  此處的「執行時間」表示 .NET 應用程式執行所在的作業系統平臺和 CPU 架構，例如： `linux-x64` 。

舊版 .NET 檔有時候會使用「執行時間」，以 [實現 .net](#implementation-of-net)的意義，如下列範例所示：

- 「不同的 .NET 執行階段會實作特定版本的 .NET Standard。」
- 「要在多個執行階段上執行的程式庫應以此架構為目標。」 (指的是 .NET Standard)
- 「不同的 .NET 執行階段會實作特定版本的 .NET Standard。 … 每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本...」

## <a name="stack"></a>堆疊

可搭配使用以建置及執行應用程式的一組程式設計技術。

「.NET 堆疊」是指 .NET Standard 和所有 .NET 實作。 「一個 .NET 堆疊」一詞可能是指 .NET 的一項實作。

## <a name="target-framework"></a>Target Framework - 目標 Framework

.NET 應用程式或程式庫依賴的 API 集合。

應用程式或程式庫可以將目標設為某個版本的 .NET Standard (例如 .NET Standard 2.0) ，這是一組標準化的 Api，適用于所有 .NET 執行。 應用程式或程式庫也可以將目標設為某個版本的特定 .NET 實作；在此情況下，它可以存取實作特定的 API。 例如，以 Xamarin.iOS 為目標的應用程式可以存取 Xamarin 提供的 iOS API 包裝函式。

針對某些目標 Framework (例如 .NET Framework)，可用的 API 是由 .NET 實作安裝在系統上的組件所定義，這可能包含應用程式架構 API (例如 ASP.NET、WinForms)。 針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，架構 API 是由安裝在應用程式或程式庫中的套件所定義。 在此情況下，目標架構會隱含地指定參考所有封裝的封裝，這些封裝會組成架構。

請參閱[目標 Framework](frameworks.md)。

## <a name="tfm"></a>TFM

目標 Framework Moniker。

用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。 目標 Framework 通常會由簡短名稱參考，例如 `net462`。 雖然有完整格式的 TFM (例如 .NETFramework,Version=4.6.2)，但通常不會用來指定目標 Framework。

請參閱[目標 Framework](frameworks.md)。

## <a name="uwp"></a>UWP

通用 Windows 平台。

用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。 它是設計來統一您可能想要鎖定的不同裝置類型，包括電腦、平板電腦、手機，甚至是 Xbox。 UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。 您可以用 c + +、c #、Visual Basic 和 JavaScript 來撰寫應用程式。 使用 c # 和 Visual Basic 時，.net Api 是由 .NET 5 和更新版本所提供， (包括 .NET Core 2.1-3.1) 。

## <a name="see-also"></a>另請參閱

- [.NET 指南](index.yml)
- [.NET Framework 指南](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [ASP.NET 總覽](/aspnet/index#pivot=aspnet)
- [ASP.NET Core 總覽](/aspnet/index#pivot=core)
