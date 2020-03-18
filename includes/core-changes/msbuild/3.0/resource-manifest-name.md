---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967831"
---
### <a name="resource-manifest-file-names"></a>資源清單檔案名

從 .NET Core 3.0 開始，生成的資源清單檔案名已更改。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 之前，當在 MSBuild 專案檔案中為資源 *（.resx*） 檔設置[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile)中繼資料時，生成的清單名稱是*Namespace.classname.resources*。 未設置["依賴"](/visualstudio/msbuild/common-msbuild-project-items#compile)時，生成的清單名稱為*Namespace.classname.folderpath相對問題.文化.資源*。

從 .NET Core 3.0 開始，當 *.resx*檔與同名原始檔案同時位於時，例如，在 Windows 表單應用中，資源清單名稱從原始檔案中第一種類型的全名生成。 例如，如果*Type.cs*與*Type.resx*同地，則生成的清單名稱為*Namespace.classname.resources*。 但是，如果修改 *.resx*檔`EmbeddedResource`的屬性上的任何屬性，則生成的清單檔案名可能不同：

- 如果屬性`LogicalName`上`EmbeddedResource`的屬性已設置，則該值將用作資源清單檔案名。

  範例：

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **生成的資源清單檔案名**：*某些名稱.資源*（無論 *.resx*檔案名或區域性或任何其他中繼資料）。

- 如果未`LogicalName`設置，但`ManifestResourceName``EmbeddedResource`屬性上的屬性已設置，則其值與檔副檔名 *.resources*結合使用，用作資源清單檔案名。

  範例：

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **生成的資源清單檔案名**：*某些名稱.資源*或*SomeName.fr-FR.資源*。

- 如果以前的規則不適用，並且`DependentUpon``EmbeddedResource`元素上的屬性設置為原始檔案，則原始檔案中的第一類的類型名稱將用於資源清單檔案名。 更具體地說，生成的檔案名是*\[Namespace.Classname 。文化]資源*。

  範例：

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **生成的資源清單檔案名** *：Namespace.Classname.資源*或*Namespace.Classname.fr-FR.資源*（`Namespace.Classname`其中是*MyTypes.cs*中第一類的名稱）。

- 如果`EmbeddedResourceUseDependentUponConvention`前面的規則不適用，則是`true`（.NET Core 的預設值），並且有一個原始檔案與具有相同基本檔案名的 *.resx*檔共存，則 *.resx*檔依賴于匹配的原始檔案，並且生成的名稱與上一個規則相同。 這是 .NET Core 專案的"預設設置"規則。
  
  範例：
  
  MyTypes.cs*和* *MyTypes.resx*或*MyTypes.fr-FR.resx*的檔存在於同一資料夾中。
  
  **生成的資源清單檔案名** *：Namespace.Classname.資源*或*Namespace.Classname.fr-FR.資源*（`Namespace.Classname`其中是*MyTypes.cs*中第一類的名稱）。

- 如果上述規則都不適用，則生成的資源清單檔案名為*RootNamespace。\[文化。資源*. 相對路徑是`Link``EmbeddedResource`元素屬性的值（如果設置為）。 否則，相對路徑是`Identity``EmbeddedResource`元素屬性的值。 在 Visual Studio 中，這是從專案根到解決方案資源管理器中檔的路徑。

#### <a name="recommended-action"></a>建議的動作

如果您對生成的清單名稱不滿意，您可以：

- 根據前面描述的命名規則之一修改資源檔中繼資料。

- 設置為`EmbeddedResourceUseDependentUponConvention``false`專案檔案中，以完全退出新約定：

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > 如果`LogicalName`或`ManifestResourceName`屬性存在，則其值仍將用於生成的檔案名。

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A
