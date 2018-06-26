---
title: 選取 C# 語言版本 - C# 指南
description: 設定編譯器以特定的編譯器版本執行語法驗證
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207910"
---
# <a name="select-the-c-language-version"></a>選取 C# 語言版本

C# 編譯器會預設為已發行的語言最新主要版本。 您可以選擇使用語言的新點發行來編譯任何專案。 選擇語言的較新版本可讓您的專案利用最新的語言功能。 在其他情況下，使用較舊版本的語言時，您可能需要驗證專案全新地進行編譯。

此功能可讓在您開發環境中決定安裝新版本的 SDK 和工具，與在專案中決定納入新語言功能這兩件事分開。 您可以在組建電腦上安裝最新的 SDK 和工具。 每個專案可以設定為針對其組建使用特定版本的語言。

有數種方法可以設定語言版本：

- 依賴 [Visual Studio 快速動作](#visual-studio-quick-action)。
- 在 [Visual Studio UI](#set-the-language-version-in-visual-studio) 中設定語言版本。
- 手動編輯您的 [**.csproj** 檔案](#edit-the-csproj-file)。
- 針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。
- 設定 [`-langversion`編譯器選項](#set-the-langversion-compiler-option)。

## <a name="visual-studio-quick-action"></a>Visual Studio 快速動作

Visual Studio 可協助您判斷您需要的語言版本。 如果您使用不適用於目前設定版本的語言功能，Visual Studio 會顯示可能的修正，以更新專案的語言版本。

## <a name="set-the-language-version-in-visual-studio"></a>在 Visual Studio 中設定語言版本

您可以在 Visual Studio 中設定版本。 以滑鼠右鍵按一下 [方案總管] 的專案節點，然後選取 [屬性]。 選取 [建置] 索引標籤並選取 [進階] 按鈕。 在下拉式清單中選取版本。 下圖顯示「最新」設定︰

![進階組建設定的螢幕擷取畫面，您可以在其中指定語言版本](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> 如果您使用 Visual Studio IDE 來更新 csproj 檔，IDE 會為每個組建組態建立個別的節點。 您一般會在所有組建組態中設定相同的值，但您需要針對每個組建組態明確設定，或在修改此設定時選取 [所有組態]。 您會在 csproj 檔案中看到下列內容：
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>編輯 csproj 檔案

您可以在 **.csproj** 檔案中設定語言版本。 如下所示新增元素：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

`latest` 值使用 C# 語言的最新次要版本。 有效值為：

|值|意義|
|------------|-------------|
|default|編譯器會接受它可支援之最新主要版本的所有有效語言語法。|
|ISO-1|編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中所含的語法 |
|ISO-2|編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) 中所含的語法 |
|3|編譯器只會接受 C# 3.0 或更低版本中所含的語法。|
|4|編譯器只會接受 C# 4.0 或更低版本中所含的語法。|
|5|編譯器只會接受 C# 5.0 或更低版本中所含的語法。|
|6|編譯器只會接受 C# 6.0 或更低版本中所含的語法。|
|7|編譯器只會接受 C# 7.0 或更低版本中所含的語法。|
|7.1|編譯器只會接受 C# 7.1 或更低版本中所含的語法。|
|7.2|編譯器只會接受 C# 7.2 或更低版本中所含的語法。|
|7.3|編譯器只會接受 C# 7.3 或更低版本中所含的語法。|
|latest|編譯器會接受它可支援的所有有效語言語法。|

特殊字串 `default` 和 `latest` 會分別解析成安裝在組建電腦上的最新主要 (C# 7.0) 和次要 (C# 7.3) 語言版本。

## <a name="configure-multiple-projects"></a>設定多個專案

您可以建立 **Directory.build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。 您通常會在解決方案目錄中進行。 將下列內容新增到解決方案目錄中的 **Directory.build.props** 檔案：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

現在，包含該檔案之目錄的每個子目錄中的組建將會使用 C# 版本 7.3 語法。 如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。

## <a name="set-the-langversion-compiler-option"></a>設定 langversion 編譯器選項

您可以使用 `-langversion` 命令列選項。 如需詳細資訊，請參閱 [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) 編譯器選項的文章。 您可以藉由輸入 `csc -langversion:?`，看到有效值的清單。
