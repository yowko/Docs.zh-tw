---
title: 目標 Framework
description: 了解 .NET Core 應用程式和程式庫的目標 Framework。
author: richlander
ms.author: mairaw
ms.date: 05/31/2018
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 346eece8fdb391fd62b369db6ef65964fcd6e67a
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728312"
---
# <a name="target-frameworks"></a>目標 Framework

當您以應用程式或程式庫中的架構為目標時，您將指定要提供給應用程式或程式庫的一組 API。 您可以在專案檔中使用目標 Framework Moniker (TFM) 來指定目標 Framework。

應用程式或程式庫可以將目標設為某個版本的 [.NET Standard](~/docs/standard/net-standard.md)。 .NET Standard 版本代表跨所有 .NET 實作的標準化 API 集合。 例如，程式庫可以將目標設為 .NET Standard 1.6，以存取跨 .NET Core 和 .NET Framework (兩者使用相同的程式碼基底) 運作的 API。

應用程式或程式庫也可以將目標設為特定 .NET 實作，以存取實作特定的 API。 例如，以 Xamarin.iOS (例如 `Xamarin.iOS10`) 為目標的應用程式可以存取 iOS 10 之 Xamarin 提供的 iOS API 包裝函式；或者，以通用 Windows 平台 (UWP，`uap10.0`) 為目標的應用程式可以存取針對執行 Windows 10 的裝置所編譯的 API。

針對某些目標 Framework (例如 .NET Framework)，API 是由該架構安裝在系統上的組件所定義，而且可能包含應用程式架構 API (例如 ASP.NET)。

針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，API 是由包含在應用程式或程式庫中的套件所定義。 「中繼套件」是 NuGet 套件，本身沒有任何內容，而是一份相依性 (其他專案) 清單。 以 NuGet 套件為基礎的目標 Framework 會隱含指定一個中繼套件，該套件會參考組成架構的所有套件。

## <a name="latest-target-framework-versions"></a>最新目標 Framework 版本

下表定義最常用的目標 Framework、其參考方式，以及它們所實作的 [.NET Standard](~/docs/standard/net-standard.md) 版本。 這些目標 Framework 版本是最新穩定版本。 不顯示發行前版本。 目標 Framework Moniker (TFM) 是用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。

| 目標 Framework      | Latest <br/> 穩定版本 | Target Framework Moniker (TFM) | 已實作 <br/> .NET Standard 版本 |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.0                         | netstandard2.0                 | N/A                                     |
| .NET Core             | 2.1                         | netcoreapp2.1                  | 2.0                                     |
| .NET Framework        | 4.7.2                       | net472                         | 2.0                                     |

## <a name="supported-target-framework-versions"></a>支援的目標 Framework 版本

目標 Framework 通常會由 TFM 參考。 下表顯示 .NET Core SDK 和 NuGet 用戶端所支援的目標 Framework。 對等項目會顯示在括弧內。 例如，`win81` 是 `netcore451` 的對等 TFM。

| 目標 Framework           | TFM |
| -------------------------- | --- |
| .NET Standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472 |
| Windows 市集              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| 通用 Windows 平台 | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>如何指定目標 Framework

目標 Framework 會在專案檔中指定。 指定單一目標 Framework 時，請使用 **TargetFramework** 項目。 下列主控台應用程式專案檔會示範如何將目標設為 .NET Core 2.0：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

當您指定多個目標 Framework 時，您可以有條件地參考每個目標 Framework 的組件。 在您的程式碼中，您可以使用前置處理器符號搭配 *if-then-else* 邏輯，有條件地對這些組件進行編譯。

下列程式庫專案檔是以 .NET Standard 的 API (`netstandard1.4`) 以及 .NET Framework 的 API (`net40` 和 `net45`) 為目標。 使用具有多個目標 Framework 的複數 **TargetFrameworks** 項目。 當針對兩個 .NET Framework TFM 編譯程式庫時，注意 `Condition` 屬性如何包含實作特定的套件：

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

您可以在程式庫或應用程式中撰寫條件程式碼，為每個目標 Framework 進行編譯：

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

組建系統知道代表目標 Framework 的前置處理器符號，如[支援的目標 Framework 版本](#supported-target-framework-versions)表格中所示。 使用代表 .NET Standard 或 .NET Core TFM 的符號時，請以底線取代點，並將小寫字母變更為大寫 (例如 `netstandard1.4` 的符號是 `NETSTANDARD1_4`)。

.NET Core 目標 Framework 之前置處理器符號的完整清單如下：

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>已被取代的目標 Framework

下列目標 Framework 已被取代。 以這些目標 Framework 為目標的套件應該移轉至所指出的取代項目。

| 已被取代的 TFM                                                                             | Replacement |
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

[套件、中繼套件和架構](../core/packages.md)  
[使用跨平台工具開發程式庫](../core/tutorials/libraries.md)  
[.NET Standard](net-standard.md)  
[.NET Core 版本控制](../core/versions/index.md)  
[dotnet/standard GitHub 存放庫](https://github.com/dotnet/standard)  
[NuGet 工具 GitHub 存放庫](https://github.com/joelverhagen/NuGetTools)  
[Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html) (.NET 中的 Framework 設定檔)
