---
title: 區域函式與 Lambda 運算式的比較
description: 了解區域函式可能比 Lambda 運算式更適用的原因。
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 4fb8ea78b783871a19a8d5578d571e00da37642a
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2018
---
# <a name="local-functions-compared-to-lambda-expressions"></a>區域函式與 Lambda 運算式的比較

第一眼，[區域函式](programming-guide/classes-and-structs/local-functions.md)和 [Lambda 運算式](lambda-expressions.md)十分類似。 在許多情況下，選擇使用 Lambda 運算式或區域函式與樣式和個人喜好設定相關。 不過，您應該注意可使用任一選項的實際差異。

讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。 首先是使用區域函式的版本：

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

針對使用 Lambda 運算式的實作版本進行對比：

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

區域函式具有名稱。 Lambda 運算式是指派給 `Func` 或 `Action` 類型變數的匿名方法。 當您宣告區域函式時，引數類型和傳回型別是函式宣告的一部分。 引數類型和傳回型別是 Lambda 運算式之變數型別宣告的一部分，而不是 Lambda 運算式主體的一部分。 這兩個差異可能會導致更清楚的程式碼。

區域函式的明確指派規則與 Lambda 運算式不同。 您可以從所在範圍的任何程式碼位置參考區域函式宣告。 Lambda 運算式必須指派給委派變數，才能提供存取 (或透過參考 Lambda 運算式的委派進行呼叫)。請注意，若為使用 Lambda 運算式的版本，則必須在定義 Lambda 運算式 `nthFactorial` 之前，將其宣告和初始化。 如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。
這些差異表示使用區域函式時，您可以更輕鬆地建立遞迴演算法。 您可以宣告並定義呼叫其本身的區域函式。 Lambda 運算式必須加以宣告並指派預設值，才可以重新指派給參考相同 Lambda 運算式的主體。

明確指派規則也會影響區域函式或 Lambda 運算式所擷取的任何變數。 區域函式和 Lambda 運算式規則都要求在將區域函式或 Lambda 運算式轉換成委派時，明確指派任何擷取的變數。 差別在於 Lambda 運算式會在宣告時會轉換成委派。 區域函式只會在用作委派時，才會轉換成委派。 如果您宣告區域函式，並只透過類似方法的呼叫方式來參考它，則不會轉換成委派。 該規則可讓您在區域函式之封入範圍內的任何便利位置宣告區域函式。 通常會在父方法結尾的任何傳回陳述式之後宣告區域函式。

第三，編譯器可以執行靜態分析，讓區域函式明確指派封入範圍內所擷取的變數。 請考量以下範例：

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

編譯器可判斷 `LocalFunction` 是否在呼叫時明確指派 `y`。 由於 `LocalFunction` 是在 `return` 陳述式之前呼叫，因此會在 `return` 陳述式明確定義 `y`。

啟用範例分析的分析允許第四點差異。
根據其使用方式，區域函式可避免 Lambda 運算式一律需要的堆積配置。 如果區域函式永遠不會轉換成委派，而且區域函式所擷取的變數無法由其他 Lambda 或轉換成委派的區域函式擷取，則編譯器可以避免堆積配置。 

請考慮使用以下非同步範例：

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。 如果是區域函式，實作關閉的物件可以是 `struct` 類型。 該結構類型會以傳址方式傳遞至區域函式。 這項實作差異可節省配置資源。

Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。
區域函式不會造成這項額外負荷。 在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。

> [!NOTE]
> 這個方法的對等區域函式也會使用關閉的類別。 不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。 區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。 Lambda 運算式中不可以有 `yield return` 陳述式。

雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。
如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。
