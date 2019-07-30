---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 06/14/2019
ms.openlocfilehash: b1dd243d754bfc3b682c084820547f6b7846f0ea
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484664"
---
# <a name="whats-new-in-net-core-30-preview-6"></a>.NET Core 3.0 (Preview 6) 的新功能

本文描述 .NET Core 3.0 (到 Preview 6) 的新功能。 其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。 您可以使用 .NET Core 3.0 SDK 元件「Windows 傳統型」來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。 具體而言，只有在 Windows 上才支援並包含「Windows 傳統型」元件。 如需詳細資訊，請參閱本文稍後的 [Windows 傳統型](#windows-desktop)一節。

.NET Core 3.0 新增 C# 8.0 支援。 強烈建議您搭配 OmniSharp 延伸模組使用[最新版的 Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview) 或 Visual Studio Code。

立即在 Windows、Mac 及 Linux 上[下載並開始使用 .NET Core 3.0 Preview 6](https://aka.ms/netcore3download) \(英文\)。

如需每個預覽版的詳細資訊，請參閱下列公告：

- [.NET Core 3.0 Preview 6 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/) \(英文\)
- [.NET Core 3.0 Preview 5 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [.NET Core 3.0 Preview 4 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [.NET Core 3.0 Preview 3 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [.NET Core 3.0 Preview 2 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [.NET Core 3.0 Preview 1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a>.NET Core SDK Windows Installer

Windows 的 MSI 安裝程式從 .NET Core 3.0 開始即已變更。 SDK 安裝程式現在會就地升級 SDK 功能帶版本。 功能帶是在版本號碼「修補程式」  部分以「一百」  為單位的群組中定義。 例如，**3.0._101_** 和 **3.0._201_** 便是位於兩個不同功能帶中的版本，而 **3.0._101_** 和 **3.0._199_** 則位於相同的功能帶。 此外，安裝 .NET Core SDK **3.0._101_** 時，.NET Core SDK **3.0._100_** 便會從電腦移除 (若存在的話)。 在相同電腦上安裝 .NET Core SDK **3.0._200_** 時，不會移除 .NET Core SDK **3.0._101_** 。

如需版本設定的詳細資訊，請參閱 [.NET Core 版本設定概觀](../versions/index.md)。

## <a name="c-80-preview"></a>C# 8.0 Preview

.NET Core 3.0 支援 C# 8 Preview。 如需 C# 8.0 功能的詳細資訊，請參閱 [C# 8.0 的新功能](../../csharp/whats-new/csharp-8.md)。

## <a name="net-standard-21"></a>.NET Standard 2.1

雖然 .NET Core 3.0 支援 **.NET Standard 2.1**，但預設 `dotnet new classlib` 範本會產生以 **.NET Standard 2.0** 為目標的專案。 若要以 **.NET Standard 2.1** 為目標，請編輯您的專案檔並將 `TargetFramework` 屬性變更為 `netstandard2.1`：

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

如果目前使用 Visual Studio，您需要 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，因為 Visual Studio 2017 不支援 **.NET Standard 2.1** 或 **.NET Core 3.0**。

## <a name="improved-net-core-version-apis"></a>改善的 .NET Core 版本 API

從 .NET Core 3.0 開始，.NET Core 所提供版本 API 現在會傳回您預期的資訊。 例如：

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> 重大變更。 這是技術上的重大變更，因為版本設定配置已變更。

## <a name="net-platform-dependent-intrinsics"></a>.NET 平台相依內建

已新增 API，允許存取特定效能導向的 CPU 指令，例如 **SIMD** 或**位元操作指令**集合。 這些指令可協助您在某些情況 (例如有效率地平行處理資料) 下大幅提升效能。 

.NET 程式庫 (如果適用) 已開始使用這些指令來提升效能。

如需詳細資訊，請參閱 [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md) (.NET 平台相依內建)。

## <a name="default-executables"></a>預設可執行檔

.NET Core 現在預設會建置[架構相依可執行檔](../deploying/index.md#framework-dependent-executables-fde)。 這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新行為。 先前，只有[獨立式部署](../deploying/index.md#self-contained-deployments-scd)會產生可執行檔。

在 `dotnet build` 或 `dotnet publish` 期間，會建立符合您所用 SDK 環境和平台的可執行檔。 針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：

* 您可以按兩下可執行檔。
* 您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。

## <a name="single-file-executables"></a>單一檔案可執行檔

`dotnet publish` 命令支援將您的應用程式封裝成平台特定單一檔案可執行檔。 可執行檔會自我解壓縮，並包含執行應用程式所需的所有相依性 (包括原生)。 第一次執行應用程式時，系統會將應用程式解壓縮到以應用程式名稱和組建識別碼為基礎的目錄。 再次執行應用程式時的啟動速度會更快。 除非使用新版本，否則應用程式不需要再次自我解壓縮。

若要發佈單一檔案可執行檔，請在專案中或在命令列上使用 `dotnet publish` 命令來設定 `PublishSingleFile`：

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

-或-

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

如需單一檔案發佈的詳細資訊，請參閱[單一檔案搭配程式設計文件](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md)。

## <a name="assembly-linking"></a>組件連結

.NET Core 3.0 SDK 隨附能透過分析 IL 並修剪未使用的組件來減少應用程式大小的工具。

自封式應用程式包含執行程式碼所需的一切項目，因此不需要在主機電腦上安裝 .NET。 不過，應用程式經常只需要一小部分的架構子集便能運作，而其他未使用的程式庫則可以被移除。

.NET Core 現在包含會使用 [IL 連結器](https://github.com/mono/linker) \(英文\) 工具來掃描應用程式 IL 的設定。 此工具會偵測所需的程式碼，然後修剪未使用的程式庫。 此工具可以大幅減少某些應用程式的部署大小。

若要啟用此工具，請在專案中新增 `<PublishTrimmed>` 設定，並發佈獨立式應用程式：

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

例如，所包含的基本 "hello world" 新主控台專案在發佈時的大小大約是 70 MB。 透過使用 `<PublishTrimmed>`，該大小會被縮減為大約 30 MB。

請務必記得，對使用反映或相關動態功能的應用程式或架構 (包括 ASP.NET Core 和 WPF) 進行修剪經常會發生中斷的情況。 會發生此中斷的原因是因為連結器不知道此動態行為，因此無法判斷反映所需的架構類型有哪些。 可以對 IL 連結器工具加以設定來使其注意到此情況。

無論如何，請務必在修剪後測試您的應用程式。

如需 IL 連結器工具的詳細資訊，請參閱[文件](https://aka.ms/dotnet-illink) \(英文\) 或造訪 [mono/linker]( https://github.com/mono/linker) \(英文\) 存放庫。

## <a name="tiered-compilation"></a>階層式編譯

.NET Core 3.0 預設會開啟[階層式編譯](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC)。 這項功能可讓執行階段更彈性地使用 Just-In-Time (JIT) 編譯器來獲得更佳的效能。

TC 的主要優點是能夠啟用較慢速但較快產生程式碼，或品質較高但較慢產生程式碼的 JIT 重新編譯方法。 由於行經各種執行階段 (從啟動到穩定狀態)，因此有助於提升應用程式的效能。 這與非 TC 方法相反，在非 TC 方法中，所有方法都是以單一方式 (與高品質層相同) 進行編譯，這會偏重穩定狀態而非啟動效能。

若要啟用 Quick JIT (層級 0 JIT 編譯的程式碼)，請在您的專案檔中使用此設定：

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

若要完全停用 TC，請在您的專案檔中使用此設定：

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a>ReadyToRun 映像

您可以透過將應用程式組件編譯為 ReadyToRun (R2R) 格式，來改善 .NET Core 應用程式的啟動時間。 R2R 是一種預先(AOT) 編譯。

R2R 二進位檔會透過減少 Just-In-Time (JIT) 編譯器在應用程式載入時所需執行的工作量，來改善啟動效能。 二進位檔包含的機器碼，與 JIT 所會產生的內容類似。

R2R 二進位檔大小較大，因為它們會同時包含中繼語言 (IL) 程式碼 (在某些案例下仍需要使用)，以及相同程式碼的原生版本。 R2R 只有在您發佈以特定執行階段環境 (RID) (例如 Linux x64 或 Windows x64) 為目標的自封式應用程式時才可供使用。

若要將應用程式編譯為 R2R，請加入 `<PublishReadyToRun>` 設定：

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

發佈自封式應用程式。 例如，此命令會針對 64 位元版本的 Windows 建立自封式應用程式：

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a>跨平台/架構限制

ReadyToRun 編譯器目前不支援跨目標。 您必須在指定的目標上進行編譯。 例如，如果您想要適用於 Windows x64 的 R2R 映像，便需要在該環境上執行發佈命令。

鎖定多重目標的例外狀況：

- Windows x64 可以用來編譯 Windows ARM32、ARM64 及 x86 映像。
- Windows x86 可以用來編譯 Windows ARM32 映像。
- Linux x64 可以用來編譯 Linux ARM32 和 ARM64 映像。

## <a name="build-copies-dependencies"></a>組建複本相依性

`dotnet build` 命令現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。 先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。

有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。

## <a name="local-tools"></a>本機工具

.NET Core 3.0 引進本機工具。 本機工具與[全域工具](../tools/global-tools.md)類似，但與磁碟上的某個特定位置立建立關聯。 本機工具並非全域可用，而是以 NuGet 套件形式散發。

> [!WARNING]
> 如果您在 .NET Core 3.0 Preview 1 中嘗試本機工具 (例如執行 `dotnet tool restore` 或 `dotnet tool install`)，請刪除本機工具快取資料夾。 否則，本機工具將無法在任何較新版本中運作。 此資料夾位於：
>
> 在 macOS 上，Linux：`rm -r $HOME/.dotnet/toolResolverCache`
>
> 在 Windows 上：`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。 此資訊清單檔定義可在該資料夾和以下資料夾提供的工具。 您可以隨程式碼散發資訊清單檔，確保使用您程式碼的任何人都能進行還原並使用相同工具。

不論是全域工具還是區域工具，都需要一個相容的執行階段版本。 NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。 若要在全域或本機安裝這些工具，您仍然需要安裝 [.NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。

## <a name="major-version-roll-forward"></a>主要版本向前復原

.NET Core 3.0 引進選擇性功能，可讓您的應用程式向前復原到 .NET Core 最新主要版本。 此外，也已新增設定來控制如何將向前復原套用至您的應用程式。 這可透過下列方式進行設定：

- 專案檔屬性：`RollForward`
- 執行階段組態檔屬性：`rollForward`
- 環境變數：`DOTNET_ROLL_FORWARD`
- 命令列引數：`--roll-forward`

必須指定下列其中一個值。 若省略設定，**Minor** 會是預設值。

- **LatestPatch**\
向前復原到最高的修補程式版本。 這會停用次要版本向前復原。
- **Minor**\
如果缺少要求的次要版本，則會向前復原到最低次要版本中次高的版本。 如果要求的次要版本存在，則會使用 **LatestPatch** 原則。
- **Major**\
如果缺少要求的主要版本，則會向前復原到最低主要版本中次高的版本，以及最低的次要版本。 如果要求的主要版本存在，則會使用 **Minor** 原則。
- **LatestMinor**\
向前復原到最高的次要版本，即使要求的次要版本存在也一樣。 適用於裝載案例的元件。
- **LatestMajor**\
向前復原到最高主要版本和最高次要版本，即使要求的主要版本存在也一樣。 適用於裝載案例的元件。
- **Disable**\
不會向前復原。 只會繫結至指定的版本。 此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。 只有測試時才建議使用這個值。

除了 **Disable** 設定，所有設定都會使用最高可用的修補程式版本。

## <a name="windows-desktop"></a>Windows 桌面

.NET Core 3.0 支援使用 Windows Presentation Foundation (WPF) 和 Windows Forms 的 Windows 傳統型應用程式。 這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。

「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。

您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 會新增 [新增專案]  範本，供 .NET Core 3.0 Windows Forms 和 WPF 使用。

如需如何移植現有 .NET Framework 應用程式的詳細資訊，請參閱[移植 WPF 專案](../porting/wpf.md)和[移植 Windows Forms 專案](../porting/winforms.md)。

## <a name="com-callable-components---windows-desktop"></a>COM 可呼叫元件 - Windows 傳統型

您現在可以在 Windows 上建立 COM 可呼叫受控元件。 此功能對於搭配 COM 增益集模型使用 .NET Core 很重要，也提供 .NET Framework 同位。

不同於 .NET Framework (其中使用 *mscoree.dll* 作為 COM 伺服器)，.NET Core 會在您建置 COM 元件時，將原生啟動器 DLL 新增至 *bin* 目錄。

如需如何建立及取用 COM 元件的範例，請參閱 [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) (COM 示範)。

## <a name="msix-deployment---windows-desktop"></a>MSIX 部署 - Windows 傳統型

[MSIX](https://docs.microsoft.com/windows/msix/) 是新的 Windows 應用程式套件格式。 它可以用來將 .NET Core 3.0 桌面應用程式部署至 Windows 10。

Visual Studio 2019 中提供的 [Windows 應用程式套件專案](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net) \(機器翻譯\) 可讓您利用[獨立式](../deploying/index.md#self-contained-deployments-scd) .NET Core 應用程式建立 MSIX 套件。

.NET Core 專案檔必須指定在 `<RuntimeIdentifiers>` 屬性中支援的執行階段：

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

.NET Core Windows Forms 應用程式可以使用 <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> 設定高 DPI 模式。 除非已透過其他方法 (例如在 `Application.Run` 前面加上 `App.Manifest` 或 P/Invoke) 進行設定，否則 `SetHighDpiMode` 方法可以設定對應的高 DPI 模式。

可能的 `highDpiMode` 值 (如 <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> 列舉所示) 為：

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

如需高 DPI 模式的詳細資訊，請參閱 [Windows 上的高 DPI 傳統型應用程式開發](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)。

### <a name="ranges-and-indices"></a>範圍和索引

新的 <xref:System.Index?displayProperty=nameWithType> 類型可用於編製索引。 您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

此外，還有 <xref:System.Range?displayProperty=nameWithType> 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。 您可以接著使用 `Range` 來編製索引以產生配量：

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

如需詳細資訊，請參閱[範圍和索引教學課程](../../csharp/tutorials/ranges-indexes.md)。

### <a name="async-streams"></a>非同步資料流

<xref:System.Collections.Generic.IAsyncEnumerable%601> 類型是 <xref:System.Collections.Generic.IEnumerable%601> 的新非同步版本。 此語言可讓您透過 `IAsyncEnumerable<T>` 執行 `await foreach` 以取用其元素，然後對它們使用 `yield return` 以產生元素。

下列範例同時示範如何產生和取用非同步資料流。 `foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。 此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。 針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。

如需詳細資訊，請參閱[非同步資料流教學課程](../../csharp/tutorials/generate-consume-asynchronous-stream.md)。

## <a name="ieee-floating-point-improvements"></a>IEEE 浮點增強功能

正在更新浮點 API，以遵守 [IEEE 754-2008 修訂](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)。 這些變更的目標是公開所有的**必要**作業，並確定它們在行為上符合 IEEE 規格。如需浮點增強功能的詳細資訊，請參閱 [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) (.NET Core 3.0 中的浮點剖析和格式化增強功能) 部落格文章。

剖析與格式化修正包括：

* 正確地剖析並捨入任意長度的輸入。
* 正確地剖析並格式化負零。
* 正確地剖析 `Infinity` 和 `NaN`，方法為執行不區分大小寫的檢查，並允許適當時在前面選擇性加上 `+`。

新的 <xref:System.Math?displayProperty=nameWithType> API 包括：

* <xref:System.Math.BitIncrement(System.Double)> 和 <xref:System.Math.BitDecrement(System.Double)>\
對應至 `nextUp` 和 `nextDown` IEEE 作業。 它們會傳回最小浮點數，比較大於或小於輸入 (分別)。 例如，`Math.BitIncrement(0.0)` 會傳回 `double.Epsilon`。

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)> 和 <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
對應至 `maxNumMag` 和 `minNumMag`IEEE 作業，它們傳回的值大於或小於兩個輸入的範圍 (分別)。 例如，`Math.MaxMagnitude(2.0, -3.0)` 會傳回 `-3.0`。

* <xref:System.Math.ILogB(System.Double)>\
對應至傳回整數值的 `logB` IEEE 作業，它會傳回輸入參數的對數，以整數 2 為底數。 此方法實際上與 `floor(log2(x))` 相同，但完成時發生最少捨入錯誤。

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
對應至採用整數值的 `scaleB` IEEE 作業，它會有效傳回 `x * pow(2, n)`，但完成時發生最少捨入錯誤。

* <xref:System.Math.Log2(System.Double)>\
對應至 `log2` IEEE 作業，它會傳回 2 為底數的對數。 它會將捨入錯誤減至最少。

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
對應至 `fma` IEEE 作業，它會執行融合的乘積和。 亦即，它會將 `(x * y) + z` 當作單一作業來執行，藉此將捨入錯誤減至最少。 範例將是傳回 `1e308` 的 `FusedMultiplyAdd(1e308, 2.0, -1e308)`。 一般 `(1e308 * 2.0) - 1e308` 會傳回 `double.PositiveInfinity`。

* <xref:System.Math.CopySign(System.Double,System.Double)>\
對應至 `copySign` IEEE 作業，它會傳回 `x` 的值，但具有 `y` 的符號。

## <a name="fast-built-in-json-support"></a>快速的內建 JSON 支援

.NET 使用者大幅倚賴 [**Json.NET**](https://www.newtonsoft.com/json) 及其他熱門的 JSON 程式庫 (這些仍持續是絕佳的選擇)。 **Json.NET** 使用 .NET 字串作為其基底資料類型，實際上就是 UTF-16。

新的內建 JSON 支援是高效能、低配置，並以 `Span<byte>` 為基礎。 三個新的主要 JSON 相關類型已新增到 .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> 命名空間。 這些類型「尚未」  支援簡單的 CLR 物件 (POCO) 序列化與還原序列化。

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。 `Utf8JsonReader` 是一個基礎的低階類型，可用來建置自訂剖析器和還原序列化程式。 使用新的 `Utf8JsonReader` 來讀取 JSON 承載會比使用來自 **Json.NET** 的讀取器快兩倍。 它會等到您需要將 JSON 權杖實現為 (UTF-16) 字串時，才進行配置。

以下是完整閱讀 Visual Studio Code 所建立 [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) 檔案的範例：

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 提供高效能、非快取、僅轉接方式，從常見的 .NET 類型 (像是 `String`、`Int32` 和 `DateTime`) 撰寫 UTF-8 編碼的 JSON 文字。 如同讀取器，寫入器是一個基礎的低階類型，可用來建置自訂序列化程式。 使用新的 `Utf8JsonWriter` 撰寫 JSON 承載，其速度比從 **Json.NET** 使用寫入器還要快 30-80%，且不會配置。

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> 是組建在 `Utf8JsonReader` 之上。 `JsonDocument` 可讓您剖析 JSON 資料和組建唯讀文件物件模型 (DOM)，而您可以查詢此模型來支援隨機存取和列舉。 撰寫資料的 JSON 項目可以透過 <xref:System.Text.Json.JsonElement> 類型來存取，而此類型被 `JsonDocument` 公開為稱為 `RootElement` 的屬性。 `JsonElement` 包含 JSON 陣列和物件列舉程式，以及將 JSON 文字轉換為一般.NET 類型的 API。 使用 `JsonDocument` 剖析一般 JSON 承載，並存取其所有成員，速度比 **Json.NET** 還要快 2-3 倍，且極少配置合理大小 (亦即 < 1 MB) 的資料。

以下是 `JsonDocument` 和 `JsonElement` 的使用方式樣本，其可作為起點：

以下是完整閱讀 Visual Studio Code 所建立 [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) 檔案的 C# 8.0 範例：

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> 建置在 <xref:System.Text.Json.Utf8JsonReader> 和 <xref:System.Text.Json.Utf8JsonWriter> 之上，以在使用 JSON 文件和片段時，提供快速的低記憶體序列化選項。

查看： https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md 以取得要移植到本文的範例

以下是將物件序列化成 JSON 的範例：

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

以下是將 JSON 字串還原序列化成物件的範例。 您可以使用上述範例所產生的 JSON 字串：

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Interop 增強功能

.NET Core 3.0 改善原生 API Interop。

### <a name="type-nativelibrary"></a>類型：NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> 提供封裝來載入原生程式庫 (使用與 .NET Core P/Invoke 相同的負載邏輯)，並提供相關的 Helper 函式 (例如 `getSymbol`)。 如需程式碼範例，請參閱 [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin) (DLLMap 示範)。

### <a name="windows-native-interop"></a>Windows 原生 Interop

Windows 提供豐富的原生 API，其採用的形式為一般 C API、COM 和 WinRT。 除了 .NET Core 3.0 支援 **P/Invoke** 之外，.NET Core 3.0 還新增 **CoCreate COM API** 和 **Activate WinRT API** 的功能。 如需程式碼範例，請參閱 [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo) (Excel 示範)。

## <a name="http2-support"></a>HTTP/2 支援

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型支援 HTTP/2 通訊協定。 如果啟用 HTTP/2，則會透過 TLS/ALPN 交涉 HTTP 通訊協定版本，並會在伺服器選擇使用它時使用 HTTP/2。

預設通訊協定會保持為 HTTP/1.1，但 HTTP/2 可以兩種不同的方式啟用。 首先，您可以設定 HTTP 要求訊息來使用 HTTP/2：

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

再來，您可以變更 <xref:System.Net.Http.HttpClient> 來預設使用 HTTP/2：

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

當您在開發應用程式時，經常會想要使用未加密的連線。 如果您知道目標端點會使用 HTTP/2，便可以針對 HTTP/2 開啟未加密的連線。 若要開啟它，您可以將 `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` 環境變數設定為 `1`，或是在應用程式內容中啟用它：

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>Linux 上的 TLS 1.3 和 OpenSSL 1.1.1

.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。 透過 TLS 1.3：

* 因為用戶端與伺服器之間所需的來回行程次數減少，所以改善了連線時間。
* 因為移除各種已淘汰和不安全的密碼編譯演算法，所以提升了安全性。

.NET Core 3.0 在 Linux 系統上使用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (若可供使用)。 當 **OpenSSL 1.1.1** 可供使用時，<xref:System.Net.Security.SslStream?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型就會使用 **TLS 1.3** (假設用戶端和伺服器都支援 **TLS 1.3**)。

>[!IMPORTANT]
>Windows 和 macOS 尚未支援 **TLS 1.3**。 .NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。

下列 C# 8.0 範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0：

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>密碼編譯加密方式

.NET 3.0 新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援，分別透過 <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> 和 <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> 來實作。 這些演算法都是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)。

下列程式碼示範如何使用 `AesGcm` 加密方式將隨機資料加密和解密。

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>密碼編譯金鑰匯入/匯出

.NET Core 3.0 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰。 您無須使用 X.509 憑證。

所有金鑰類型 (例如 *RSA*、*DSA*、*ECDsa* 和 *ECDiffieHellman*) 都支援下列格式：

* **公開金鑰**
  * X.509 SubjectPublicKeyInfo

* **私密金鑰**
  * PKCS#8 PrivateKeyInfo
  * PKCS#8 EncryptedPrivateKeyInfo

RSA 金鑰也支援：

* **公開金鑰**
  * PKCS#1 RSAPublicKey

* **私密金鑰**
  * PKCS#1 RSAPrivateKey

匯出方法會產生 DER 編碼的二進位資料，而匯入方法也是如此。 如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS#8** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> 來檢查，而 **PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> 來檢查。 **PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> 來操作。

## <a name="serialport-for-linux"></a>適用於 Linux 的 SerialPort

.NET Core 3.0 在 Linux 上支援 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>。

先前，.NET Core 僅支援在 Windows 上使用 `SerialPort`。

## <a name="docker-and-cgroup-memory-limits"></a>Docker 和 cgroup 記憶體限制

從 Preview 3 開始，在 Linux 上執行 .NET Core 3.0 和 Docker 搭配 cgroup 記憶體限制的效果最佳。 使用記憶體限制 (例如使用 `docker run -m`) 執行 Docker 容器會變更 .NET Core 的運作方式。

* 預設記憶體回收行程 (GC) 堆積大小：上限為 20 MB，或容器上 75% 的記憶體限制。
* 可將明確大小設定為 cgroup 限制的絕對數目或百分比。
* 每個 GC 堆積的保留區段大小下限為 16 MB。 此大小可減少電腦上所建立的堆積數目。

## <a name="smaller-garbage-collection-heap-sizes"></a>較小的記憶體回收堆積大小

已減少記憶體回收行程的預設堆積大小，而導致 .NET Core 使用較少的記憶體。 這項變更較符合使用新式處理器快取大小的層代 0 配置預算。

## <a name="garbage-collection-large-page-support"></a>記憶體回收大型頁面支援

大型頁面 (Large Page，在 Linux 上又稱為 Huge Page) 是一項功能，其中作業系統能夠建立大於原生頁面大小 (通常為 4K) 的記憶體區域，以提升要求這些大型頁面的應用程式效能。

記憶體回收行程現在可以設定 **GCLargePages** 設定作為選擇性功能，來選擇在 Windows 上配置大型頁面。

## <a name="gpio-support-for-raspberry-pi"></a>Raspberry Pi 的 GPIO 支援

兩個套件已發佈至您可以用於 GPIO 程式設計的 NuGet：

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

GPIO 套件包含 *GPIO*、*SPI*、*I2C* 和 *PWM* 裝置的 API。 IoT 繫結套件包含裝置繫結。 如需詳細資訊，請參閱[裝置 GitHub 存放庫](https://github.com/dotnet/iot/blob/master/src/devices/)。

## <a name="arm64-linux-support"></a>ARM64 Linux 支援

.NET Core 3.0 新增 ARM64 for Linux 的支援。 ARM64 的主要使用案例目前是搭配 IoT 案例。 如需詳細資訊，請參閱 [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) (.NET Core ARM64 狀態)。

[ARM64 上適用於 .NET Core 的 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)可供 Alpine、Debian 和 Ubuntu 使用。

> [!NOTE]
> 目前尚未提供 **ARM64** Windows 支援。
