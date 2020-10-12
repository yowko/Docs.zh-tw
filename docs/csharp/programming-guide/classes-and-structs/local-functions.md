---
title: 區域函式 - C# 程式設計手冊
description: 'C # 中的區域函式是在另一個成員中嵌套的私用方法，可從其包含成員中呼叫。'
ms.date: 10/09/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: a2d389c8b1c687dc4885004fcdc33e0ed7ada977
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955677"
---
# <a name="local-functions-c-programming-guide"></a>區域函式 (C# 程式設計手冊)

從 C# 7.0 開始，C# 支援「區域函式」**。 區域函式是另一個成員中巢狀型別的私用方法。 它們只可以從其包含成員呼叫。 區域函式可以宣告於下列項目中，以及從下列項目呼叫：

- 方法，特別是迭代器方法和非同步方法
- 建構函式
- 屬性存取子
- 事件存取子
- 匿名方法
- Lambda 運算式
- 完成項
- 其他區域函式

不過，區域函式不能宣告於運算式主體成員內。

> [!NOTE]
> 在某些情況下，您可以使用 Lambda 運算式來實作區域函式也支援的功能。 如需比較，請參閱 [區域函數與 lambda 運算式](#local-functions-vs-lambda-expressions)。

區域函式讓程式碼的意圖更為清楚。 讀取您的程式碼的任何人都可以看到，除了包含的方法之外，無法呼叫方法。 對於 Team 專案，它們也可讓另一個開發人員無法從類別或結構的其他位置錯誤地直接呼叫方法。

## <a name="local-function-syntax"></a>區域函式語法

區域函式定義為包含成員內的巢狀方法。 其定義具有下列語法：

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

您可以使用下列修飾詞搭配區域函數：

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- [`static`](../../language-reference/keywords/static.md) C # 8.0 和更新版本中的 () 。 靜態區域函式無法捕捉本機變數或實例狀態。
- [`extern`](../../language-reference/keywords/extern.md) C # 9.0 和更新版本中的 () 。 外部區域函數必須是 `static` 。

在包含成員中定義的所有區域變數（包含其方法參數）都可在非靜態區域函數中存取。

不同于方法定義，區域函式定義不能包含成員存取修飾詞。 因為所有區域函式都是私用，所以包含 `private` 這類關鍵字的存取修飾詞會產生編譯器錯誤 CS0106「修飾詞 'private' 對此項目無效」。

下列範例定義名為 `AppendPathSeparator` 的區域函式，而此區域函式是名為 `GetText` 之方法的私用項目：

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

從 c # 9.0 開始，您可以將屬性套用至區域函數、其參數和型別參數，如下列範例所示：

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

上述範例使用 [特殊屬性](../../language-reference/attributes/nullable-analysis.md) 來協助編譯器在可為 null 的內容中進行靜態分析。

## <a name="local-functions-and-exceptions"></a>區域函式和例外狀況

區域函式的其中一個有用功能是它們可以允許立即顯示例外狀況。 對於方法迭代器，只有在列舉傳回的序列時，才會顯示例外狀況，而不是擷取迭代器時。 對於非同步方法，等候傳回的工作時，會觀察到非同步方法中擲回的任何例外狀況。

下列範例 `OddSequence` 會定義列舉指定範圍中奇數數位的方法。 因為它會將一個大於 100 的數字傳遞至 `OddSequence` 列舉值方法，所以此方法會擲回 <xref:System.ArgumentOutOfRangeException>。 顯示範例輸出時，只有在您逐一查看數字時，才會顯示例外狀況，而不是擷取列舉值時。

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

如果您將 iterator 邏輯放入區域函式中，當您抓取列舉值時，就會擲回引數驗證例外狀況，如下列範例所示：

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

您可以透過與非同步作業類似的方式來使用區域函數。 等候對應的工作時，非同步方法介面中擲回的例外狀況。 區域函式允許您的程式碼快速失敗，並允許擲回並同步觀察到您的例外狀況。

下列範例使用名為 `GetMultipleAsync` 的非同步方法暫停指定的秒數，並傳回該秒數之隨機倍數的值。 延遲上限是 5 秒；如果值大於 5，則會產生 <xref:System.ArgumentOutOfRangeException>。 如下列範例所示，只有在等候工作時，才會觀察到將值6傳遞給方法時所擲回的例外狀況 `GetMultipleAsync` 。

:::code language="csharp" source="snippets/local-functions/AsyncWithoutLocal.cs" :::

如同方法反覆運算器，您可以重構上述範例，並將非同步作業的程式碼放在區域函式中。 如下列範例的輸出所示，當 <xref:System.ArgumentOutOfRangeException> 呼叫方法時，就會擲 `GetMultiple` 回。

:::code language="csharp" source="snippets/local-functions/AsyncWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a>區域函式與 Lambda 運算式的比較

第一眼，區域函式和 [Lambda 運算式](../../language-reference/operators/lambda-expressions.md)十分類似。 在許多情況下，選擇使用 Lambda 運算式或區域函式與樣式和個人喜好設定相關。 不過，您應該注意可使用任一選項的實際差異。

讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。 首先是使用區域函式的版本：

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

針對使用 Lambda 運算式的實作版本進行對比：

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

區域函式具有名稱。 Lambda 運算式是指派給 `Func` 或 `Action` 類型變數的匿名方法。 當您宣告區域函式時，引數類型和傳回型別是函式宣告的一部分。 引數類型和傳回型別是 Lambda 運算式之變數型別宣告的一部分，而不是 Lambda 運算式主體的一部分。 這兩個差異可能會導致更清楚的程式碼。

區域函式的明確指派規則與 Lambda 運算式不同。 您可以從所在範圍的任何程式碼位置參考區域函式宣告。 必須先將 lambda 運算式指派給委派變數，才能存取 (或透過參考 lambda 運算式) 的委派呼叫。 請注意，使用 lambda 運算式的版本必須在定義 lambda 運算式之前，先將其宣告和初始化 `nthFactorial` 。 如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。 這些差異表示使用區域函式時，您可以更輕鬆地建立遞迴演算法。 您可以宣告並定義呼叫其本身的區域函式。 Lambda 運算式必須加以宣告並指派預設值，才可以重新指派給參考相同 Lambda 運算式的主體。

明確指派規則也會影響區域函式或 Lambda 運算式所擷取的任何變數。 區域函式和 Lambda 運算式規則都要求在將區域函式或 Lambda 運算式轉換成委派時，明確指派任何擷取的變數。 差別在於 Lambda 運算式會在宣告時會轉換成委派。 區域函式只會在用作委派時，才會轉換成委派。 如果您宣告區域函式，並只透過類似方法的呼叫方式來參考它，則不會轉換成委派。 該規則可讓您在區域函式之封入範圍內的任何便利位置宣告區域函式。 通常會在父方法結尾的任何傳回陳述式之後宣告區域函式。

第三，編譯器可以執行靜態分析，讓區域函式明確指派封入範圍內所擷取的變數。 請考慮此範例：

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

編譯器可判斷 `LocalFunction` 是否在呼叫時明確指派 `y`。 由於 `LocalFunction` 是在 `return` 陳述式之前呼叫，因此會在 `return` 陳述式明確指派 `y`。

啟用範例分析的分析允許第四點差異。 根據其使用方式，區域函式可避免 Lambda 運算式一律需要的堆積配置。 如果區域函式永遠不會轉換成委派，而且區域函式所擷取的變數無法由其他 Lambda 或轉換成委派的區域函式擷取，則編譯器可以避免堆積配置。

請考慮使用以下非同步範例：

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。 如果是區域函式，實作關閉的物件可以是 `struct` 類型。 該結構類型會以傳址方式傳遞至區域函式。 這項實作差異可節省配置資源。

Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。 區域函式不會造成這項額外負荷。 在上述範例中，區域函式版本的配置比 lambda 運算式版本少兩倍。

> [!NOTE]
> 這個方法的對等區域函式也會使用關閉的類別。 不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。 區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。 Lambda 運算式中不可以有 `yield return` 陳述式。

雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。 如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。

## <a name="see-also"></a>另請參閱

- [方法](methods.md)
