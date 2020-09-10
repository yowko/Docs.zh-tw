---
title: 區域函式 - C# 程式設計手冊
description: 'C # 中的區域函式是在另一個成員中嵌套的私用方法，可從其包含成員中呼叫。'
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: c1c6c6becb3894b05cb9ed89f7f33dcf249b20eb
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656181"
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
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

區域函式可以使用 [async](../../language-reference/keywords/async.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修飾詞。

請注意，在區域函式中可以存取包含成員中所定義的所有區域變數 (包含其方法參數)。

不同于方法定義，區域函式定義不能包含成員存取修飾詞。 因為所有區域函式都是私用，所以包含 `private` 這類關鍵字的存取修飾詞會產生編譯器錯誤 CS0106「修飾詞 'private' 對此項目無效」。

> [!NOTE]
> 在 c # 8.0 之前，區域函數不能包含 `static` 修飾詞。 包含 `static` 關鍵字會產生編譯器錯誤 CS0106 「修飾詞 ' static ' 對此專案無效」或編譯器錯誤，指出您應該使用 c # 8.0 或更高版本。

此外，屬性無法套用至區域函式或其參數和型別參數。

下列範例定義名為 `AppendPathSeparator` 的區域函式，而此區域函式是名為 `GetText` 之方法的私用項目：

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>區域函式和例外狀況

區域函式的其中一個有用功能是它們可以允許立即顯示例外狀況。 對於方法迭代器，只有在列舉傳回的序列時，才會顯示例外狀況，而不是擷取迭代器時。 對於非同步方法，等候傳回的工作時，會觀察到非同步方法中擲回的任何例外狀況。

下列範例定義 `OddSequence` 方法，以列舉所指定範圍之間的奇數。 因為它會將一個大於 100 的數字傳遞至 `OddSequence` 列舉值方法，所以此方法會擲回 <xref:System.ArgumentOutOfRangeException>。 顯示範例輸出時，只有在您逐一查看數字時，才會顯示例外狀況，而不是擷取列舉值時。

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

相反地，您可以在執行驗證時以及從區域函式傳回迭代器來擷取迭代器之前擲回例外狀況，如下列範例所示。

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

透過類似的方式，可以使用區域函式來處理非同步作業外的例外狀況。 非同步方法中擲回的例外狀況通常需要您檢查 <xref:System.AggregateException> 的內部例外狀況。 區域函式允許您的程式碼快速失敗，並允許擲回並同步觀察到您的例外狀況。

下列範例使用名為 `GetMultipleAsync` 的非同步方法暫停指定的秒數，並傳回該秒數之隨機倍數的值。 延遲上限是 5 秒；如果值大於 5，則會產生 <xref:System.ArgumentOutOfRangeException>。 如下列範例所示，在 `GetMultipleAsync` 方法開始執行之後，會將值 6 傳遞給 `GetMultipleAsync` 方法時所擲回的例外狀況包裝在 <xref:System.AggregateException> 中。

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

與使用方法迭代器執行的作業相同，我們可以從這個範例重構程式碼先進行驗證，再呼叫非同步方法。 如下列範例輸出所示，<xref:System.ArgumentOutOfRangeException> 不會包裝在 <xref:System.AggregateException> 中。

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>區域函式與 Lambda 運算式的比較

第一眼，區域函式和 [Lambda 運算式](../../language-reference/operators/lambda-expressions.md)十分類似。 在許多情況下，選擇使用 Lambda 運算式或區域函式與樣式和個人喜好設定相關。 不過，您應該注意可使用任一選項的實際差異。

讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。 首先是使用區域函式的版本：

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

針對使用 Lambda 運算式的實作版本進行對比：

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

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

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。 如果是區域函式，實作關閉的物件可以是 `struct` 類型。 該結構類型會以傳址方式傳遞至區域函式。 這項實作差異可節省配置資源。

Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。 區域函式不會造成這項額外負荷。 在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。

> [!NOTE]
> 這個方法的對等區域函式也會使用關閉的類別。 不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。 區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。 Lambda 運算式中不可以有 `yield return` 陳述式。

雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。 如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。

## <a name="see-also"></a>另請參閱

- [方法](methods.md)
