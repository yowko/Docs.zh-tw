---
title: "區域函式 (C# 程式設計手冊)"
ms.date: 06/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e95d48e451038f0f7004d0901f329b2c57fe5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="local-functions-c-programming-guide"></a>區域函式 (C# 程式設計手冊)

從 C# 7 開始，C# 支援「區域函式」。 區域函式是另一個成員中巢狀型別的私用方法。 它們只可以從其包含成員呼叫。 區域函式可以宣告於下列項目中，以及從下列項目呼叫：

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
> 在某些情況下，您可以使用 Lambda 運算式來實作區域函式也支援的功能。 如需比較，請參閱[區域函式與 Lambda 運算式的比較](../../local-functions-vs-lambdas.md)。

區域函式讓程式碼的意圖更為清楚。 讀取您程式碼的任何人都可以知道無法呼叫這個方法，但包含的方法除外。 對於 Team 專案，它們也可讓另一個開發人員無法從類別或結構的其他位置錯誤地直接呼叫方法。
 
## <a name="local-function-syntax"></a>區域函式語法

區域函式定義為包含成員內的巢狀方法。 其定義具有下列語法：

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

區域函式可以使用 [async](../../language-reference/keywords/async.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修飾詞。 

請注意，在區域函式中可以存取包含成員中所定義的所有區域變數 (包含其方法參數)。 

與方法定義不同，區域函式定義不能包含下列項目：

- 成員存取修飾詞。 因為所有區域函式都是私用，所以包含 `private` 這類關鍵字的存取修飾詞會產生編譯器錯誤 CS0106「修飾詞 'private' 對此項目無效」。
 
- [static](../../language-reference/keywords/static.md) 關鍵字。 包含 `static` 關鍵字會產生編譯器錯誤 CS0106「修飾詞 'static' 對此項目無效」。

此外，屬性無法套用至區域函式或其參數和型別參數。 
 
下列範例定義名為 `AppendPathSeparator` 的區域函式，而此區域函式是名為 `GetText` 之方法的私用項目：
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>區域函式和例外狀況

區域函式的其中一個有用功能是它們可以允許立即顯示例外狀況。 對於方法迭代器，只有在列舉傳回的序列時，才會顯示例外狀況，而不是擷取迭代器時。 對於非同步方法，等候傳回的工作時，會觀察到非同步方法中擲回的任何例外狀況。 

下列範例定義 `OddSequence` 方法，以列舉所指定範圍之間的奇數。 因為它會將一個大於 100 的數字傳遞至 `OddSequence` 列舉值方法，所以此方法會擲回 <xref:System.ArgumentOutOfRangeException>。 顯示範例輸出時，只有在您逐一查看數字時，才會顯示例外狀況，而不是擷取列舉值時。

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

相反地，您可以在執行驗證時以及從區域函式傳回迭代器來擷取迭代器之前擲回例外狀況，如下列範例所示。

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

透過類似的方式，可以使用區域函式來處理非同步作業外的例外狀況。 非同步方法中擲回的例外狀況通常需要您檢查 <xref:System.AggregateException> 的內部例外狀況。 區域函式允許您的程式碼快速失敗，並允許擲回並同步觀察到您的例外狀況。

下列範例使用名為 `GetMultipleAsync` 的非同步方法暫停指定的秒數，並傳回該秒數之隨機倍數的值。 延遲上限是 5 秒；如果值大於 5，則會產生 <xref:System.ArgumentOutOfRangeException>。 如下列範例所示，在 `GetMultipleAsync` 方法開始執行之後，會將值 6 傳遞給 `GetMultipleAsync` 方法時所擲回的例外狀況包裝在 <xref:System.AggregateException> 中。

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

與使用方法迭代器執行的作業相同，我們可以從這個範例重構程式碼先進行驗證，再呼叫非同步方法。 如下列範例輸出所示，<xref:System.ArgumentOutOfRangeException> 不會包裝在 <x:System.AggregateException> 中。

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>請參閱
[方法](methods.md)
