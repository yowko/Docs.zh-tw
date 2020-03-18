---
title: 包、元包和框架 - .NET 核心
description: 了解套件、中繼套件和架構的術語。
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 657519edf1c0860ee3222c71ce85723e19029a9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398976"
---
# <a name="packages-metapackages-and-frameworks"></a>套件、中繼套件和架構

.NET Core 是由 NuGet 套件構成的平台。 有些產品體驗可獲益於細部定義的套件，有些則更適合廣泛定義的套件。 為了適應這種二元性，.NET Core 作為一組細細微性的包和粗糙的塊進行分發，包裝類型非正式地稱為[元包](#metapackages)。

每個 .NET Core 包都支援在多個 .NET 實現上運行，表示為框架。 其中一些框架是傳統的框架，如`net46`，它表示 .NET 框架。 其他還有可以視為「套件型架構」的全新架構，該架構可以建立新的模型來定義架構。 這些基於包的框架完全創建並定義為包，在包和框架之間形成了牢固的關係。

## <a name="packages"></a>Packages

.NET Core 被拆分為一組包，提供基元、高級資料類型、應用組合類型和通用實用程式。 每個包都表示同名的單個程式集。 例如，[系統.運行時包](https://www.nuget.org/packages/System.Runtime)包含系統.Runtime.dll。

以細部方式定義的套件有下列許多優點：

- 細部套件可以按照自己的排程出貨，且僅會對其他套件進行相對有限的測試。
- 細部套件可以提供不同的作業系統和 CPU 支援。
- 細部套件可以僅具有特定一個程式庫的專屬相依性。
- 由於未參考的套件不會跟應用程式一起散發，因此應用程式比較小。

其中有些優勢只適用於特定情況。 比方說，.NET Core 套件的出貨時間通常與相同平台支援的排程相同。 需要進行服務時，修正程式可以透過小型單一套件更新的形式來散發和安裝。 由於變更的範圍較窄，修正程式的驗證和提供時間可以僅限於滿足單一程式庫的需求。

以下是 .NET Core 的主要 NuGet 套件清單：

- [系統.運行時](https://www.nuget.org/packages/System.Runtime)- 最基本的 .NET 核心包，<xref:System.Object>包括<xref:System.String> <xref:System.Array>、<xref:System.Action>和<xref:System.Collections.Generic.IList%601>。
- [System.Collections](https://www.nuget.org/packages/System.Collections) \(英文\)：(主要為) 泛型集合的組合，包括 <xref:System.Collections.Generic.List%601> 和 <xref:System.Collections.Generic.Dictionary%602>。
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) \(英文\)：HTTP 網路通訊類型的組合，包括 <xref:System.Net.Http.HttpClient> 和 <xref:System.Net.Http.HttpResponseMessage>。
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) \(英文\)：用來讀取和寫入本機或網路磁碟型儲存裝置的類型組合，包括 <xref:System.IO.File> 和 <xref:System.IO.Directory>。
- [System.Linq](https://www.nuget.org/packages/System.Linq) \(英文\)：用來查詢物件的類型組合，包括 `Enumerable` 和 <xref:System.Linq.ILookup%602>。
- [系統.反射](https://www.nuget.org/packages/System.Reflection)- 一組用於載入、檢查和啟動類型的類型，包括<xref:System.Reflection.Assembly>和 。 <xref:System.Reflection.TypeInfo> <xref:System.Reflection.MethodInfo>

一般來說，包含[中繼套件](#metapackages)比包含每個套件更簡單且穩固。 不過，當您需要單一套件時，您可以如下列範例所示將它加入，該範例參考 [System.Runtime](https://www.nuget.org/packages/System.Runtime/) \(英文\) 套件。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>中繼套件

元包是一種 NuGet 包約定，用於描述一組有意義的一起。 元包通過使它們成為依賴項來表示這組包。 元包可以通過指定框架來選擇為包集建立框架。

根據預設，舊版的 .NET Core 工具 (project.json 和 csproj 工具) 已指定架構和中繼套件。 不過目前，目標架構會隱含參考中繼套件，因此每個中繼套件都會繫結至目標架構。 例如，`netstandard1.6` 架構會參考 NetStandard.Library 1.6.0 版的中繼套件。 同樣地，`netcoreapp2.1` 架構會參考 Microsoft.NETCore.App 2.1.0 版的中繼套件。 如需詳細資訊，請參閱 [Implicit metapackage package reference in the .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md) (.NET Core SDK 中的隱含中繼套件參考)。

以框架為目標並隱式引用元包意味著實際上，您將作為單個筆勢添加對其每個從屬包的引用。 這會讓這些套件中的所有程式庫都可供 IntelliSense (或類似體驗) 使用，以及用於發行您的應用程式。

使用中繼套件的優點如下：

- 讓參考大量細部套件的使用者體驗更方便。
- 其中所定義的套件組 (包括特定版本)，均經過測試且適合共同運作。

.NET Standard 中繼套件是：

- [NET標準.庫](https://www.nuget.org/packages/NETStandard.Library)- 描述屬於 .NET 標準的庫。 適用于所有支援 .NET 標準實現的 .NET 實現（例如.NET 框架、.NET 核心和單聲道）。 建立`netstandard`框架。

主要的 .NET Core 中繼套件包括：

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) - 描述屬於 .NET Core 散發套件的程式庫。 建立`.NETCoreApp`框架。 仰賴較小的 `NETStandard.Library`。
- [Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) \(英文\) - 包含所有來自 ASP.NET Core 和 Entity Framework Core 之支援的套件，除了那些包含協力廠商相依性的套件。 如需詳細資訊，請參閱 [ASP.NET Core 的 Microsoft.AspNetCore.App 中繼套件](/aspnet/core/fundamentals/metapackage-app)。
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) - 包含 ASP.NET Core 所有支援的套件、Entity Framework Core，以及 ASP.NET Core 和 Entity Framework Core 所使用的內部和協力廠商相依性。 如需詳細資訊，請參閱 [ASP.NET Core 2.x 的 Microsoft.AspNetCore.All 中繼套件](/aspnet/core/fundamentals/metapackage)。
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) - 一組相容性 facade，其可啟用以 mscorlib 為基礎的可攜式類別庫 (PCL)，以在 .NET Core 上執行。

## <a name="frameworks"></a>架構

每個 .NET Core 套件都會支援一組執行階段架構。 架構也說明了具有特定架構目標時可以仰賴的可用 API 集 (和其他可能的特性)。 當有新的 API 加入時，就會為其建立版本。

例如，[System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) 支援下列架構：

- .NETFramework,Version=4.6
- .NETStandard,Version=1.3
- 6 Xamarin 平台 (例如 xamarinios10)

對比前兩個框架非常有用，因為它們是定義框架的兩種不同方法的示例：

- 該`.NETFramework,Version=4.6`框架表示 .NET 框架 4.6 中的可用 API。 可以生成使用 .NET Framework 4.6 引用程式集編譯的庫，然後在 net46 lib 資料夾中在 NuGet 包中分發這些庫。 它將用於針對 .NET 框架 4.6 或與其相容的應用。 這是所有架構的傳統運作方式。

- `.NETStandard,Version=1.3` 架構是以套件為基礎的架構。 它需仰賴以架構為目標的套件，並根據該架構來定義並公開 API。

## <a name="package-based-frameworks"></a>以套件為基礎的架構

架構和套件之間沒有雙向關聯性。 第一個部分要定義特定架構可用的 API，例如 `netstandard1.3`。 目標為 `netstandard1.3` (或 `netstandard1.0` 這類相容架構) 的套件會定義 `netstandard1.3` 可用的 API。 這乍聽之下像是循環定義，其實不然。 由於是「以套件為基礎」，因此架構的 API 定義也來自套件。 架構本身並不會定義任何 API。

關聯性的第二個部分是資產的選取項目。 套件可以包含多個架構的資產。 參考一組套件及/或中繼套件時，需要依據架構來判斷應該選取哪些資產，例如 `net46` 或 `netstandard1.3`。 選擇正確的資產非常重要。 例如，`net46` 資產不太可能相容於 .NET Framework 4.0 或 .NET Core 1.0。

您可以在下圖中看到此關聯性。 *API* 會以「架構」** 為目標，並加以定義。 「架構」** 可用來「選取資產」**。 「資產」** 可提供 API。

![以套件為基礎的架構組合](./media/packages/package-framework.png)

搭配 .NET Core 使用的主要套件型架構有以下兩個：

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET 標準 （[目標框架 Moniker](../standard/frameworks.md)： `netstandard`） 框架表示由 .NET 標準定義並構建在[.NET 標準](../standard/net-standard.md)之上的 API。 要在多個執行階段上執行的程式庫應以此架構為目標。 它們將在任何符合 .NET 標準的運行時（如 .NET Core、.NET Framework 和 Mono/Xamarin）上得到支援。 其中每個執行階段都支援一組 .NET Standard 版本，這取決於它們實作哪些 API 而定。

框架`netstandard`隱式引用[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library)元包。 例如，以下 MSBuild 專案檔案指示專案目標`netstandard1.6`， 引用[`NETStandard.Library`版本 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0)元包。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

不過，專案檔中的架構和中繼套件參考不需要相符，而且您可以使用專案檔中的 `<NetStandardImplicitPackageVersion>` 項目，指定低於中繼套件版本的架構版本。 例如，以下是有效的專案檔。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

目標為 `netstandard1.3` 卻使用 `NETStandard.Library` 1.6.0 版，看似不合理， 但這是有效的使用案例，因為中繼套件仍支援舊版的 `netstandard`。 如果您已經在 1.6.0 版中繼套件上進行標準化，並將其用於所有程式庫，且這些程式庫的目標為各種 `netstandard` 版本時，就可能發生這種情況。 使用這個方法時，您只需要還原 `NETStandard.Library` 1.6.0 而不需還原舊版。

若是使用 `NETStandard.Library` 1.3.0 版但目標為 `netstandard1.6`，這種反向情況無效。 由於較低版本的中繼套件不會公開較高架構的任何資產，因此使用較低的中繼套件時，您不能將目標設為更高的架構。 中繼套件的版本配置會判斷提示中繼套件應符合所描述架構的最高版本。 由於版本配置的特性，假設第一個 `NETStandard.Library` 版本包含 `netstandard1.6` 資產，該版本即為 v1.6.0。 （對於與前一個示例的對稱性，此處使用 v1.3.0，但實際上不存在。

### <a name="net-core-application"></a>.NET Core 應用程式

.NET 核心 （[目標框架 Moniker](../standard/frameworks.md)： `netcoreapp`） 框架表示 .NET Core 分發及其提供的主控台應用程式模型附帶的包和相關 API。 由於目標為主控台應用程式模型，因此 .NET Core 應用程式必須使用此架構，包括僅限於 .NET Core 中執行的程式庫也應如此。 使用此架構時，可限制應用程式和程式庫僅在 .NET Core 中執行。

`Microsoft.NETCore.App` 中繼套件是以 `netcoreapp` 架構為目標。 它提供約 ~60 種程式庫的存取權，其中 `NETStandard.Library` 套件提供約 ~40 種，另外再加上 ~20 多種。 若要存取其他 API，您可以參考其他目標為 `netcoreapp` 或相容架構的程式庫，例如 `netstandard`。

大部分由 `Microsoft.NETCore.App` 所提供的其他程式庫也會以 `netstandard` 為目標 (在其他 `netstandard` 程式庫滿足其相依性的情況下)。 這表示 `netstandard` 程式庫也可以將這些套件做為相依性參考。
