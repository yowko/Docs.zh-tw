---
title: C# 7.1 中的新增功能
description: C# 7.1 新功能的概觀。
ms.date: 08/16/2017
ms.openlocfilehash: 00baec45d7582d3ac12c7b0865241f5cd8159246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-71"></a>C# 7.1 中的新增功能

C# 7.1 是 C# 語言的第一個發行的小數點版本。 這表示這個語言的版本發行速度將會越來越快。 您很快能使用下列新功能。理想情況下，這些新功能只要一就緒，您就能開始使用。
 C# 7.1 加入了新功能，可將編譯器加以設定，使其符合指定的語言版本。
 這使得工具的升級與語言版本的升級能夠分開來決定。


C# 7.1 也新增了[語言版本選擇](#language-version-selection)組態項目、三種新的語言功能和新的編譯器行為。

此版本的新款語言功能包括：

* [`async``Main`方法](#async-main)
  - 應用程式的進入點允許使用`async`修飾詞。
* [`default`常值運算式](#default-literal-expressions)
  - 目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。
* [推斷的元組項目名稱](#inferred-tuple-element-names)
  - 在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。


最後，編譯器有兩個選項 `/refout` 和 `/refonly`，它們控制了[參考組件產生](#reference-assembly-generation)。

## <a name="language-version-selection"></a>版本選取項目

C# 編譯器自 Visual Studio 2017 15.3 與 .NET Core SDK 2.0 起開始支援 C# 7.1。 不過，7.1 的功能預設為關閉。 若要啟用 7.1 功能，您需要變更專案的語言版本設定。

在 [方案總管]的專案節點上按一下滑鼠右鍵，並選取 [屬性]。 選取 [建置] 索引標籤並選取 [進階] 按鈕。 在下拉式清單中選取 [C# 最新的次要版本 (最新版)]，或特定版本 [C# 7.1]，如下圖所示。 `latest` 值表示您想要使用目前電腦上的最新次要版本。 `C# 7.1` 表示您想要使用 C# 7.1，即使是已有較新的次要版本發行。

![設定語言版本](./media/csharp-7-1/advanced-build-settings.png)

或者，您可以編輯 "csproj" 檔案，並新增或修改下列行：

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> 如果您使用 Visual Studio IDE 來更新 csproj 檔，IDE 會為每個組建組態建立個別的節點。 您一般會在所有組建組態中設定相同的值，但您需要針對每個組建組態明確設定，或在修改此設定時選取 [所有組態]。 您會在 csproj 檔案中看到下列內容：

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

`LangVersion` 項目的有效設定為：

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

特殊字串 `default` 和 `latest` 會分別解析成安裝在組建電腦上的最新主要和次要語言版本。

此設定能讓在您開發環境中安裝新版本的 SDK 和工具與在專案中選擇納入新語言功能這兩件事分開。 您可以在組建電腦上安裝最新的 SDK 和工具。 每個專案可以設定為針對其組建使用特定版本的語言。

## <a name="async-main"></a>非同步主要

「非同步主要」方法可讓您在 `Main` 方法中使用 `await`。
在過去您必須這樣寫：

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

現在您可以這樣寫：

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

如果您的程式不會傳回結束代碼，您可以宣告傳回 <xref:System.Threading.Tasks.Task> 的 `Main` 方法：

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)主題中閱讀更多詳細資料。

## <a name="default-literal-expressions"></a>預設常值運算式

預設常值運算式是預設值運算式的增強功能。
這些運算式會將變數初始化為預設值。 在過去您必須這樣寫：

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

您現在可以略過初始化右側的類型：

```csharp
Func<string, bool> whereClause = default;
```

您可以在關於[預設值運算式](../programming-guide/statements-expressions-operators/default-value-expressions.md)的 C# 程式設計手冊主題進一步了解這項增強功能。

這項增強功能也會變更 [default 關鍵字](../language-reference/keywords/default.md)的部分剖析規則。

## <a name="inferred-tuple-element-names"></a>Tuple 型別推導

本方法為 C# 7.0 版本 Tuple 方法的改進， 許多時候，當您初始化 Tuple 時，用於指派右側的變數會與您想要的元組項目名稱相同：

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

元組項目的名稱可以從用來在 C# 7.1 中初始化元組的變數加以推斷：

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

您可以在[元組](../tuples.md)主題中深入了解此功能。

## <a name="reference-assembly-generation"></a>參考組件產生

有兩個新的編譯器選項會產生「僅參考的組件」：[/refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [/refonly](../language-reference/compiler-options/refonly-compiler-option.md)。
連結的主題將更詳細地說明這些選項和參考組件。
