---
title: 平台相容性分析器
description: Roslyn 分析器，可協助偵測跨平臺應用程式和程式庫中的平臺相容性問題。
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: fcd5ec755789ff7f2472d8077dd52f321bf9f167
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756178"
---
# <a name="platform-compatibility-analyzer"></a>平台相容性分析器

您可能聽過「單一 .NET」的格言：單一、統一的平臺，可用於建立任何類型的應用程式。 .NET 5.0 SDK 包含 ASP.NET Core、Entity Framework Core、WinForms、WPF、Xamarin 和 ML.NET，並且會隨著時間增加更多平臺的支援。 .NET 5.0 致力於提供一種體驗，讓您不必擔心不同的 .NET 種類，但也不會嘗試完全抽象化基礎作業系統)  (作業系統。 您將繼續能夠呼叫平臺專屬的 Api，例如 P/Invoke、WinRT 或適用于 iOS 和 Android 的 Xamarin 系結。

但是，在元件上使用平臺特定的 Api，表示程式碼無法在所有平臺上運作。 我們需要在設計階段偵測到此情況的方法，讓開發人員在不小心使用平臺特定 Api 時取得診斷。 為了達成此目標，.NET 5.0 引進了 [平臺相容性分析器](/visualstudio/code-quality/ca1416) 和互補的 api，協助開發人員在適當的情況下識別及使用平臺特定的 api。
新的 Api 包括：

- <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 將 Api 標注為平臺特定的批註，並 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 將 api 標注為在特定 OS 上不受支援。 這些屬性可以選擇性地包含版本號碼，並已套用至核心 .NET 程式庫中的某些平臺特定 Api。
- `Is<Platform>()` 以及 `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` 類別中的靜態方法，可 <xref:System.OperatingSystem?displayProperty=nameWithType> 安全地呼叫平臺特定的 api。 例如， <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> 可以用來保護對 windows 特定 api 的呼叫，而 <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> ( # A1 可以用來保護已建立版本的 WINDOWS 特定 api 呼叫。 請參閱這些方法的 [範例](#guard-platform-specific-apis-with-guard-methods) ，以瞭解如何使用這些方法來作為平臺特定 API 參考的防護。

> [!TIP]
> 平臺相容性分析器會升級並取代[.NET API 分析器](../../standard/analyzers/api-analyzer.md)的[探索跨平臺問題](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues)功能。

## <a name="prerequisites"></a>必要條件

平臺相容性分析器是 Roslyn 的程式碼品質分析器之一。 從 .NET 5.0 開始，這些分析器會 [隨附于 .NET SDK](../../fundamentals/productivity/code-analysis.md)。 根據預設，平臺相容性分析器僅針對以或更新版本為目標的專案啟用 `net5.0` 。 不過，您可以針對以其他架構為目標的專案 [啟用](/visualstudio/code-quality/ca1416.md#configurability) 它。

## <a name="how-the-analyzer-determines-platform-dependency"></a>分析器如何判斷平臺相關性

- **未歸屬 API**會視為在**所有 OS 平臺**上運作。
- 標記為的 API `[SupportedOSPlatform("platform")]` 只會被視為可移植到指定的作業系統 `platform` 。
  - 您可以多次套用屬性，以指出 () 的 **多平臺支援** `[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]` 。
  - 如果未使用適當的**平臺內容**參考平臺特定 api，分析器會產生**警告**：
    - 如果專案未以支援的平臺為目標，則會**發出警告** (例如，Windows 特定的 API 呼叫和專案的目標 `<TargetFramework>net5.0-ios14.0</TargetFramework>`) 。
    - 如果專案是多目標 () ，則會**發出警告** `<TargetFramework>net5.0</TargetFramework>` 。
    - 如果在以任何**指定平臺**為目標的專案中參考平臺特定的 api，則**不會發出警告** (例如，針對 Windows 特定的 api 呼叫和專案的目標 `<TargetFramework>net5.0-windows</TargetFramework>`) 。
    - 如果平臺特定 API 呼叫受到對應平臺檢查方法的防護，則**不會發出警告** (例如 `if(OperatingSystem.IsWindows())`) 。
    - 如果從相同平臺特定的內容參考平臺特定的 API， (**呼叫網站也**以) 進行屬性化，則**不會發出警告** `[SupportedOSPlatform("platform")` 。
- 標記為的 API `[UnsupportedOSPlatform("platform")]` 只會在指定的 OS 上被視為不受支援， `platform` 但所有其他平臺皆支援此 API。
  - 您可以使用不同的平臺多次套用屬性，例如 `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]` 。
  - 只有當對**warning** `platform` 呼叫位置有效時，分析器才會產生警告：
    - 如果專案的目標平臺是以不 (支援的屬性為目標的平臺，例如，如果 API 是以屬性化，而且呼叫位置的目標是) ，則會**發出警告** `[UnsupportedOSPlatform("windows")]` `<TargetFramework>net5.0-windows</TargetFramework>` 。
    - **Warns**如果專案是多目標且 `platform` 包含在預設[MSBuild `<SupportedPlatform>` ](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props)專案群組中，或 `platform` 手動包含在 `MSBuild` items 群組內，則會發出警告 \<SupportedPlatform> ：

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - 如果您要建立的應用程式不是以不受支援的平臺為目標，或為多目標，且該平臺未包含在預設的 [ [MSBuild `<SupportedPlatform>` ](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props)專案] 群組中，則**不會發出警告**。
- 這兩個屬性都可以使用或不含版本號碼作為平臺名稱的一部分來具現化。
  - 版本號碼的格式 `major.minor[.build[.revision]]` 為; `major.minor` 是必要的， `build` 而且和 `revision` 部分是選擇性的。 例如，「Windows 7.0」表示 Windows 7.0 版，但「Windows」則會被視為 Windows 0.0。

如需詳細資訊，請參閱 [屬性如何運作的範例，以及它們所造成的診斷](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce)。

### <a name="advanced-scenarios-for-combining-attributes"></a>合併屬性的 Advanced 案例

- 如果有 `[SupportedOSPlatform]` 和屬性的組合 `[UnsupportedOSPlatform]` ，則所有屬性都會依作業系統平臺識別碼分組：
  - **僅支援的清單**。 如果每個作業系統平臺的最低版本是 `[SupportedOSPlatform]` 屬性，則會將 API 視為僅受列出的平臺支援，而且所有其他平臺都不支援此 API。 `[UnsupportedOSPlatform]`每個平臺的選擇性屬性只能有較高版本的最低支援版本，表示從指定的版本開始移除 API。

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - **唯一不支援的清單**。 如果每個作業系統平臺的最低版本是 `[UnsupportedOSPlatform]` 屬性，則會將 API 視為只有列出的平臺不支援，而且所有其他平臺都支援此 API。 此清單可能具有 `[SupportedOSPlatform]` 相同平臺但版本較高的屬性，代表從該版本開始支援 API。

    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - **不一致的清單**。 如果某些平臺的最低版本是 `[SupportedOSPlatform]` 在 `[UnsupportedOSPlatform]` 其他平臺上，則會被視為不一致，分析器不支援此版本。
  - 如果和屬性的最小版本 `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` 相等，分析器會將平臺視為 **支援的唯一清單**的一部分。
- 平臺屬性可以套用至類型、成員 (方法、欄位、屬性和事件) 以及具有不同平臺名稱或版本的元件。
  - 在最上層套用的屬性 `target` 會影響其所有成員和類型。
  - 只有當子系層級的屬性符合規則「子批註可以縮小平臺支援，但無法將其加寬」時，才適用。
    - 當父系 **僅支援** 清單時，子成員屬性無法加入新的平臺支援，因為這樣會擴充父系支援。 只能將新平臺的支援新增至父系本身。 但是子系可以具有 `Supported` 與較新版本相同平臺的屬性，因為這樣會縮小支援。 此外，子系的屬性也可以是相同的平臺，也就是可 `Unsupported` 縮小父支援。
    - 當父系有 **不支援** 的清單時，子成員屬性可以新增新平臺的支援，因為這樣會縮小父系支援。 但是，它不能有與 `Supported` 父系相同平臺的屬性，因為它會擴充父系支援。 相同平臺的支援只能加入至套用原始屬性的父系 `Unsupported` 。
  - 如果為 `[SupportedOSPlatform("platformVersion")]` 相同名稱的 API 套用了一次以上 `platform` ，分析器只會考慮具有最小版本的應用程式。
  - 如果 `[UnsupportedOSPlatform("platformVersion")]` 為相同名稱的 API 套用了兩次以上 `platform` ，分析器就只會將這兩個版本視為最舊的版本。

  > [!NOTE]
  > 在較新版本中，一開始就支援但不支援 (移除) 的 API，不應該在較新版本中取得 resupported。

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a>屬性的運作方式，以及它們所產生之診斷的範例

  ```csharp
  // An API supported only on Windows.
  [SupportedOSPlatform("Windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  public void Caller()
  {
      WindowsOnlyApi(); // warns: 'WindowsOnlyApi' is supported on 'windows'

      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Windows'
      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Linux'
      SupportedOnWindowsAndLinuxOnly();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 8.0 and later
      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // for same platform analyzer only warn for the latest version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  public void Caller2()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'android'

      // warns:'StartedWindowsSupportFromVersion8' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFromVersion8' is supported on 'windows' 8.0 and later
      StartedWindowsSupportFromVersion8();

      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is supported on 'windows' 8.0 and later
      // even there were 3 diagnostics found analyzer warn only for the first 2.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

## <a name="handle-reported-warnings"></a>處理回報的警告

處理這些診斷的建議方式是確保您只在適當的平臺上執行時，才呼叫平臺專屬的 Api。 以下是您可以用來解決警告的選項;選擇最適合您情況的哪一種：

- **防護通話**。 您可以在執行時間依條件呼叫程式碼來達成此目的。 `Platform`使用其中一個平臺檢查方法（例如或），檢查您是否正在執行 `OperatingSystem.Is<Platform>()` `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` 。

- **將呼叫位置標示為平臺特定**。 您也可以選擇將自己的 Api 標記為平臺專屬的 Api，如此一來，就能有效地將需求轉送至您的呼叫端。 使用與參考的平臺相依呼叫相同的屬性，標記包含方法或類型或整個元件。 [範例](#mark-call-site-as-platform-specific)。

- **使用平臺檢查判斷提示呼叫位置**。 如果您不想要在執行時間額外負荷額外的 `if` 語句，請使用 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 。 [範例](#assert-the-call-site-with-platform-check)。

- **刪除程式碼**。 通常不是您想要的，因為這表示當 Windows 使用者使用您的程式碼時，會喪失精確度。 如果存在跨平臺的替代方案，您可能會比使用平臺專用的 Api 更好。

- **隱藏警告**。 您也可以直接透過 EditorConfig 專案或來隱藏警告 `#pragma warning disable ca1416` 。 不過，此選項應該是使用平臺特定 Api 時的最後手段。

### <a name="guard-platform-specific-apis-with-guard-methods"></a>使用 guard 方法保護平臺特定的 Api

Guard 方法的平臺名稱應該與呼叫平臺相依的 API 平臺名稱相符。 如果呼叫 API 的平臺字串包含版本：

- 若為 `[SupportedOSPlatform("platformVersion")]` 屬性，guard 方法平臺 `version` 應大於或等於呼叫平臺的 `Version` 。
- 若為 `[UnsupportedOSPlatform("platformVersion")]` 屬性，guard 方法的平臺 `version` 應小於或等於呼叫平臺的 `Version` 。

  ```csharp
  public void CallingSupportedOnlyApis() // Allow list calls
  {
      if (OperatingSystem.IsWindows())
      {
          WindowsOnlyApi(); // will not warn
      }

      if (OperatingSystem.IsLinux())
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn, within one of the supported context
      }

      // Can use &&, || logical operators to guard combined attributes
      if (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10.0.19041)))
      {
          ApiSupportedFromWindows8UnsupportFromWindows10();
      }

      if (OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903))
      {
          AssemblySupportedOnWindowsApiSupportedFromWindows10(); // Only need to check latest supported version
      }
  }

  public void CallingUnsupportedApis()
  {
      if (!OperatingSystem.IsAndroid())
      {
          DoesNotWorkOnAndroid(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || OperatingSystem.IsWindowsVersionAtLeast(8))
      {
          StartedWindowsSupportFromVersion8(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || // supported all other platforms
         (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903)))
      {
          StartedWindowsSupportFrom8UnsupportedFrom10(); // will not warn
      }
  }
  ```

- 如果您需要保護以 `netstandard` 或 `netcoreapp` 不提供新 api 為目標的程式碼 <xref:System.OperatingSystem> ，則 <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> 可以使用 API，並將會由分析器來遵守。 但是，它並不像新增的 Api 一樣優化 <xref:System.OperatingSystem> 。 如果結構中不支援該平臺 <xref:System.Runtime.InteropServices.OSPlatform> ，您可以呼叫 <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> 並傳入平臺名稱（分析器也會遵循）。

  ```csharp
  public void CallingSupportedOnlyApis()
  {
      if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn
      }

      if (RuntimeInformation.IsOSPlatform(OSPlatform.Create("browser")))
      {
          ApiOnlySupportedOnBrowser(); // call of browser specific API
      }
  }
  ```

### <a name="mark-call-site-as-platform-specific"></a>將呼叫網站標示為平臺特定

平臺名稱應符合呼叫平臺相依的 API。 如果平臺字串包含版本：

- 若為 `[SupportedOSPlatform("platformVersion")]` 屬性，呼叫位置平臺 `version` 應大於或等於呼叫平臺的 `Version`
- 針對 `[UnsupportedOSPlatform("platformVersion")]` 屬性，呼叫網站平臺 `version` 應小於或等於呼叫平臺的 `Version`

  ```csharp
  // an API supported only on Windows.
  [SupportedOSPlatform("windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  [SupportedOSPlatform("windows8.0")] // call site attributed Windows 8.0 or above.
  public void Caller()
  {
      WindowsOnlyApi(); // will not warn as call site is for Windows.

      // will not warn as call site is for Windows.
      SupportedOnWindowsAndLinuxOnly();

      // will not warn for the API's [SupportedOSPlatform("windows8.0")] attribute.
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // as the call site version is lower than calling version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows11.0")] // call site attributed with windows 11.0 or above.
  public void Caller2()
  {
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // will not warn as call site version higher than calling API.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")] // call site supports Windows from version 8.0 to 10.0.19041.0.
  public void Caller3()
  {
      // will not warn as caller has exact same attributes.
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // As call site stopped support from that version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on Android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  [UnsupportedOSPlatform("windows")] // Caller no support Windows for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'Android'.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }

  [UnsupportedOSPlatform("windows")]
  [UnsupportedOSPlatform("android")] // Caller not support Windows and Android for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // will not warn as call site not supports Android.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

### <a name="assert-the-call-site-with-platform-check"></a>使用平臺檢查判斷提示呼叫網站

[平臺防護範例](#guard-platform-specific-apis-with-guard-methods)中使用的所有條件式檢查，也可以當做的條件使用 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 。

  ```csharp
  // An API supported only on Linux.
  [SupportedOSPlatform("linux")]
  public void LinuxOnlyApi() { }

  public void Caller()
  {
      Debug.Assert(OperatingSystem.IsLinux());

      LinuxOnlyApi(); // will not warn
  }
  ```

## <a name="see-also"></a>另請參閱

- [.NET 5 中的目標 Framework 名稱](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [標注平臺特定 Api 並偵測其使用](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [針對特定平臺上不支援的 Api 進行批註](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [CA1416 平臺相容性分析器](/visualstudio/code-quality/ca1416)
- [.NET API 分析器](../../standard/analyzers/api-analyzer.md)
