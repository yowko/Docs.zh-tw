---
title: SDK 樣式專案中的目標 framework-.NET
description: 瞭解 .NET 應用程式和程式庫的目標 framework。
ms.date: 11/06/2020
ms.prod: dotnet
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 7a3dcd61c330607bacf0d05dbd775c62cfa15b37
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765055"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>SDK 樣式專案中的目標 framework

當您以應用程式或程式庫中的架構為目標時，您將指定要提供給應用程式或程式庫的一組 API。 您可以使用目標 framework 標記 (TFM) ，在專案檔中指定目標 framework。

應用程式或程式庫可以將目標設為某個版本的 [.NET Standard](net-standard.md)。 .NET Standard 版本代表跨所有 .NET 實作的標準化 API 集合。 例如，程式庫可以將目標設為 .NET Standard 1.6，以存取跨 .NET Core 和 .NET Framework (兩者使用相同的程式碼基底) 運作的 API。

應用程式或程式庫也可以將目標設為特定 .NET 實作，以存取實作特定的 API。 例如，以 Xamarin 為目標的應用程式 (例如， `Xamarin.iOS10`) 可存取適用于 iOS 10 的 xamarin 提供的 IOS API 包裝函式，或是以通用 Windows 平臺 (UWP 為目標的應用程式， `uap10.0`) 可以存取針對執行 Windows 10 的裝置進行編譯的 api。

針對某些目標 framework （例如 .NET Framework），Api 是由架構安裝在系統上的元件所定義，而且可能包含應用程式架構 Api (例如 ASP.NET) 。

針對以套件為基礎的目標 framework (例如，.NET 5、.NET Core 和 .NET Standard) ，Api 是由應用程式或程式庫中包含的 NuGet 套件所定義。

## <a name="latest-versions"></a>最新版本

下表定義最常見的目標 framework、其參考方式，以及它們所執行的 [.NET Standard](net-standard.md) 版本。 這些目標 Framework 版本是最新穩定版本。 不顯示發行前版本。 目標 framework 標記 (TFM) 是標準化的標記格式，用於指定 .NET 應用程式或程式庫的目標 framework。

| 目標架構      | Latest <br/> 穩定版本 | 目標 framework 標記 (TFM)  | 已實作 <br/> .NET Standard 版本 |
| :-: | :-: | :-: | :-: |
| .NET 5                | 5.0                         | net 5。0                         | 不適用                                     |
| .NET Standard         | 2.1                         | netstandard 2。1                 | 不適用                                     |
| .NET Core             | 3.1                         | netcoreapp 3。1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-frameworks"></a>支援的目標 framework

目標 Framework 通常會由 TFM 參考。 下表顯示 .NET SDK 和 NuGet 用戶端支援的目標 framework。 對等項目會顯示在括弧內。 例如，`win81` 是 `netcore451` 的對等 TFM。

| 目標 Framework           | TFM |
| -------------------------- | --- |
| .NET 5 (和 .NET Core)      | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2.2<br>netcoreapp 3。0<br>netcoreapp 3。1<br>net 5.0 * |
| .NET Standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0<br>netstandard 2。1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows 市集              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| 通用 Windows 平台 | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

