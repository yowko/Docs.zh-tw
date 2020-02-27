---
title: C# 語言版本控制 - C# 指南
description: 瞭解如何根據您C#的專案以及該選擇背後的原因來決定語言版本。 瞭解如何手動覆寫預設值。
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626760"
---
# <a name="c-language-versioning"></a>C# 語言版本控制

最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。 Visual Studio 不會提供變更值的 UI，但是您可以藉由編輯 *.csproj*檔案來變更它。 選擇預設值可確保您使用的是與目標 framework 相容的最新語言版本。 您可以從存取與您專案的目標相容的最新語言功能中獲益。 此預設選項也可確保您不會使用需要在目標 framework 中提供之類型或執行時間行為的語言。 選擇比預設值新的語言版本可能會導致難以診斷編譯時期和執行階段錯誤。

C#8.0 （和更新版本）僅在 .NET Core 3.x 和較新版本上受到支援。 許多最新的功能都需要 .NET Core 3.x 中引進的程式庫和執行時間功能：

- 預設介面成員執行需要 .NET Core 3.0 CLR 中的新功能。
- 非同步資料流程需要新的類型 <xref:System.IAsyncDisposable?displayProperty=nameWithType>、<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>。
- 索引和範圍需要新的類型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType>。
- 可為 null 的參考型別利用數個[屬性](../nullable-attributes.md)來提供更好的警告。 這些屬性是在 .NET Core 3.0 中新增的。 其他目標架構尚未使用上述任何屬性來標注。 這表示可為 null 的警告可能無法正確反映潛在的問題。

## <a name="defaults"></a>Defaults

編譯器會根據下列規則決定預設值：

|目標 Framework|version|C# 語言版本預設值|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。 您可在任何環境中使用該預覽的最新功能，而不會影響以發行的 .NET Core 版本為目標的專案。

## <a name="override-a-default"></a>覆寫預設

如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：

- 手動編輯您的[專案檔](#edit-the-project-file)。
- 針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。
- 設定 [`-langversion`編譯器選項](compiler-options/langversion-compiler-option.md)。

### <a name="edit-the-project-file"></a>編輯專案檔

您可以在專案檔中設定語言版本。 例如，如果您明確希望存取預覽功能，您可以新增如下元素：

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。

### <a name="configure-multiple-projects"></a>設定多個專案

若要設定多個專案，您可以建立包含 `<LangVersion>` 元素的 **.props**檔案。 您通常會在解決方案目錄中進行。 將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

包含該檔案之目錄的所有子目錄中的組建都會使用預覽C#版本。 如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。

## <a name="c-language-version-reference"></a>C# 語言版本參考

下表顯示所有目前的 C# 語言版本。 如果您的編譯器較舊，可能不一定要瞭解每個值。 如果您安裝 .NET Core 3.0 或更新版本，則可以存取列出的所有專案。

|值|意義|
|------------|-------------|
|preview|編譯器會接受最新預覽版本的所有有效語言語法。|
|最新|編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。|
|latestMajor|編譯器會接受編譯器最新已發行主要版本的語法。|
|8.0|編譯器只會接受 C# 8.0 或更低版本中所含的語法。|
|7.3|編譯器只會接受 C# 7.3 或更低版本中所含的語法。|
|7.2|編譯器只會接受 C# 7.2 或更低版本中所含的語法。|
|7.1|編譯器只會接受 C# 7.1 或更低版本中所含的語法。|
|7|編譯器只會接受 C# 7.0 或更低版本中所含的語法。|
|6|編譯器只會接受 C# 6.0 或更低版本中所含的語法。|
|5|編譯器只會接受 C# 5.0 或更低版本中所含的語法。|
|4|編譯器只會接受 C# 4.0 或更低版本中所含的語法。|
|3|編譯器只會接受 C# 3.0 或更低版本中所含的語法。|
|ISO-2|編譯器只會接受 ISO/IEC 23270:2006 C# （2.0）中所包含的語法。 |
|ISO-1|編譯器只會接受 ISO/IEC 23270:2003 C# （1.0/1.2）中所包含的語法。 |
