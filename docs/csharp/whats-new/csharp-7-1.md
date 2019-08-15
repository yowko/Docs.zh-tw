---
title: C# 7.1 中的新增功能
description: C# 7.1 新功能的概觀。
ms.date: 04/09/2019
ms.openlocfilehash: a95111b6f217a2ca5c520c2d4d70efa0e23742f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347608"
---
# <a name="whats-new-in-c-71"></a>C# 7.1 中的新增功能

C# 7.1 是 C# 語言的第一個發行的小數點版本。 這表示這個語言的版本發行速度將會越來越快。 您很快能使用下列新功能。理想情況下，這些新功能只要一就緒，您就能開始使用。 C# 7.1 加入了新功能，可將編譯器加以設定，使其符合指定的語言版本。 這使得工具的升級與語言版本的升級能夠分開來決定。

C# 7.1 也新增了[語言版本選擇](../language-reference/configure-language-version.md)設定元素、三種新的語言功能和新的編譯器行為。

此版本的新款語言功能包括：

* [`async``Main`方法](#async-main)
  - 應用程式的進入點允許使用`async`修飾詞。
* [`default`常值運算式](#default-literal-expressions)
  - 目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。
* [推斷的元組項目名稱](#inferred-tuple-element-names)
  - 在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。
* [泛型型別參數的模式比對](#pattern-matching-on-generic-type-parameters)
  - 您可以對型別為泛型型別參數的變數使用模式比對運算式。

最後，編譯器有兩個選項 `-refout` 和 `-refonly`，它們控制了[參考組件產生](#reference-assembly-generation)。

若要使用小數點版本中的最新功能，您需要[設定編譯器語言版本](../language-reference/configure-language-version.md)並選取該版本。

此文章的其餘部分將概述各個功能。 您將了解每項功能背後的原因。 您將了解語法。 您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：

1. 安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。
1. 複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。
1. 將目前目錄設為 *try-samples* 存放庫的 *csharp7* 子目錄。
1. 執行 `dotnet try`。

## <a name="async-main"></a>非同步主要

「非同步主要」  方法可讓您在 `Main` 方法中使用 `await`。
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

您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)文章中閱讀更多詳細資料。

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

您可以在關於[預設值運算式](../programming-guide/statements-expressions-operators/default-value-expressions.md)的 C# 程式設計指南文章中進一步了解這項增強功能。

這項增強功能也會變更 [default 關鍵字](../language-reference/keywords/default.md)的部分剖析規則。

## <a name="inferred-tuple-element-names"></a>推斷的 Tuple 元素名稱

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

您可以在[元組](../tuples.md)文章中深入了解此功能。

## <a name="pattern-matching-on-generic-type-parameters"></a>泛型型別參數的模式比對

從 C# 7.1 開始，`is` 和 `switch` 型別模式的模式運算式可能會有泛型型別參數的型別。 在檢查可能是 `struct` 或 `class` 型別的型別，以及您想要避免 boxing 時，這可能非常有用。

## <a name="reference-assembly-generation"></a>參考組件產生

有兩個新編譯器選項會產生「僅參考的組件」  ：[-refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [-refonly](../language-reference/compiler-options/refonly-compiler-option.md)。
連結的文章將更詳細地說明這些選項和參考組件。
