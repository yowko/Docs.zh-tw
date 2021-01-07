---
title: MSBuild 如何產生資訊清單檔案名
description: 描述影響 MSBuild 在編譯時期產生的資源資訊清單檔案名之因素。
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 2e0461e34bbd7f8da35bea1db1913a32915c7117
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970677"
---
# <a name="how-resource-manifest-files-are-named"></a>資源資訊清單檔案的命名方式

當 MSBuild 編譯 .NET Core 專案時，具有 *.resx* 副檔名的 XML 資源檔會轉換成二進位 *.resources* 檔案。 二進位檔案內嵌在編譯器的輸出中，而且可以由讀取 <xref:System.Resources.ResourceManager> 。 本文描述 MSBuild 如何為每個 *.resources* 檔案選擇名稱。

> [!TIP]
> 如果您明確地將資源專案加入至專案檔，且它也 [隨附于 .Net Core 的預設包含 glob](../project-sdk/overview.md#default-includes-and-excludes)，您將會收到組建錯誤。 若要手動將資源檔加入為 `EmbeddedResource` 專案，請將 `EnableDefaultEmbeddedResourceItems` 屬性設定為 false。

## <a name="default-name"></a>預設名稱

在 .NET Core 3.0 和更新版本中，當符合下列兩個條件時，就會使用資源資訊清單的預設名稱：

- 資源檔不會明確包含在專案檔中，做為 `EmbeddedResource` 具有 `LogicalName` 、 `ManifestResourceName` 或 `DependentUpon` 中繼資料的專案。
- `EmbeddedResourceUseDependentUponConvention`專案檔中的屬性未設定為 `false` 。 根據預設，這個屬性設定為 `true`。 如需詳細資訊，請參閱 [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention)。

如果資源檔與相同根檔案名 (*.cs* 或 *.vb*) 的原始程式檔共存，則在來源檔案中定義之第一個類型的完整名稱會用於資訊清單檔案名。 例如，如果 `MyNamespace.Form1` 是 *Form1.cs* 中所定義的第一個型別，而 *Form1.cs* 與 *Form1* 共存，則該資源檔產生的資訊清單名稱就是 *MyNamespace。*

## <a name="logicalname-metadata"></a>LogicalName 中繼資料

如果資源檔已明確包含在專案檔中當做 `EmbeddedResource` 具有 `LogicalName` 中繼資料的專案，則 `LogicalName` 會使用此值做為資訊清單名稱。 `LogicalName` 優先于任何其他中繼資料或設定。

例如，在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是 *SomeName。*

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

-或-

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a>ManifestResourceName 中繼資料

如果資源檔已明確包含在專案檔中做為 `EmbeddedResource` `ManifestResourceName` 中繼資料 (且 `LogicalName` 不存在) 中，則 `ManifestResourceName` 會將值與副檔名 *. 資源* 合併使用，作為資訊清單檔案名。

例如，在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是 *SomeName。*

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

下列專案檔程式碼片段中所定義資源檔的資訊清單名稱是 *SomeName.fr-fr。*

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a>DependentUpon 中繼資料

如果資源檔已明確包含在專案檔中做為 `EmbeddedResource` 中繼資料 (的專案，而且 `DependentUpon` `LogicalName` `ManifestResourceName` 沒有) ，則會使用所定義來源檔案中的資訊 `DependentUpon` 做為資源資訊清單檔案名。 具體而言，來源檔案中所定義的第一個型別的名稱會用在資訊清單名稱中，如下所示： *Namespace. Classname \[ 。文化特性]. 資源*。

例如，在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是 *命名空間。 Classname. 資源* (其中 `Namespace.Classname` 是 *MyTypes.cs*) 中所定義的第一個類別。

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

下列專案檔程式碼片段中所定義資源檔的資訊清單名稱是 *Namespace.Classname.fr* ， (其中 `Namespace.Classname` 是 *MyTypes.cs*) 中所定義的第一個類別。

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a>EmbeddedResourceUseDependentUponConvention 屬性

如果在 `EmbeddedResourceUseDependentUponConvention` 專案檔中將設定為 `false` ，則每個資源資訊清單檔案名會以專案的根命名空間和 .resx 檔的專案根目錄中的相對路徑為基礎 *。* 更明確地說，產生的資源資訊清單檔案名為 *RootNamespace. RelativePathWithDotsForSlashes。 \[文化特性。]資源*。 這也是在3.0 之前的 .NET Core 版本中用來產生資訊清單名稱的邏輯。

> [!NOTE]
>
> - 如果未 `RootNamespace` 定義，它會預設為專案名稱。
> - 如果 `LogicalName` 為 `ManifestResourceName` 專案檔 `DependentUpon` 中的專案指定、或中繼資料 `EmbeddedResource` ，則此命名規則不適用於該資源檔。

## <a name="see-also"></a>請參閱

- [資訊清單資源命名的運作方式](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [.NET Core SDK 專案的 MSBuild 屬性](../project-sdk/msbuild-props.md)
- [MSBuild 重大變更](../compatibility/msbuild.md)