\* .NET 5.0 和更新版本的 Tfm 包含作業系統特定的變化。 如需詳細資訊，請參閱下一節： [.net 5 作業系統特定 tfm](#net-5-os-specific-tfms)。

### <a name="net-5-os-specific-tfms"></a>.NET 5 作業系統專用 Tfm

例如，針對每個 .NET 5.0 和更新版本的 TFM， `net5.0` 都有 TFM 的變化，其中包含作業系統特定的系結。 下表顯示這些變化。

| 作業系統特定格式 | 範例        |
|--------------------|----------------|
| \<base-tfm>-android | net 5.0-android |
| \<base-tfm>-ios     | net 5.0-ios     |
| \<base-tfm>-macos   | net 5.0-macos   |
| \<base-tfm>-tvos    | net 5.0-tvos    |
| \<base-tfm>-watchos | net 5.0-watchos |
| \<base-tfm>>microsoft-windows-powershell | net 5.0-windows |

`net5.0`TFM 僅包含可跨平臺運作的技術。 指定作業系統特定的 TFM，可讓您的應用程式使用的作業系統專用 Api，例如 Windows Forms 或 iOS 系結。 作業系統專用的 Tfm 也會繼承 TFM 可用的每個 API `net5.0` 。

若要讓您的應用程式可在不同平臺上使用，您可以將目標設為多個 OS 專用 Tfm，並使用預處理器指示詞，在 OS 特定 API 呼叫周圍新增平臺防護 `#if` 。

下表顯示 .NET 5 Tfm 與舊版 .NET 版本 Tfm 的相容性。

| TFM             | 相容于                                            | 注意 |
|-----------------|------------------------------------------------------------|-|
| net 5。0          | net1..具有 NU1701 警告的 4 () <br />netcoreapp1..3.1 (參考 WinForms 或 WPF 時發出警告) <br />netstandard1..2.1 | |
| net 5.0-android  | xamarin. android (再加上繼承自) 的其他專案 `net5.0` | |
| net 5.0-ios      | xamarin (再加上繼承自) 的其他所有專案 `net5.0` | |
| net 5.0-macos    | xamarin (再加上繼承自) 的其他所有專案 `net5.0` | |
| net 5.0-tvos     | xamarin. tvos (再加上繼承自) 的其他專案 `net5.0` | |
| net 5.0-watchos  | xamarin. watchos (再加上繼承自) 的其他專案 `net5.0` | |
| net 5.0-windows  | netcoreapp1..3.1 (以及繼承自) 的其他專案 `net5.0` | 包含 WinForms、WPF 和 UWP Api。<br />如需詳細資訊，請參閱 [在桌面應用程式中呼叫 Windows 執行階段 api](/windows/apps/desktop/modernize/desktop-to-uwp-enhance)。 |

#### <a name="suggested-targets"></a>建議的目標

使用這些指導方針來判斷要在您的應用程式中使用的 TFM：

- 可移植至多個平臺的應用程式應該以目標 `net5.0` 。 這包括大部分的程式庫，但也 ASP.NET Core 和 Entity Framework。

- 平臺特定程式庫應以平臺特定的類別為目標。 例如，WinForms 和 WPF 專案應設為目標 `net5.0-windows` 。

- 跨平臺應用程式模型 (Xamarin 表單、ASP.NET Core) 和橋接器套件 (Xamarin Essentials) 至少應 `net5.0` 為目標，但可能也會以其他平臺特定的類別為目標，以加速更多 api 或功能。

#### <a name="os-version-in-tfms"></a>Tfm 中的作業系統版本

您也可以在 TFM 結尾指定選用的 OS 版本，例如， `net5.0-ios13.0` 指出您的應用程式可使用的 api。  (.NET 5 SDK 將會更新，以在發行時支援較新的 OS 版本。 ) 若要取得新發行的 Api，請將 TFM 中的作業系統版本遞增。 您仍然可以將應用程式與舊版作業系統相容 (，並將專案新增至您的專案檔，以新增對較新版本) Api 呼叫的防護 `SupportedOSPlatformVersion` 。 `SupportedOSPlatformVersion`元素表示執行您的應用程式所需的最低作業系統版本。

例如，下列專案檔摘錄會指定 iOS 14 Api 可供應用程式使用，但它可以在 iOS 13 或更新版本的電腦上執行。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net5.0-ios14.0</TargetFramework>
    <SupportedOSPlatformVersion>13.0</SupportedOSPlatformVersion> (minimum os platform version)
  </PropertyGroup>

  ...

</Project>
```

## <a name="how-to-specify-a-target-framework"></a>如何指定目標 framework

目標 framework 是在專案檔中指定。 當指定單一目標 framework 時，請使用 [TargetFramework 元素](../core/project-sdk/msbuild-props.md#targetframework)。 下列主控台應用程式專案檔會示範如何將目標設為 .NET 5.0：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

當您指定多個目標 Framework 時，您可以有條件地參考每個目標 Framework 的組件。 在您的程式碼中，您可以使用前置處理器符號搭配 *if-then-else* 邏輯，有條件地對這些組件進行編譯。

下列程式庫專案的目標是 .NET Standard (`netstandard1.4`) 和 .NET Framework (`net40` 和 `net45`) 的 api。 使用具有多個目標 framework 的複數 [TargetFrameworks 元素](../core/project-sdk/msbuild-props.md#targetframeworks) 。 `Condition`當您針對兩個 .NET Framework tfm 編譯程式庫時，屬性會包含特定的執行套件：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

在您的程式庫或應用程式中，您可以使用 [預處理器](../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞，針對每個目標 framework 編譯條件式程式碼：

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

當您使用 SDK 樣式專案時，組建系統會注意代表支援的 [目標 framework 版本](#supported-target-frameworks) 資料表中所顯示之目標 framework 的預處理器符號。 使用代表 .NET Standard、.NET Core 或 .NET 5 TFM 的符號時，以底線取代點和連字號，並將小寫字母變更為大寫 (例如，的符號 `netstandard1.4` 會 `NETSTANDARD1_4`) 。

.NET 目標 framework 的預處理器符號完整清單如下：

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>已被取代的目標 Framework

下列目標 Framework 已被取代。 以這些目標 framework 為目標的套件應該遷移至指示的取代。

| 已被取代的 TFM                                                                             | 取代 |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| win                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>請參閱

- [.NET 5 中的目標 framework 名稱](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [使用跨平台工具開發程式庫](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [.NET Core 版本控制](../core/versions/index.md)
- [dotnet/standard GitHub 存放庫](https://github.com/dotnet/standard)
- [NuGet 工具 GitHub 存放庫](https://github.com/joelverhagen/NuGetTools)
- [Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html) (.NET 中的 Framework 設定檔)
- [平台相容性分析器](analyzers/platform-compat-analyzer.md)
