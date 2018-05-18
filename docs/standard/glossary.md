---
title: .NET 字彙表
description: 了解 .NET 文件中所使用之特定詞彙的意義。
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 195fbb799432b9d01a5faf301c9f8f2d1edfa1ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="net-glossary"></a>.NET 字彙表

此字彙表的主要目標是釐清經常出現在 .NET 文件中但沒有定義之特定詞彙和縮略字的意義。

## <a name="aot"></a>AOT

預先編譯器。

此編譯器類似於 [JIT](#jit)，也會將 [IL](#il) 轉譯成機器碼。 相較於 JIT 編譯，AOT 編譯會在執行應用程式之前發生，而且通常會在不同的電腦上執行。 由於 AOT 工具鏈不在執行階段編譯，因此不需要縮短花在編譯的時間。 這表示它們可以花更多的時間在最佳化。 由於 AOT 的內容是整個應用程式，因此 AOT 編譯器也會執行跨模組連結和整個程式分析，這表示會追蹤所有參考並產生單一可執行檔。

## <a name="aspnet"></a>ASP.NET 

隨附於 .NET Framework 的原始 ASP.NET 實作。

有時 ASP.NET 是指包括 ASP.NET Core 在內之兩個 ASP.NET 實作的籠統名詞。 該詞彙在任何指定的執行個體中所代表的意義取決於內容。 當想要澄清您不是使用 ASP.NET 來表示這兩種實作時，請參閱 ASP.NET 4.x。 

請參閱 [ASP.NET 文件](/aspnet/#pivot=aspnet)。

## <a name="aspnet-core"></a>ASP.NET Core

建置於 .NET Core 之 ASP.NET 的跨平台、高效能、開放原始碼實作。

請參閱 [ASP.NET Core 文件](/aspnet/#pivot=core)。

## <a name="assembly"></a>組件

可以包含可由應用程式或其他組件呼叫之 API 集合的 *.dll*/*.exe* 檔案。

一個組件可以包含介面、類別、結構、列舉和委派等類型。 專案的 *bin* 資料夾中的組件有時稱為「二進位檔」。 另請參閱[程式庫](#library)。

## <a name="clr"></a>CLR

Common Language Runtime。

確切意義取決於內容，但這通常是指 .NET Framework 的執行階段。 CLR 會處理記憶體配置和管理。 CLR 也是虛擬機器，它不只會執行應用程式，也會使用 JIT 編譯器即時產生和編譯程式碼。 目前的 Microsoft CLR 實作僅限 Windows。

## <a name="coreclr"></a>CoreCLR

.NET Core Common Language Runtime。

此 CLR 是從與 CLR 相同的程式碼基底所建置。 一開始，CoreCLR 是 Silverlight 的執行階段，其設計目的是為了在多個平台上執行，特別是 Windows 和 OS X。CoreCLR 現在是 .NET Core 的一部分，代表 CLR 的簡化版本。 它仍然是跨平台執行階段，現在支援許多 Linux 發行版本。 CoreCLR 也是具有 JIT 和程式碼執行功能的虛擬機器。

## <a name="corefx"></a>CoreFX

.NET Core 基底類別庫 (BCL)

由 System.* (以及一定範圍內的 Microsoft.*) 命名空間組成的一組程式庫。 BCL 是 ASP.NET Core 等較高層級的應用程式架構建置所在之較低層級的一般目的架構。 .NET Core BCL 的原始程式碼包含在 [CoreFX 存放庫](https://github.com/dotnet/corefx)中。 不過，大多數的 .NET Core API 也適用於 .NET Framework；因此您可以將 CoreFX 視為 .NET Framework BCL 的分支。

## <a name="corert"></a>CoreRT

.NET Core 執行階段。

相較於 CLR/CoreCLR，CoreRT 不是虛擬機器，這表示它不會包含即時產生和執行程式碼的功能，因為它不包含 [JIT](#jit)。 不過，它包含 [GC](#gc)，以及執行階段類型識別 (RTTI) 和反映功能。 不過，其型別系統已設計成不需要反映的中繼資料。 這讓 [AOT](#aot) 工具鏈能夠抽離不必要的中繼資料，更重要的是，它能夠識別應用程式未使用的程式碼。 CoreRT 正在開發中。

請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)

## <a name="ecosystem"></a>生態系統

用來建置及執行適用於指定技術之應用程式的所有執行階段軟體、開發工具和社群資源。

「.NET 生態系統」一詞與「.NET 堆疊」等類似詞彙的不同之處在於，前者包含協力廠商應用程式和程式庫。 以下是用於句子中的範例：

- 「[.NET Standard](#net-standard) 背後的動機是在 .NET 生態系統中建立更高的一致性。」 

## <a name="framework"></a>架構

一般而言，一組功能齊全的 API 可加快開發和部署以特定技術為基礎的應用程式。 ASP.NET Core 和 Windows Forms 即為此一般意義的應用程式架構範例。 另請參閱[程式庫](#library)。

「架構」一字在下列詞彙中有更特定的技術意義：
* [.NET Framework](#net-framework)
* [目標 Framework](#target-framework)
* [TFM (目標 Framework Moniker)](#tfm)

在現有的文件中，「架構」有時是指 [.NET 實作](#implementation-of-net)。 例如，某篇文章可能會將 .NET Core 稱為架構。 我們計劃從文件中排除這個令人混淆的用法。

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

.NET 實作包括：

- 一或多個執行階段。 範例：CLR、CoreCLR、CoreRT。
- 實作 .NET Standard 版本並可能包含其他 API 的類別庫。 範例：.NET Framework 基底類別庫、.NET Core 基底類別庫。
- (選擇性) 一或多個應用程式架構。 範例：ASP.NET、Windows Forms 和 WPF 會包含在 .NET Framework 中。
- (選擇性) 開發工具。 某些開發工具可在多個實作之間共用。

.NET 實作的範例：

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [通用 Windows 平台 (UWP)](#uwp)

## <a name="library"></a>程式庫

可由應用程式或其他程式庫呼叫的 API 集合。 .NET 程式庫是由一或多個[組件](#assembly)組成。

程式庫和[架構](#framework)等字在使用時通常同義。

## <a name="metapackage"></a>中繼套件

沒有自己的程式庫，而只是一份相依性清單的 NuGet 套件。 內含的套件可以選擇性地建立目標 Framework 的 API。

請參閱[套件、中繼套件和架構](../core/packages.md)

## <a name="mono"></a>Mono

Mono 是需要小型執行階段時主要使用的 .NET 實作。 它是支援 Android、Mac、iOS、tvOS 和 watchOS 版 Xamarin 應用程式的執行階段，而且主要著重在資源使用量較少的應用程式。

它支援目前發行的所有 .NET Standard 版本。

在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。 它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。

Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。

若要深入了解 Mono，請參閱 [Mono 文件](https://www.mono-project.com/docs/)。

## <a name="net"></a>.NET

[.NET Standard](#net-standard) 以及所有 [.NET 實作](#implementation-of-net)和工作負載的籠統詞彙。 一律為大寫，絕對不會是 ".Net"。

請參閱 [.NET 指南](index.md)

## <a name="net-core"></a>.NET Core 

.NET 的跨平台、高效能、開放原始碼實作。 包括 Core Common Language Runtime (CoreCLR)、Core AOT 執行階段 (CoreRT 開發中)、Core 基底類別庫，以及 Core SDK。

請參閱 [.NET Core](../core/index.md)。

## <a name="net-core-cli"></a>.NET Core CLI

用於開發 .NET Core 應用程式的跨平台工具鏈。

請參閱 [.NET Core 命令列介面 (CLI) 工具](../core/tools/index.md)。

## <a name="net-core-sdk"></a>.NET Core SDK

可讓開發人員建立 .NET Core 應用程式和程式庫的一組程式庫和工具。 包括用於建置應用程式的 [.NET Core CLI](#net-core-cli)、用於建置及執行應用程式的 .NET Core 程式庫和執行階段，以及執行 CLI 命令及執行應用程式的 dotnet 可執行檔 (*dotnet.exe*)。

請參閱 [.NET Core SDK 概觀](../core/sdk.md)。

## <a name="net-framework"></a>.NET Framework

只會在 Windows 上執行的 .NET 實作。 包括 Common Language Runtime (CLR)、基底類別庫，以及 ASP.NET、Windows Forms 和 WPF 等應用程式架構程式庫。

請參閱 [.NET Framework 指南](../framework/index.md)。

## <a name="net-native"></a>.NET Native

產生機器碼預先編譯 (AOT) 而不是 Just-In-Time (JIT) 的編譯器工具鏈。

編譯會在開發人員的電腦上發生，其運作方式類似於 C++ 編譯器和連結器。 它會移除未使用的程式碼，並花更多時間在最佳化。 它會從程式庫擷取程式碼，並將其合併成可執行檔。 結果會是代表整個應用程式的單一模組。

UWP 是 .NET Native 第一個支援的應用程式架構。 現在，我們支援建置適用於 Windows、macOS 和 Linux 的原生主控台應用程式。

請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)

## <a name="net-standard"></a>.NET Standard

可用於每個 .NET 實作之 .NET API 的型式規格。

.NET Standard 規格在文件中有時稱為程式庫。 由於程式庫不只包含規格 (介面)，還包含 API 實作，因此將 .NET Standard 稱為「程式庫」會造成誤導。 我們計劃從文件中排除該用法，只有參考 .NET Standard 中繼套件的名稱 (`NETStandard.Library`) 時除外。

請參閱 [.NET Standard](net-standard.md)。

## <a name="ngen"></a>NGEN

原生 (映像) 產生。

您可以將這項技術視為永續性 JIT 編譯器。 它通常會在執行程式碼的電腦上編譯程式碼，但編譯通常會發生在安裝期間。

## <a name="package"></a>套件

NuGet 套件 (簡稱套件) 是 *.zip* 檔案，其中包含一或多個同名組件及其他中繼資料 (例如作者名稱)。

*.zip* 檔案包含一個 *.nupkg* 延伸模組和許多特定資產 (例如 *.dll* 檔案和 *.xml* 檔案)，可搭配多個架構和版本使用。 安裝於應用程式或程式庫時，會根據應用程式或程式庫所指定的目標 Framework 來選取適當的資產。 定義介面的資產位於 *ref* 資料夾中，而定義實作的資產則位於 *lib* 資料夾中。

## <a name="platform"></a>platform

作業系統及其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。

以下是用於句子中的範例：

- 「.NET Core 是 .NET 的跨平台實作。」 
- 「PCL 設定檔代表 Microsoft 平台，而 .NET Standard 則無從驗證平台。」

.NET 文件經常使用「.NET 平台」來表示 .NET 實作或包含所有實作的 .NET 堆疊。 這兩種用法通常會與主要 (OS/硬體) 意義混淆，因此我們計劃從文件中排除這些用法。

## <a name="runtime"></a>執行階段

受管理程式的執行環境。

OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。 以下是 .NET 執行階段的一些範例：

- Common Language Runtime (CLR)
- Core Common Language Runtime (CoreCLR)
- .NET Native (適用於 UWP)
- Mono 執行階段

.NET 文件有時會使用「執行階段」來表示 .NET 實作。 例如，在下列句子中，「執行階段」應該取代成「實作」：

- 「不同的 .NET 執行階段會實作特定版本的 .NET Standard。」
- 「要在多個執行階段上執行的程式庫應以此架構為目標。」 (指的是 .NET Standard)
- 「不同的 .NET 執行階段會實作特定版本的 .NET Standard。 … 每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本...」

我們計劃排除這個不一致的用法。 

## <a name="stack"></a>堆疊

可搭配使用以建置及執行應用程式的一組程式設計技術。

「.NET 堆疊」是指 .NET Standard 和所有 .NET 實作。 「一個 .NET 堆疊」一詞可能是指 .NET 的一項實作。 

## <a name="target-framework"></a>Target Framework - 目標 Framework

.NET 應用程式或程式庫依賴的 API 集合。

應用程式或程式庫可以將目標設為某個版本的 .NET Standard (例如 .NET Standard 2.0)，這會是跨所有 .NET 實作之一組標準化 API 的規格。 應用程式或程式庫也可以將目標設為某個版本的特定 .NET 實作；在此情況下，它可以存取實作特定的 API。 例如，以 Xamarin.iOS 為目標的應用程式可以存取 Xamarin 提供的 iOS API 包裝函式。

針對某些目標 Framework (例如 .NET Framework)，可用的 API 是由 .NET 實作安裝在系統上的組件所定義，這可能包含應用程式架構 API (例如 ASP.NET、WinForms)。 針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，架構 API 是由安裝在應用程式或程式庫中的套件所定義。 在此情況下，目標 Framework 會隱含指定一個中繼套件，該套件會參考組成架構的所有套件。

請參閱[目標 Framework](frameworks.md)。

## <a name="tfm"></a>TFM

目標 Framework Moniker。

用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。 目標 Framework 通常會由簡短名稱參考，例如 `net462`。 雖然有完整格式的 TFM (例如 .NETFramework,Version=4.6.2)，但通常不會用來指定目標 Framework。

請參閱[目標 Framework](frameworks.md)。

## <a name="uwp"></a>UWP

通用 Windows 平台。

用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。 其設計目的是為了整合您可能想要設為目標的不同裝置類型，包括電腦、平板電腦、平板手機、手機，甚至是 Xbox。 UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。 您可以使用 C++、C#、VB.NET 和 JavaScript 來撰寫應用程式。 使用 C# 和 VB.NET 時，.NET API 是由 .NET Core 所提供。

## <a name="see-also"></a>另請參閱

[.NET 指南](index.md)  
[.NET Framework 指南](../framework/index.md)  
[.NET Core](../core/index.md)  
[ASP.NET 概觀](/aspnet/index#pivot=aspnet)  
[ASP.NET Core 概觀](/aspnet/index#pivot=core)  

