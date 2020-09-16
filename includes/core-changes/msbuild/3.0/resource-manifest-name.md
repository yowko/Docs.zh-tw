---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206219"
---
### <a name="resource-manifest-file-name-change"></a>資源資訊清單檔案名變更

從 .NET Core 3.0 開始，在預設情況下，MSBuild 會為資源檔產生不同的資訊清單檔案名。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 之前，如果 `LogicalName` `ManifestResourceName` 為專案檔中的專案指定了 no、或 `DependentUpon` 中繼資料 `EmbeddedResource` ，則 MSBuild 會在模式中產生資訊清單檔案名 `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` 。 如果 `RootNamespace` 專案檔中未定義，它會預設為專案名稱。 例如，根專案*目錄中名為*MyProject 的資源檔所產生的資訊清單名稱是*MyProject.Form1.resources*。

從 .NET Core 3.0 開始，如果資源檔與相同名稱的原始程式檔共存 (*例如，Form1.cs) ，MSBuild*會使用來源檔案*Form1.cs*中的類型資訊，以在模式中產生資訊清單檔案名 `<Namespace>.<ClassName>.resources` 。 命名空間和類別名稱是從共置原始檔中的第一個型別解壓縮而來。 例如，與名為*Form1.cs*的*原始程式檔共存的資源*檔所產生的資訊清單名稱，會是*MyNamespace。* 要注意的重點是，檔案名的第一個部分與舊版的 .NET Core (*MyNamespace* ，而不是 *MyProject*) 。

> [!NOTE]
> 如果您在 `LogicalName` `ManifestResourceName` 專案檔中的 `DependentUpon` 專案上指定、或中繼資料 `EmbeddedResource` ，則這項變更不會影響該資源檔。

這項重大變更是透過將 `EmbeddedResourceUseDependentUponConvention` 屬性新增至 .Net Core 專案所引進。 依預設，不會在 .NET Core 專案檔中明確列出資源檔，因此沒有 `DependentUpon` 中繼資料可指定如何命名產生的 *.resources* 檔案。 當 `EmbeddedResourceUseDependentUponConvention` 設為 `true` （預設值）時，MSBuild 會尋找共置的原始程式檔，並從該檔案中解壓縮命名空間和類別名稱。 如果您將設定 `EmbeddedResourceUseDependentUponConvention` 為 `false` ，MSBuild 會根據先前的行為（結合和相對檔案路徑）來產生資訊清單名稱 `RootNamespace` 。

#### <a name="recommended-action"></a>建議的動作

在大部分的情況下，開發人員不需要採取任何動作，而且您的應用程式應該會繼續運作。 但是，如果此變更中斷您的應用程式，您可以：

- 將您的程式碼變更為預期新的資訊清單名稱。

- 在專案檔中將設定為，以退出宣告新的命名慣例 `EmbeddedResourceUseDependentUponConvention` `false` 。

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A
