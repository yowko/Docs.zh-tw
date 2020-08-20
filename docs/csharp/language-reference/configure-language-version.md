---
title: C# 語言版本控制 - C# 指南
description: '瞭解如何根據您的專案以及該選項背後的原因來決定 c # 語言版本。 瞭解如何手動覆寫預設值。'
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: a27f3210f399f1bed190c18d778cf3824772d576
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656846"
---
# <a name="c-language-versioning"></a>C# 語言版本控制

最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。 Visual Studio 不會提供 UI 來變更值，但您可以編輯 *.csproj* 檔案來變更該值。 選擇預設值可確保您使用與目標 framework 相容的最新語言版本。 您可以從與專案目標相容的最新語言功能存取中獲益。 此預設選項也可確保您不會使用需要類型或執行時間行為的語言，而無法在您的目標 framework 中使用。 選擇比預設版本新的語言版本，可能會導致難以診斷編譯時期和執行階段錯誤。

本文中的規則適用于使用 Visual Studio 2019 或 .NET Core 3.0 SDK 提供的編譯器。 屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。

只有 .NET Core 3.x 和更新版本才支援 c # 8.0 (和更高版本的) 。 許多最新功能都需要 .NET Core 3.x 所引進的程式庫和執行時間功能：

- [預設介面執行](../whats-new/csharp-8.md#default-interface-methods) 需要 .net CORE 3.0 CLR 中的新功能。
- [非同步資料流程](../whats-new/csharp-8.md#asynchronous-streams) 需要新的類型 <xref:System.IAsyncDisposable?displayProperty=nameWithType> 、 <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> 。
- [索引和範圍](../whats-new/csharp-8.md#indices-and-ranges) 需要新的類型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType> 。
- [可為 null 的參考型別](../whats-new/csharp-8.md#nullable-reference-types) 會使用數個 [屬性](attributes/nullable-analysis.md) ，以提供更好的警告。 這些屬性已在 .NET Core 3.0 中新增。 其他目標 framework 尚未以上述任何屬性標注。 這表示可為 null 的警告可能無法精確反映潛在問題。

## <a name="defaults"></a>Defaults

編譯器會根據下列規則決定預設值：

| 目標架構 | version | C# 語言版本預設值 |
|------------------|---------|-----------------------------|
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 1.x     | C# 7.3                      |
| .NET Framework   | all     | C# 7.3                      |

當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。 您可以在任何環境中使用該預覽版的最新功能，而不會影響以發行之 .NET Core 版本為目標的專案。

## <a name="override-a-default"></a>覆寫預設

如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：

- 手動編輯您的[專案檔](#edit-the-project-file)。
- 針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。
- 設定[ `-langversion` 編譯器選項](compiler-options/langversion-compiler-option.md)。

### <a name="edit-the-project-file"></a>編輯專案檔

您可以在專案檔中設定語言版本。 例如，如果您明確希望存取預覽功能，您可以新增如下元素：

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。

### <a name="configure-multiple-projects"></a>設定多個專案

若要設定多個專案，您可以建立包含元素的 **.props**檔案。 `<LangVersion>` 您通常會在解決方案目錄中進行。 將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

在包含該檔案之目錄的所有子目錄中建立的組建都會使用 preview c # 版本。 如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。

## <a name="c-language-version-reference"></a>C# 語言版本參考

下表顯示所有目前的 C# 語言版本。 如果您的編譯器較舊，您的編譯器可能不一定會瞭解每一個值。 如果您安裝的是 .NET Core 3.0 或更新版本，則可以存取所列的所有專案。

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> 開啟 [Visual Studio 的開發人員命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)，然後執行下列命令，以查看您電腦上可用的語言版本清單。
>
> ```CMD
> csc -langversion:?
> ```
>
> 質疑這類 [langversion](compiler-options/langversion-compiler-option.md) 編譯選項，將會列印如下所示的內容：
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
