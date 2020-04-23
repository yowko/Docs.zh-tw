---
title: C# 語言版本控制 - C# 指南
description: 瞭解如何根據項目確定 C# 語言版本以及該選擇背後的原因。 瞭解如何手動覆蓋預設值。
ms.date: 02/21/2020
ms.openlocfilehash: 850c4a860878593d80aaa3b7b38efaff9e003f43
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102654"
---
# <a name="c-language-versioning"></a>C# 語言版本控制

最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。 Visual Studio 不提供更改值的 UI,但您可以通過編輯*csproj*檔來更改該值。 選擇預設值可確保使用與目標框架相容的最新語言版本。 您可以造訪與項目目標相容的最新語言功能。 此預設選擇還可確保不使用需要目標框架中不可用的類型或運行時行為的語言。 選擇比預設值更新的語言版本可能會導致難以診斷編譯時間和運行時錯誤。

本文中的規則適用於使用 Visual Studio 2019 或 .NET Core 3.0 SDK 提供的編譯器。 屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。

C# 8.0(更高版本)僅在 .NET Core 3.x 和較新版本上受支援。 許多最新的功能需要 .NET Core 3.x 中引入的庫和運行時功能:

- 默認介面成員實現需要 .NET Core 3.0 CLR 中的新功能。
- 非同步需要新類型<xref:System.IAsyncDisposable?displayProperty=nameWithType>,<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType><xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>與 。
- 索引和範圍需要新類型<xref:System.Index?displayProperty=nameWithType>和<xref:System.Range?displayProperty=nameWithType>。
- 空引用類型使用多個[屬性](attributes/nullable-analysis.md)來提供更好的警告。 這些屬性在 .NET Core 3.0 中添加。 其他目標框架尚未使用任何這些屬性進行批文。 這意味著無效警告可能無法準確反映潛在問題。

## <a name="defaults"></a>Defaults

編譯器會根據下列規則決定預設值：

|目標架構|version|C# 語言版本預設值|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。 您可以在任何環境中將最新的功能與預覽一起使用,而不會影響針對已發佈的 .NET Core 版本的專案。

## <a name="override-a-default"></a>覆寫預設

如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：

- 手動編輯您的[專案檔](#edit-the-project-file)。
- 針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。
- 設定[`-langversion`編譯器選項](compiler-options/langversion-compiler-option.md)。

### <a name="edit-the-project-file"></a>編輯專案檔

您可以在專案檔中設定語言版本。 例如，如果您明確希望存取預覽功能，您可以新增如下元素：

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。

### <a name="configure-multiple-projects"></a>設定多個專案

要設定多個專案,您可以創建包含該元素的`<LangVersion>` **Directory.Build.props**檔。 您通常會在解決方案目錄中進行。 將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

包含該檔的目錄的所有子目錄中的生成將使用預覽 C# 版本。 如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。

## <a name="c-language-version-reference"></a>C# 語言版本參考

下表顯示所有目前的 C# 語言版本。 如果編譯器較舊,則不一定瞭解每個值。 如果安裝 .NET Core 3.0 或更高版本,則可以訪問列出的所有內容。

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
|ISO-2|編譯器僅接受 ISO/IEC 23270:2006 C# (2.0) 中包含的語法。 |
|ISO-1|編譯器僅接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中包含的語法。 |
