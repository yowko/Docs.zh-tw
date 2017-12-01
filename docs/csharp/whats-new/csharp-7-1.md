---
title: "在 C# 7.1 最新消息"
description: "7.1 C# 中的新功能的概觀。"
keywords: "C# 語言設計，7.1，Visual Studio 2017，"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a>在 C# 7.1 最新消息

C# 7.1 是第一個點版本的 C# 語言。 它會將標示為語言增加的發行日程。 您可以使用的新功能，最好是每個新功能就緒時。 C# 7.1 加入設定以符合指定的版本的語言編譯器的功能。 可讓您分隔在決定要從在決定来升級的語言版本升級工具。

將 C# 7.1[語言版本選擇](#language-version-selection)組態項目、 三個新的語言功能和新編譯器行為。

在此版本中的新語言功能包括：

* [`async``Main`方法](#async-main)
  - 應用程式的進入點可以有`async`修飾詞。
* [`default`常值運算式](#default-literal-expressions)
  - 目標類型可以推斷時，您可以使用預設值運算式中預設常值運算式。
* [推斷的 tuple 項目名稱](#inferred-tuple-element-names)
  - Tuple 元素的名稱來推斷與 tuple 初始化，在許多情況下。

最後，編譯器會有兩個選項`/refout`和`/refonly`該控制項[參考組件產生](#reference-assembly-generation)。

## <a name="language-version-selection"></a>語言版本選取項目

C# 編譯器支援 C# 7.1 開始使用 Visual Studio 2017 版本 15.3 或.NET Core SDK 2.0。 不過，7.1 功能已關閉的預設值。 若要啟用 7.1 功能，您需要變更您的專案的語言版本設定。

在 Visual Studio 中，以滑鼠右鍵按一下方案總管 中的專案節點，然後選取**屬性**。 選取**建置**索引標籤並選取**進階** 按鈕。 在下拉式清單中選取**C# 最新次要版本 （最新版）**，或特定版本**C# 7.1**映像下列所示。 `latest`值表示您想要使用目前電腦上的最新的次要版本。 `C# 7.1`表示您想要使用 C# 7.1，即使有較新的次要版本發行。

![設定的語言版本](./media/csharp-7-1/advanced-build-settings.png)

或者，您可以編輯"csproj 「 檔案和新增或修改下列行：

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> 如果您使用 Visual Studio IDE 來更新 csproj 檔時，IDE 會建立個別的節點，每個組建組態。 您將一般設定中的值相同所有組建組態，但您需要明確設定每個組建組態，或當您修改此設定時，請選取 「 所有的組態 >。 您會看到下列於 csproj 檔案中：

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

有效的設定，如`LangVersion`項目：

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

特殊字串`default`和`latest`解析成最新的主要和次要語言版本分別安裝在組建電腦上。

此設定以減少在您選擇要在專案中的新語言功能的開發環境中安裝新版本的 SDK 和工具。 您可以在組建電腦上安裝最新的 SDK 和工具。 每個專案可以設定為使用其建立的特定版本的語言。

## <a name="async-main"></a>主要的非同步處理

*非同步主要*方法可讓您使用`await`中您`Main`方法。
先前，您需要撰寫：

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

您現在可以撰寫：

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

如果您的程式不會傳回結束代碼，您可以宣告`Main`方法會傳回<xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

閱讀更多詳細資料中的相關[非同步主要](../programming-guide/main-and-command-args/index.md)程式設計指南中的主題。

## <a name="default-literal-expressions"></a>預設常值運算式

預設常值運算式是預設值運算式的增強功能。
這些運算式初始化的變數預設值。 您先前會寫入：

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

您現在可以略過初始化右手邊的類型：

```csharp
Func<string, bool> whereClause = default;
```

您可以進一步了解 C# 程式設計手冊 > 主題中的這項增強功能上[預設值運算式](../programming-guide/statements-expressions-operators/default-value-expressions.md)。

這項增強功能也會變更部分的剖析規則[default 關鍵字](../language-reference/keywords/default.md)。

## <a name="inferred-tuple-element-names"></a>推斷的 tuple 項目名稱

這項功能是在 C# 7.0 中所引進的 tuple 功能小增強功能。 許多次當您初始化 tuple，用於指派的右側的變數是您想要的 tuple 項目名稱相同：

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Tuple 元素的名稱來推斷從用來初始化在 C# 7.1 tuple 的變數：

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

您可以進一步了解這項功能[Tuple](../tuples.md)主題。

## <a name="reference-assembly-generation"></a>產生參考組件

有兩個新的編譯器選項產生*僅參考的組件*: [/refout](../language-reference/compiler-options/refout-compiler-option.md)和[/refonly](../language-reference/compiler-options/refonly-compiler-option.md)。
連結的主題將說明這些選項和更詳細的參考組件。
