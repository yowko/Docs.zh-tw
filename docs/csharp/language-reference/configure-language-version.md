---
title: C# 語言版本控制 - C# 指南
description: 了解如何根據您的專案決定 C# 語言版本，以及您可以手動調整的不同值。
ms.date: 07/10/2019
ms.openlocfilehash: 3c1035d983660ea0a945e4d4b7b72c69736c90cb
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980128"
---
# <a name="c-language-versioning"></a>C# 語言版本控制

最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。 這是因為 C# 語言可能具有依賴於型別或執行階段元件的功能，而並非每個 .NET 實作都提供。 這也可確保建置專案的任何目標，您可以根據預設獲得最相容的語言版本。

The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK. 屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。 

## <a name="defaults"></a>預設值

編譯器會根據下列規則決定預設值：

|目標 Framework|版本|C# 語言版本預設值|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET 標準|2.1|C# 8.0|
|.NET 標準|2.0|C# 7.3|
|.NET 標準|1.x|C# 7.3|
|.NET Framework|全部|C# 7.3|

## <a name="default-for-previews"></a>預設為預覽

當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。 這能確保可讓您利用最新功能，保證可在任何環境中使用該預覽，而不會影響對已發行之 .NET Core 版本為目標的專案。

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

To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element. 您通常會在解決方案目錄中進行。 將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

現在，包含該檔案之目錄中每個子目錄的組建，將會使用預覽 C# 版本。 如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。

## <a name="c-language-version-reference"></a>C# 語言版本參考

下表顯示所有目前的 C# 語言版本。 如果您的編譯器版本較舊，可能不一定了解每個值。 如果您安裝 .NET Core 3.0，您將能存取所列的所有項目。

|{2&gt;值&lt;2}|意義|
|------------|-------------|
|preview|編譯器會接受最新預覽版本的所有有效語言語法。|
|latest|編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。|
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
|ISO-2|The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0). |
|ISO-1|The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2). |
