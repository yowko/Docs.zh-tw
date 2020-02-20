---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451877"
---
### <a name="resource-manifest-file-names"></a>資源資訊清單檔案名

從 .NET Core 3.0 開始，產生的資源資訊清單檔案名已變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 之前，針對 MSBuild 專案檔中的資源（ *.resx*）檔案設定[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile)中繼資料時，產生的資訊清單名稱是*Namespace. Classname. resources*。 未設定[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile)時，產生的資訊清單名稱為*Namespace. FolderPathRelativeToRoot. Culture. resources*。

從 .NET Core 3.0 開始，當 *.resx*檔案與相同名稱的原始程式檔共存時（例如，在 Windows Forms 應用程式中），會從來源檔案中第一個類型的完整名稱產生資源資訊清單名稱。 例如，如果*Type.cs*與 *.resx*共存，則產生的資訊清單名稱會是*Namespace. Classname. resources*。 不過，如果您修改 *.resx*檔案的 [`EmbeddedResource`] 屬性上的任何屬性，產生的資訊清單檔案名可能會不同：

- 如果已設定 [`EmbeddedResource`] 屬性上的 [`LogicalName`] 屬性，則會使用該值做為資源資訊清單檔案名。

  範例：

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **產生的資源資訊清單檔案名**： *SomeName* （不論 *.resx*檔案名或文化特性或任何其他中繼資料）。

- 如果未設定 `LogicalName`，但 `EmbeddedResource` 屬性上的 `ManifestResourceName` 屬性已設定，則會使用其值（與副檔名 *.resources*結合）做為資源資訊清單檔案名。

  範例：

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **產生的資源資訊清單檔案名**： *SomeName .resources*或*SomeName.fr*。

- 如果先前的規則不適用，而且 `EmbeddedResource` 元素上的 `DependentUpon` 屬性設定為來源檔案，則來源檔案中第一個類別的類型名稱會在資源資訊清單檔案名中使用。 更明確地說，產生的檔案名是*Namespace. Classname\[。Culture] .resources*。

  範例：

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **產生的資源資訊清單檔案名**： *Namespace. Classname. resources*或*Namespace.Classname.fr-fr* （其中 `Namespace.Classname` 是*MyTypes.cs*中第一個類別的名稱）。

- 如果先前的規則不適用，`EmbeddedResourceUseDependentUponConvention` 是 `true` （.NET Core 的預設值），而且有一個與 *.resx*檔案共置的原始程式檔具有相同的基底檔案名，則 *.resx*檔案會相依于相符的原始程式檔，而產生的名稱與上一個規則中的相同。 這是 .NET Core 專案的「預設設定」規則。
  
  範例：
  
  Files *MyTypes.cs*和*MyTypes*或*MyTypes.fr-fr*存在於相同的資料夾中。
  
  **產生的資源資訊清單檔案名**： *Namespace. Classname. resources*或*Namespace.Classname.fr-fr* （其中 `Namespace.Classname` 是*MyTypes.cs*中第一個類別的名稱）。
    
- 如果上述規則都不適用，則產生的資源資訊清單檔案名為*RootNamespace. RelativePathWithDotsForSlashes.\[文化特性。]資源*。 相對路徑是 `EmbeddedResource` 元素的 `Link` 屬性值（如果已設定的話）。 否則，相對路徑就是 `EmbeddedResource` 元素的 `Identity` 屬性值。 在 Visual Studio 中，這是從專案根目錄到方案總管中檔案的路徑。

#### <a name="recommended-action"></a>建議的動作

如果您不滿意所產生的資訊清單名稱，可以：

- 根據先前所述的其中一個命名規則來修改您的資源檔中繼資料。

- 在您的專案檔中，將 `EmbeddedResourceUseDependentUponConvention` 設定為 `false`，以完全退出宣告新的慣例：

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > 如果 `LogicalName` 或 `ManifestResourceName` 屬性存在，其值仍會用於產生的檔案名。

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A
