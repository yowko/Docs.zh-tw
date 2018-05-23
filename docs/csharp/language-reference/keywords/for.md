---
title: for (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 2c099411499c6ca8396c55955bdc634e48caf621
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
---
# <a name="for-c-reference"></a>for (C# 參考)

透過 `for` 迴圈，您可以重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。 這種迴圈對於逐一查看陣列很有用，也適用於您事先知道迴圈要反覆運算幾次的其他應用。
  
## <a name="example"></a>範例

在下列範例中，`i` 值會寫入至主控台，並在迴圈每次反覆運算就加 1：
  
[!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]
  
上述範例中的 [for 陳述式](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)會執行下列動作：
  
1.  首先，請建立變數 `i` 的初始值。 不論迴圈重複幾次，此步驟只會發生一次。 您可以將此初始化視為在迴圈程序之外進行。
  
2.  為了評估條件 (`i <= 5`)，`i` 值會與 5 進行比較。
  
    -   如果 `i` 小於或等於 5，則條件會評估為 `true`，而且會執行下列動作。  
  
        1.  迴圈主體中的 `Console.WriteLine` 陳述式會顯示 `i` 值。  
  
        2.  此 `i` 值會加 1。  
  
        3.  迴圈會回到步驟 2 的開頭，以重新評估條件。  
  
    -   如果 `i` 大於 5，則條件會評估為`false`，而且您會結束迴圈。  
  
請注意，如果 `i` 的初始值大於 5，則迴圈主體一次也不會執行。

## <a name="sections-of-a-for-statement"></a>for 陳述式的區段
  
每個 [for 陳述式](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)都會定義*初始設定式*、*條件*和*迭代器*區段。 這些區段通常會決定迴圈的反覆運算次數。  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
這些區段有下列用途：
  
-   初始設定式區段會設定初始條件。 此區段中的陳述式只會執行一次，之後就會進入迴圈。 此區段只能包含下列兩個選項的其中之一。  
  
    -   區域迴圈變數的宣告和初始化，如第一個範例所示 (`int i = 1`)。 這是迴圈的區域變數，無法從迴圈外部存取。  
  
    -   下列清單中的零個或多個陳述式運算式，並以逗號分隔。  
  
        -   [指派](../../../csharp/language-reference/operators/assignment-operator.md)陳述式  
  
        -   方法的引動過程  
  
        -   前置或後置[遞增](../../../csharp/language-reference/operators/increment-operator.md)運算式，例如 `++i` 或 `i++`  
  
        -   前置或後置[遞減](../../../csharp/language-reference/operators/decrement-operator.md)運算式，例如 `--i` 或 `i--`  
  
        -   使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 建立物件  
  
        -   [await](../../../csharp/language-reference/keywords/await.md) 運算式  
  
-   條件區段包含布林運算式，以評估判斷迴圈應該結束或重新執行。  
  
-   迭代器區段會定義迴圈主體每次反覆運算之後的狀況。 迭代器區段包含下列零個或多個陳述式運算式，並以逗號分隔：  
  
    -   [指派](../../../csharp/language-reference/operators/assignment-operator.md)陳述式  
  
    -   方法的引動過程  
  
    -   前置或後置[遞增](../../../csharp/language-reference/operators/increment-operator.md)運算式，例如 `++i` 或 `i++`  
  
    -   前置或後置[遞減](../../../csharp/language-reference/operators/decrement-operator.md)運算式，例如 `--i` 或 `i--`  
  
    -   使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 建立物件  
  
    -   [await](../../../csharp/language-reference/keywords/await.md) 運算式  
  
-   迴圈主體包含陳述式、空白陳述式或陳述式區塊，您可以用括號括住零個或多個陳述式來建立。  
  
     您可以使用 [break](../../../csharp/language-reference/keywords/break.md) 關鍵字跳出 `for` 迴圈，或使用 [continue](../../../csharp/language-reference/keywords/continue.md) 關鍵字逐步執行到下一個反覆運算。 您也可以使用 [goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式結束任何迴圈。  
  
本主題中的第一個範例示範最典型的 `for` 迴圈，並在各區段中進行下列選擇：
  
-   初始設定式會宣告並初始化區域迴圈變數 `i`，以維護迴圈的反覆運算計數。  
  
-   條件會根據已知的最後一個值 5 來檢查迴圈變數的值。  
  
-   迭代器區段使用後置遞增陳述式 `i++`，來合計迴圈的每個反覆運算。

## <a name="more-examples"></a>更多範例
  
下列範例描述幾個較少見的選項︰將值指派給初始設定式區段中的外部迴圈變數、在初始設定式和迭代器區段中叫用 `Console.WriteLine` 方法，以及在迭代器區段中變更兩個變數的值。
  
[!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
所有定義 `for` 陳述式的運算式都是選擇性的。 例如，下列陳述式會建立一個無限迴圈：
  
[!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>另請參閱

[for 陳述式 (C# 語言規格)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[C# 參考](../../../csharp/language-reference/index.md)  
[C# 程式設計指南](../../../csharp/programming-guide/index.md)  
[C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
[foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)  
[for 陳述式 (C++)](/cpp/cpp/for-statement-cpp)  
[反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)
