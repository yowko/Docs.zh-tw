---
title: SDK 樣式專案中的目標 framework-.NET
description: 瞭解 .NET 應用程式和程式庫的目標 framework。
ms.date: 09/08/2020
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 22689f6c1f161a67978dc0f41c6bc9a6b5acfad7
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065249"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>SDK 樣式專案中的目標 framework

當您以應用程式或程式庫中的架構為目標時，您將指定要提供給應用程式或程式庫的一組 API。 您可以使用目標 framework 標記 (Tfm) ，在專案檔中指定目標 framework。

應用程式或程式庫可以將目標設為某個版本的 [.NET Standard](net-standard.md)。 .NET Standard 版本代表跨所有 .NET 實作的標準化 API 集合。 例如，程式庫可以將目標設為 .NET Standard 1.6，以存取跨 .NET Core 和 .NET Framework (兩者使用相同的程式碼基底) 運作的 API。

應用程式或程式庫也可以將目標設為特定 .NET 實作，以存取實作特定的 API。 例如，以 Xamarin 為目標的應用程式 (例如， `Xamarin.iOS10`) 可存取適用于 iOS 10 的 xamarin 提供的 IOS API 包裝函式，或是以通用 Windows 平臺 (UWP 為目標的應用程式， `uap10.0`) 可以存取針對執行 Windows 10 的裝置進行編譯的 api。

針對某些目標 framework (例如 .NET Framework) ，Api 是由架構安裝在系統上的元件所定義，而且可能包含應用程式架構 Api (例如 ASP.NET) 。

針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，API 是由包含在應用程式或程式庫中的套件所定義。 「中繼套件」** 是 NuGet 套件，本身沒有任何內容，而是一份相依性 (其他專案) 清單。 以 NuGet 套件為基礎的目標 Framework 會隱含指定一個中繼套件，該套件會參考組成架構的所有套件。

## <a name="latest-versions"></a>最新版本

下表定義最常用的目標 Framework、其參考方式，以及它們所實作的 [.NET Standard](net-standard.md) 版本。 這些目標 Framework 版本是最新穩定版本。 不顯示發行前版本。 目標 framework 標記 (TFM) 是標準化的標記格式，用於指定 .NET 應用程式或程式庫的目標 framework。

| 目標架構      | Latest <br/> 穩定版本 | 目標 framework 標記 (TFM)  | 已實作 <br/> .NET Standard 版本 |
| :-: | :-: | :-: | :-: |
| .NET Standard         | 2.1                         | netstandard 2。1                 | N/A                                     |
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

您也可以指定選用的 OS 版本，例如 `net5.0-ios12.0` 。

如需 .NET 5 Tfm 的詳細資訊，請參閱 [.net 5 中的目標 framework 名稱](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)。

## <a name="how-to-specify-a-target-framework"></a>如何指定目標 framework

目標 framework 是在專案檔中指定。 指定單一目標 Framework 時，請使用 **TargetFramework** 項目。 下列主控台應用程式專案檔會示範如何將目標設為 .NET 5.0：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

當您指定多個目標 Framework 時，您可以有條件地參考每個目標 Framework 的組件。 在您的程式碼中，您可以使用前置處理器符號搭配 *if-then-else* 邏輯，有條件地對這些組件進行編譯。

下列程式庫專案的目標是 .NET Standard (`netstandard1.4`) 和 .NET Framework (`net40` 和 `net45`) 的 api。 使用具有多個目標 Framework 的複數 **TargetFrameworks** 項目。 `Condition`當您針對兩個 .NET Framework tfm 編譯程式庫時，屬性會包含特定的執行套件：

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

## <a name="see-also"></a>另請參閱

- [使用跨平台工具開發程式庫](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [.NET Core 版本控制](../core/versions/index.md)
- [dotnet/standard GitHub 存放庫](https://github.com/dotnet/standard)
- [NuGet 工具 GitHub 存放庫](https://github.com/joelverhagen/NuGetTools)
- [Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html) (.NET 中的 Framework 設定檔)
