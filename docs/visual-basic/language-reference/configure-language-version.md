---
title: 選取 Visual Basic 語言版本
description: 設定編譯器執行特定編譯器版本搭配使用的語法驗證。
ms.date: 05/24/2018
ms.openlocfilehash: 3b6d8055dbf64f2a5c38f46b6d66794fc48a1cea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415100"
---
# <a name="select-the-visual-basic-language-version"></a>選取 Visual Basic 語言版本

Visual Basic 編譯器會預設為最新的主要版本已發行的語言。 您可以選擇使用語言的新點發行來編譯任何專案。 選擇語言的較新版本可讓您的專案利用最新的語言功能。 在其他情況下，使用較舊版本的語言時，您可能需要驗證專案全新地進行編譯。

此功能可讓在您開發環境中決定安裝新版本的 SDK 和工具，與在專案中決定納入新語言功能這兩件事分開。 您可以在組建電腦上安裝最新的 SDK 和工具。 每個專案可以設定為針對其組建使用特定版本的語言。

有三種方式可設定的語言版本：

- 手動編輯您[ **.vbproj**檔案](#edit-the-vbproj-file)
- 設定語言版本[子目錄中的多個專案](#configure-multiple-projects)
- 設定[`-langversion`編譯器選項](#set-the-langversion-compiler-option)

## <a name="edit-the-vbproj-file"></a>編輯 vbproj 檔案

您可以設定的語言版本，您 **.vbproj**檔案。 新增下列項目：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

值`latest`使用 Visual Basic 語言的最新次要版本。 有效值為：

|值|意義|
|------------|-------------|
|default|編譯器會接受它可支援之最新主要版本的所有有效語言語法。|
|9|編譯器會接受包含在 Visual Basic 9.0 或較低的語法。|
|10|編譯器會接受包含在 Visual Basic 10.0 或更低的語法。|
|11|編譯器會接受包含在 Visual Basic 11.0 或更低的語法。|
|12|編譯器會接受包含在 Visual Basic 12.0 或較低的語法。|
|14|編譯器會接受包含在 Visual Basic 14.0 或較低的語法。|
|15|編譯器會接受包含在 Visual Basic 15.0 或更低的語法。|
|15.3|編譯器會接受包含在 Visual Basic 15.3 或更低的語法。|
|15.5|編譯器會接受包含在 Visual Basic 15.5 或較低的語法。|
|latest|編譯器會接受它可支援的所有有效語言語法。|

特殊字串 `default` 和 `latest` 會分別解析成安裝在組建電腦上的最新主要和次要語言版本。

## <a name="configure-multiple-projects"></a>設定多個專案

您可以建立 **Directory.build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。 您通常會在解決方案目錄中進行。 將下列內容新增到解決方案目錄中的 **Directory.build.props** 檔案：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

現在，每個子目錄包含該檔案的目錄中的組建將會使用 Visual Basic 15.5 版語法。 如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。

## <a name="set-the-langversion-compiler-option"></a>設定 langversion 編譯器選項

您可以使用 `-langversion` 命令列選項。 如需詳細資訊，請參閱 [-langversion](../reference/command-line-compiler/langversion.md) 編譯器選項的文章。 您可以看到一份有效的值輸入`vbc -langversion:?`。
