---
title: 適用於 .NET Core 之 csproj 格式的新增項目
description: 深入了解現有和 .NET Core csproj 檔案之間的差異
ms.date: 04/08/2019
ms.openlocfilehash: 2ec1aaff88754848d844a56b1744beb2efa4cd89
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291229"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>適用於 .NET Core 之 csproj 格式的新增項目

本文件概述從 *project.json* 改為使用 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至專案檔的變更。 如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。

## <a name="implicit-package-references"></a>隱含套件參考

會根據您專案檔之 `<TargetFramework>` 或 `<TargetFrameworks>` 屬性中指定的目標架構來隱含參考中繼套件。 如果指定了 `<TargetFramework>`，則會忽略 `<TargetFrameworks>`，與順序無關。 如需詳細資訊，請參閱[套件、中繼套件和架構](../packages.md)。 

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>建議

由於會隱含參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件，因此建議使用下列最佳做法：

* 以 .NET Core 或 .NET Standard 為目標時，絕不透過專案檔中的 `<PackageReference>` 項目明確參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件。
* 如果您以 .NET Core 為目標時需要特定版本的執行階段，您應該使用專案中的 `<RuntimeFrameworkVersion>` 屬性 (例如 `1.0.4`)，而不是參考中繼套件。
  * 如果您使用[獨立性部署](../deploying/index.md#self-contained-deployments-scd)，並需要 1.0.0 LTS 執行階段的特定更新程式版本，就可能會發生此情況。
* 如果您以 .NET Standard 為目標時需要特定版本的 `NETStandard.Library` 中繼套件，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性並設定所需的版本。
* 請不要在 .NET Framework 專案中明確地新增或更新 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件的參考。 如果使用 .NET Standard 型 NuGet 套件時需要任何版本的 `NETStandard.Library`，NuGet 會自動安裝該版本。

## <a name="implicit-version-for-some-package-references"></a>某些套件參考的隱含版本

[`<PackageReference>`](#packagereference) 的大部分使用方式都需要設定 `Version` 屬性來指定要使用的 NuGet 套件版本。 不過，使用 .NET Core 2.1 或 2.2 並參考 [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) 或 [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage) 時，該屬性是不必要的。 .NET Core SDK 可以自動針對這些套件選取應使用的版本。

### <a name="recommendation"></a>建議

參考 `Microsoft.AspNetCore.App` 或 `Microsoft.AspNetCore.All` 套件時，請不要指定其版本。 若指定版本，SDK 可能會產生警告 NETSDK1071。 若要修正此警告，請移除套件版本，如下列範例所示：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> 已知問題：.NET Core 2.1 SDK 僅在專案同時使用 Microsoft.NET.Sdk.Web 時才支援此語法。 此問題已在 .NET Core 2.2 SDK 中解決。

這些針對 ASP.NET Core 中繼套件的參考，具有和大部分的一般 NuGet 套件些微不同的行為。 使用這些中繼套件之應用程式的[架構相依部署](../deploying/index.md#framework-dependent-deployments-fdd)會自動利用 ASP.NET Core 共用架構的優點。 當您使用中繼套件時，系統**不會**搭配應用程式部署來自所參考之 ASP.NET Core NuGet 套件的任何資產；ASP.NET Core 共用架構會包含這些資產。 共用架構中的資產會針對目標平台最佳化，以改善應用程式啟動時間。 如需共用架構的詳細資訊，請參閱 [.NET Core 發佈封裝](../build/distribution-packaging.md)。

如果「已指定」某個版本，系統會將它視為 ASP.NET Core 共用架構適用於架構相依部署的「最小」版本，以及獨立式部署的「確切」版本。 這可能會導致下列結果：

* 如果安裝在伺服器上的 ASP.NET Core 版本小於 PackageReference 上所指定的版本，.NET Core 處理序將無法啟動。 針對中繼套件的更新通常會在於裝載環境 (例如 Azure) 中推出之前，先在 NuGet.org 上提供使用。 將 PackageReference 上的版本更新為 ASP.NET Core 的版本，可能會導致已部署的應用程式發生失敗。
* 如果應用程式是以[獨立式部署](../deploying/index.md#self-contained-deployments-scd)的形式部署，該應用程式可能不會包含針對 .NET Core 的最新安全性更新。 沒有指定版本時，獨立式部署中的 SDK 可以自動包含最新版本的 ASP.NET Core。

## <a name="default-compilation-includes-in-net-core-projects"></a>.NET Core 專案中包含預設編譯

隨著改為使用最新 SDK 版本中的 *csproj* 格式，編譯項目的預設包含項目和排除項目以及內嵌資源都已移至 SDK 屬性檔。 這表示您不再需要於專案檔中指定這些項目。

這樣做的主要原因是為了讓專案檔更為簡潔。 SDK 中的預設值應該涵蓋最常見的使用案例，而不需要在每個建立的專案中重複這些項目。 這會產生較小的專案檔，而更容易了解及視需要手動編輯。

下表顯示 SDK 中會同時包含及排除的元素與 [Glob (英文)](https://en.wikipedia.org/wiki/Glob_(programming))：

| 元素           | 包含 Glob                              | 排除 Glob                                                  | 移除 Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| 編譯           | \*\*/\*.cs (或其他語言副檔名) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | N/A                      |
| 內嵌資源  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs、\*\*/\*.resx   |

> [!NOTE]
> **排除 Glob** 一律會排除 `./bin` 和 `./obj` 資料夾，其分別由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 屬性所代表。 整體而言，所有排除都是由 `$(DefaultItemExcludes)` 所代表。

如果您的專案有 Glob，而且您嘗試使用最新的 SDK 建置專案，您會收到下列錯誤：

> 包含了重複的編譯項目。 .NET SDK 預設會包含您專案目錄中的編譯項目。 您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。

若要解決此錯誤，您可以明確移除符合上表所列項目的 `Compile` 項目，或將 `<EnableDefaultCompileItems>` 屬性設定為 `false`，如下所示：

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

將此屬性設定為 `false` 會停用隱含包含項目，還原成必須在專案中指定預設 Glob 的舊版 SDK 行為。

這項變更不會修改其他包含項目的主要機制。 不過，如果您想要指定某些檔案由應用程式發行，您仍然可以使用 *csproj* 中已知的機制來執行這項作業 (例如 `<Content>` 項目)。

`<EnableDefaultCompileItems>` 只會停用 `Compile` GLOB，而不會影響隱含 `None` GLOB 這類其他 GLOB，後者也會套用至 \*.cs 項目。 因此，方案總管會繼續將 \*.cs 項目顯示為包含為 `None` 項目之專案的一部分。 透過類似的方式，您可以將 `<EnableDefaultNoneItems>` 設為 False 以停用隱含 `None` GLOB，如下所示：

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

若要停用**所有隱含 GLOB**，您可以將 `<EnableDefaultItems>` 屬性設定為 `false`，如下列範例所示：

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>如何以 MSBuild 查看專案的方式查看整個專案

雖然那些 csproj 變更可大幅簡化專案檔，在包括 SDK 和其目標之後，您可能會想要以 MSBuild 查看專案的方式查看完全展開的專案。 使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 切換](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 對專案進行前置處理，它可以在不需要實際建置專案的情況下，顯示匯入的檔案、檔案的來源，以及該檔案對組建的貢獻：

`dotnet msbuild -pp:fullproject.xml`

如果專案具有多個目標架構，系統應該會透過將它們的其中之一指定為 MSBuild 屬性，來使命令的結果專注於該目標架構：

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>新增項目

### <a name="sdk-attribute"></a>Sdk 屬性

*.csproj* 檔案的根 `<Project>` 元素有一個新屬性，稱為 `Sdk`。 `Sdk` 會指定專案將使用的 SDK。 如[分層文件](cli-msbuild-architecture.md)所述，SDK 是可建置 .NET Core 程式碼的一組 MSBuild [工作](/visualstudio/msbuild/msbuild-tasks)和[目標](/visualstudio/msbuild/msbuild-targets)。 下列 Sdk 適用于 .NET Core：

1. 識別碼為 `Microsoft.NET.Sdk` 的 .NET Core SDK
2. 識別碼為 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK
3. 識別碼為 `Microsoft.NET.Sdk.Razor` 的 .NET Core Razor 類別庫 SDK
4. 識別碼為 `Microsoft.NET.Sdk.Worker` 的 .NET Core 背景工作角色服務（自 .NET Core 3.0 起）
5. 具有 `Microsoft.NET.Sdk.WindowsDesktop` 識別碼的 .NET Core WinForms 和 WPF （自 .NET Core 3.0 起）

您必須在 `<Project>` 項目中將 `Sdk` 屬性設定為上述其中一個識別碼，才能使用 .NET Core 工具並建置您的程式碼。

### <a name="packagereference"></a>PackageReference

`<PackageReference>` 項目元素會[在專案中指定 NuGet 相依性](/nuget/consume-packages/package-references-in-project-files)。 `Include` 屬性會指定套件識別碼。

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

必要的 `Version` 屬性會指定要還原的套件版本。 該屬性採用 [NuGet 版本控制](/nuget/reference/package-versioning#version-ranges-and-wildcards)配置的規則。 預設行為是確切的版本相符。 例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets、ExcludeAssets 和 PrivateAssets

`IncludeAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。 根據預設，所有套件資產均包含在內。

`ExcludeAssets` 屬性指定不應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。

`PrivateAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定但未流向下一個專案的套件)。 根據預設，當此屬性不存在時，`Analyzers`、`Build` 和 `ContentFiles` 會是私人資產。

> [!NOTE]
> `PrivateAssets` 相當於 *project.json*/*xproj* `SuppressParent` 項目。

這些屬性可包含下列一或多個項目，若列出不只一個，則以分號 `;` 字元分隔：

* `Compile` – lib 資料夾的內容可供編譯。
* `Runtime` – 會散發 runtime 資料夾的內容。
* `ContentFiles` - 會使用 *contentfiles* 資料夾的內容。
* `Build` – 會使用組建資料夾中的屬性/目標。
* `Native` – 原生資產內容會複製到執行階段輸出資料夾。
* `Analyzers` – 會使用分析器。

另外，該屬性也可以包含︰

* `None` – 未使用任何資產。
* `All` – 會使用所有資產。

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
`<DotNetCliToolReference>` 項目元素指定使用者想要在專案內容中還原的 CLI 工具。 它會取代 *project.json* 中的 `tools` 節點。

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Version

`Version` 指定要還原的套件版本。 該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。 預設行為是確切的版本相符。 例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`<RuntimeIdentifiers>` 屬性元素可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../rid-catalog.md) 清單。
RID 允許發行獨立部署。

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`<RuntimeIdentifier>` 屬性元素可讓您針對專案只指定一個[執行階段識別碼 (RID)](../rid-catalog.md)。 RID 允許發佈獨立式部署。

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

如果您需要發佈以供多個執行階段使用，請改用 `<RuntimeIdentifiers>` (複數)。 只需要單一執行階段時，`<RuntimeIdentifier>` 可提供更快速的組建。

### <a name="packagetargetfallback"></a>PackageTargetFallback

`<PackageTargetFallback>` 屬性元素可讓您指定一組要在還原套件時使用的相容目標。 其設計目的是為了讓使用 dotnet [TxM (目標 x Moniker)](/nuget/schema/target-frameworks) 的套件能和未宣告 dotnet TxM 的套件一起運作。 如果您的專案使用 dotnet TxM，除非您將 `<PackageTargetFallback>` 新增至專案，以讓非 dotnet 平台變成能與 dotnet 相容，否則其相依的所有套件也必須要有 dotnet TxM。

下列範例可為專案中的所有目標提供後援：

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

下列範例只會為 `netcoreapp2.1` 目標指定後援︰

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>NuGet 中繼資料屬性

隨著改為使用 MSBuild，我們已經將封裝 NuGet 套件時使用的輸入中繼資料從 *project.json* 移動到 *.csproj* 檔。 此輸入是 MSBuild 屬性，因此必須移至 `<PropertyGroup>` 群組。 使用 `dotnet pack` 命令或屬於 SDK 一部分的 `Pack` MSBuild 目標時，會將下列的屬性清單當成封裝處理序的輸入使用。

### <a name="ispackable"></a>IsPackable

布林值，指定是否可封裝專案。 預設值為 `true`。

### <a name="packageversion"></a>PackageVersion

指定所產生之套件的版本。 接受所有形式的 NuGet 版本字串。 預設為 `$(Version)` 的值，也就是專案中的屬性 `Version`。

### <a name="packageid"></a>PackageId

指定所產生之套件的名稱。 如果未指定，`pack` 作業會預設為使用 `AssemblyName` 或目錄名稱作為套件的名稱。

### <a name="title"></a>標題

套件的易記標題，通常會用於 UI 顯示，以及 nuget.org 和 Visual Studio 套件管理員中。 如果未指定，則會改用套件識別碼。

### <a name="authors"></a>作者

以分號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些名稱會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。

### <a name="packagedescription"></a>PackageDescription

UI 顯示中的套件詳細描述。

### <a name="description"></a>描述

組件的完整描述。 如果未指定 `PackageDescription`，則此屬性也會用來作為套件的描述。

### <a name="copyright"></a>Copyright

套件的著作權詳細資料。

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

布林值，指定在安裝套件時，用戶端是否必須提示取用者接受套件授權。 預設為 `false`。

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

[SPDX 授權識別碼](https://spdx.org/licenses/) \(英文\) 或運算式。 例如，`Apache-2.0`。

此處有 [SPDX 授權識別碼](https://spdx.org/licenses/)的完整清單。 在使用授權類型運算式時，NuGet.org 只接受 OSI 或 FSF 核准的授權。

授權運算式的確切語法使用 [ABNF](https://tools.ietf.org/html/rfc5234)，如下所述。

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> 一次只能指定 `PackageLicenseExpression`、`PackageLicenseFile` 和 `PackageLicenseUrl` 其中之一。

### <a name="packagelicensefile"></a>PackageLicenseFile

若您使用未獲指派 SPDX 識別碼的授權，或其為自訂授權，則這會是套件內授權檔案的路徑 (否則，會優先使用 `PackageLicenseExpression`)

這會取代 `PackageLicenseUrl`，不能與 `PackageLicenseExpression` 合併，並需要 Visual Studio 15.9.4、.NET SDK 2.1.502 或 2.2.101 或更新版本。

您必須明確地將授權檔案新增到專案，以確保其封裝妥當，使用範例：

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

適用於套件的授權 URL。 (_自 Visual Studio 15.9.4、.NET SDK 2.1.502 及 2.2.101 起淘汰_)

### <a name="packageiconurl"></a>PackageIconUrl

具有透明背景之 64x64 映像的 URL，該映像會用作套件在 UI 顯示中的圖示。

### <a name="packagereleasenotes"></a>PackageReleaseNotes

套件的版本資訊。

### <a name="packagetags"></a>PackageTags

以分號分隔的標記清單，用以指定套件。

### <a name="packageoutputpath"></a>PackageOutputPath

決定要置放所封裝之套件的輸出路徑。 預設為 `$(OutputPath)`。

### <a name="includesymbols"></a>IncludeSymbols
此布林值會指出在封裝專案時，套件是否應該建立額外的符號套件。 符號套件的格式由 `SymbolPackageFormat` 屬性控制。

### <a name="symbolpackageformat"></a>SymbolPackageFormat
指定符號套件的格式。 如果是 "symbols.nupkg"，將使用包含 PDB、DLL 和其他輸出檔案的 *.symbols.nupkg* 副檔名建立舊版符號套件。 如果是 "snupkg"，將建立一個包含可攜式 PDB 的 snupkg 符號套件。 預設值為 "symbols.nupkg"。

### <a name="includesource"></a>IncludeSource

此布林值會指出封裝處理序是否應該建立來源套件。 來源套件包含程式庫的原始程式碼及 PDB 檔案。 原始程式檔會放在所產生之套件檔案中的 `src/ProjectName` 目錄底下。

### <a name="istool"></a>IsTool

指定是否要將所有輸出檔複製到 *tools* 資料夾，而不是 *lib* 資料夾。 請注意，這與 `DotNetCliTool` 不同，該項目是藉由在 *.csproj* 檔案中設定 `PackageType` 所指定。

### <a name="repositoryurl"></a>RepositoryUrl

指定存放庫的 URL，此存放庫是套件原始程式碼的所在位置及 (或) 正在建置的來源位置。

### <a name="repositorytype"></a>RepositoryType

指定存放庫的類型。 預設值為 "git"。

### <a name="repositorybranch"></a>RepositoryBranch
指定存放庫中來源分支的名稱。 當專案封裝在 NuGet 套件中時，會將它新增至套件中繼資料。

### <a name="repositorycommit"></a>RepositoryCommit
選擇性存放庫認可或變更集，用來指出要建立封裝的來源。 您也必須指定 `RepositoryUrl`，才能包含這個屬性。 當專案封裝在 NuGet 套件中時，此認可或變更集會新增至套件中繼資料。

### <a name="nopackageanalysis"></a>NoPackageAnalysis

指定封裝不應該在建置套件之後執行套件分析。

### <a name="minclientversion"></a>MinClientVersion

指定可安裝此套件的最低 NuGet 用戶端版本，此作業是由 nuget.exe 和 Visual Studio 套件管理員強制執行。

### <a name="includebuildoutput"></a>IncludeBuildOutput

此布林值會指定是否應該將建置輸出組建封裝成 *.nupkg* 檔案。

### <a name="includecontentinpack"></a>IncludeContentInPack

此布林值會指定是否有任何類型為 `Content` 的項目會自動包含於所產生的套件中。 預設為 `true`。

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

指定要放置輸出組件的資料夾。 輸出組件 (及其他輸出檔) 會複製到其相關的架構資料夾中。

### <a name="contenttargetfolders"></a>ContentTargetFolders

如果未指定 `PackagePath`，此屬性會指定所有內容檔案應移至的預設位置。 預設值為 "content;contentFiles"。

### <a name="nuspecfile"></a>NuspecFile

正用於封裝之 *.nuspec* 檔案的相對或絕對路徑。

> [!NOTE]
> 如果指定 *.nuspec* 檔案，則會**單獨**使用此檔案來封裝資訊，而不會使用專案中的任何資訊。

### <a name="nuspecbasepath"></a>NuspecBasePath

*.nuspec* 檔案的基底路徑。

### <a name="nuspecproperties"></a>NuspecProperties

以分號分隔的索引鍵=值組清單。

## <a name="assemblyinfo-properties"></a>AssemblyInfo 屬性

[組件屬性](../../standard/assembly/set-attributes.md)，通常存在於 AssemblyInfo 檔案，現在會自動從屬性產生。

### <a name="properties-per-attribute"></a>每個屬性 (Attribute) 的屬性 (Property)

每個屬性 (Attribute) 有一個屬性 (Property)，控制其內容，另一個則是停用其產生，如下表所示：

| 屬性                                                      | 屬性               | 要停用的屬性                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

附註：

* `AssemblyVersion` 和 `FileVersion` 預設為採用沒有後置詞的 `$(Version)` 值。 例如，如果 `$(Version)` 是 `1.2.3-beta.4`，則此值會是 `1.2.3`。
* `InformationalVersion` 預設為 `$(Version)` 的值。
* 如果有屬性，則 `InformationalVersion` 會附加 `$(SourceRevisionId)`。 可以使用 `IncludeSourceRevisionInInformationalVersion` 來加以停用。
* 也會針對 NuGet 中繼資料使用 `Copyright` 和 `Description` 屬性。
* `Configuration` 與所有建置程序共用，並且是透過 `dotnet` 命令的 `--configuration` 參數來設定。

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

布林值，啟用或停用所有 AssemblyInfo 產生。 預設值為 `true`。

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

產生組件資訊檔案的路徑。 預設為 `$(IntermediateOutputPath)` (obj) 目錄中的檔案。
