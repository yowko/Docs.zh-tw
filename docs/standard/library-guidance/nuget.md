---
title: NuGet 和.NET 程式庫
description: 最佳作法建議封裝使用 NuGet 的.NET 程式庫。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: d0ea462a7f52dd9a6b2f14be9ed5770160bf66b1
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374485"
---
# <a name="nuget"></a>NuGet

NuGet 是.NET 生態系統的套件管理員，而且是主要的方式開發人員探索，並取得.NET 開放原始碼程式庫。 [NuGet.org](https://www.nuget.org/)，針對裝載 NuGet 套件，Microsoft 所提供的免費服務是公用的 NuGet 套件的主要主機，但您可以發行至自訂的 NuGet 服務，例如[MyGet](https://www.myget.org/)和[Azure 構件](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>建立 NuGet 套件

NuGet 套件 (`*.nupkg`) 是包含.NET 組件和相關聯的中繼資料的 zip 檔案。

有兩種主要的方式，來建立 NuGet 套件。 更新與建議方式是建立封裝從 SDK 樣式專案 (專案檔，其內容開頭`<Project Sdk="Microsoft.NET.Sdk">`)。 組件和目標會自動加入至封裝和剩餘的中繼資料新增至 MSBuild 檔案，例如封裝名稱和版本號碼。 在以編譯[ `dotnet pack` ](../../core/tools/dotnet-pack.md)命令輸出`*.nupkg`檔案而不是組件。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

建立 NuGet 套件的較舊的方法是使用`*.nuspec`檔案和`nuget.exe`命令列工具。 Nuspec 檔案可讓您全權掌控，但您必須仔細地指定要包含在最終的 NuGet 套件中哪些組件和目標。 很容易發生錯誤或其他人進行變更時更新 nuspec 忘了。 Nuspec 的優點是您可以使用它建立 NuGet 套件不支援的 SDK 樣式專案檔案的架構。

**請考慮 ✔️**建立 NuGet 套件使用 SDK 樣式專案檔。

**請考慮 ✔️**設定 SourceLink 將原始檔控制中繼資料新增至您的組件和 NuGet 套件。

## <a name="package-dependencies"></a>封裝相依性

NuGet 套件相依性會詳細說明[相依性](./dependencies.md)文章。

## <a name="important-nuget-package-metadata"></a>重要的 NuGet 套件中繼資料

NuGet 套件支援許多[中繼資料屬性](/nuget/reference/nuspec)。 下表包含每個開放原始碼專案應該提供的核心中繼資料：

| MSBuild 屬性名稱              | Nuspec 名稱              | 描述  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | 封裝識別碼。 可以保留與識別項的前置詞，符合時才[準則](/nuget/reference/id-prefix-reservation)。 |
| `PackageVersion`                   | `version`                  | NuGet 封裝版本。 如需詳細資訊，請參閱 < [NuGet 套件版本](./versioning.md#nuget-package-version)。             |
| `Title`                            | `title`                    | 封裝的易記標題。 它會預設為`PackageId`。             |
| `Description`                      | `description`              | UI 中顯示套件詳細描述。             |
| `Authors`                          | `authors`                  | 套件作者，比對與 nuget.org 上的設定檔名稱的逗號分隔清單。             |
| `PackageTags`                      | `tags`                     | 以空格分隔的標記和描述套件的關鍵字清單。 搜尋套件時，會使用標記。             |
| `PackageIconUrl`                   | `iconUrl`                  | 做為封裝圖示影像 URL。 URL 應為 HTTPS 和映像應該是 64 x 64，而且有透明背景。             |
| `PackageProjectUrl`                | `projectUrl`               | 專案首頁或來源存放庫 URL。             |
| `PackageLicenseUrl`                | `licenseUrl`               | 專案的授權 URL。 可以是 URL`LICENSE`原始檔控制中的檔案。             |

**請考慮 ✔️**選擇 NuGet 套件名稱以符合 NuGet 的前置詞保留的前置詞[準則](/nuget/reference/id-prefix-reservation)。

**請考慮 ✔️**使用`LICENSE`做為原始檔控制中的檔案`LicenseUrl`。 例如， [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md)。

> [!IMPORTANT]
> 專案沒有授權的預設值為[獨佔 copyright](https://choosealicense.com/no-permission/)，導致其他人使用。

**請勿 ✔️**使用 HTTPS href 套件圖示。

> NuGet.org 這類的站台都執行以啟用 HTTPS，並顯示非 HTTPS 映像將會建立混合內容警告。

**請勿 ✔️**使用封裝圖示映像，且會 64 x 64 個獲得最佳的結果是透明的背景。

## <a name="pre-release-packages"></a>發行前套件

NuGet 套件版本尾碼會被視為[發行前版本](/nuget/create-packages/prerelease-packages)。 根據預設，NuGet 套件管理員 UI 會顯示穩定版本，除非使用者選擇單元來發行前套件，讓發行前版本套件適用於有限的使用者測試。

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> 穩定的套件無法取決於發行前版本套件中。 您必須讓您自己的套件發行前版本或較舊的穩定版本而定。

![NuGet 發行前版本套件相依性](./media/nuget/nuget-prerelease-package.png "NuGet 發行前版本套件相依性")

**請勿 ✔️**發行的發行前版本套件時測試、 預覽或實驗。

**請勿 ✔️**發佈為穩定套件，其已準備好讓其他的穩定套件可以參考它時。

## <a name="symbol-packages"></a>符號套件

NuGet 支援[產生不同的符號套件](/nuget/create-packages/symbol-packages)包含偵錯以及包含.NET 組件的主要封裝的 PDB 檔案。 它們裝載在符號伺服器和，才會隨 Visual Studio 等工具下載符號套件的概念。

目前的主要公用主機符號- [SymbolSource](http://www.symbolsource.org/) -不支援建立可攜式 Pdb 的 SDK 樣式專案和符號套件不適用。

**請考慮 ✔️**將 Pdb 內嵌於主要的 NuGet 套件。

**請避免 ❌**建立包含 Pdb 符號套件。

>[!div class="step-by-step"]
[上一頁](./strong-naming.md)
[下一頁](./dependencies.md)
