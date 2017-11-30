---
title: "區域函式與 Lambda 運算式的比較"
description: "了解區域函式可能比 Lambda 運算式更適用的原因。"
keywords: "C#, .NET, .NET Core, 最新功能, 新功能, 區域函式, Lambda 運算式"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 20312b58a24dc991791edad4bb92d3a8ca6d501a
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="local-functions-compared-to-lambda-expressions"></a>相較於 lambda 運算式的區域函式

第一眼，[區域函式](programming-guide/classes-and-structs/local-functions.md)和 [Lambda 運算式](lambda-expressions.md)十分類似。 在許多情況下，使用 lambda 運算式和區域函式之間的選擇就是樣式和個人的喜好設定。 不過，有您可以使用其中一個或其他執行個體，您應該瞭解的實際差異。

讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。 首先是使用區域函式的版本：

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

針對使用 Lambda 運算式的實作版本進行對比：

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

區域函式具有名稱。 Lambda 運算式是指派給變數的匿名方法`Func`或`Action`型別。 當您宣告區域函式時，引數類型和傳回型別是函式宣告的一部分。 Lambda 的一部分，而運算式的引數類型和傳回型別是主體的 lambda 運算式的變數類型宣告的一部分。 這些兩個差異可能會導致更清楚的程式碼。

本機函式具有比 lambda 運算式的明確設定不同的規則。 您可以從其所在範圍中的任何程式碼位置參考本機函式宣告。 Lambda 運算式之前，必須被指派給委派變數可存取 （或透過 delgate 參考 lambda 運算式呼叫。）請注意，若為使用 Lambda 運算式的版本，則必須在定義 Lambda 運算式 `nthFactorial` 之前，將其宣告和初始化。 如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。
這些差異表示遞迴演算法容易使用的區域函式所建立。 您可以宣告和呼叫其本身的本機函式定義。 Lambda 運算式必須宣告，並指派預設值，才可以重新指派給參考相同的 lambda 運算式的主體。

明確指派規則也會影響本機函式或 task<tresult> epression 所擷取的任何變數。 區域函式和 lambda 運算式規則要求，所擷取的變數會明確地指派處時本機函式或 lambda 運算式轉換成委派。 差別在於 lambda 運算式轉換成委派宣告時。 區域函式會轉換成委派，做為委派時，才。 如果您宣告區域函式，並只參考它，藉由呼叫方法，它不會轉換成委派。 該規則可讓您宣告其封入範圍內的任何便利位置的區域函式。 通常會在父方法結尾處的區域函式宣告之後傳回的任何陳述式。

第三，編譯器可以執行靜態分析，可讓本機函式來明確地指派封閉範圍中所擷取的變數。 請考量以下範例：

```csharp
bool M()
{
    int y;
    Local();
    return y;

    void Local() => y = 0;
}
```

編譯器可決定`Local`明確指派`y`時呼叫。 因為`Local`之前，會呼叫`return`陳述式，`y`會在指派 definitiely`return`陳述式。

分析，可讓分析可讓第四個差異。
根據其使用情形的區域函式可以避免永遠是必要的 lambda 運算式的堆積配置。 如果區域函式永遠不會轉換成委派，而且沒有任何區域函式所擷取的變數擷取其他的 lambda 或轉換成委派的區域函式，編譯器可以避免堆積配置。 

請考慮使用以下非同步範例：

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。 如果是區域函式，實作關閉的物件可以是 `struct` 類型。 該結構類型會是由參考傳遞至本機的函式。 在實作這項差異會儲存有關配置。

具現化所需的 lambda 運算式表示額外的記憶體配置，並可能會在時間關鍵程式碼路徑中的與效能因素。
區域函式不會造成這項額外負荷。 在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。

> [!NOTE]
> 這個方法的對等區域函式也會使用關閉的類別。 不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。 區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。 `yield return`陳述式不允許在 lambda 運算式中。

雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。
如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。
