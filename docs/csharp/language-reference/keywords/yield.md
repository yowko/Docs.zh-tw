---
title: "yield (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eb55fd5b1ade48316516cda83633935abbf8dcf9
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="yield-c-reference"></a>yield (C# 參考)
在陳述式中使用 `yield` 關鍵字時，您會表示關鍵字所在的方法、運算子或 `get` 存取子是迭代器。 如果使用 `yield` 定義迭代器，當您為自訂集合類型實作 <xref:System.Collections.Generic.IEnumerator%601> 和 <xref:System.Collections.IEnumerable> 模式時，就不需要明確的額外類別 (保存列舉之狀態的類別，請參閱 <xref:System.Collections.IEnumerator> 中的範例)。  
  
 下列範例將示範兩種形式的 `yield` 陳述式。  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>備註  
 您可以使用 `yield return` 陳述式一次傳回一個元素。  
  
 使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式或 LINQ 查詢，即可使用 iterator 方法。 `foreach` 迴圈的每個反覆項目都會呼叫 Iterator 方法。 當 Iterator 方法中到達 `yield return` 陳述式時，就會傳回 `expression` 並保留程式碼中目前的位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 您可以使用 `yield break` 陳述式結束反覆項目。  
  
 如需迭代器的詳細資訊，請參閱 [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) (迭代器)。  
  
## <a name="iterator-methods-and-get-accessors"></a>Iterator 方法和 get 存取子  
 迭代器的宣告必須符合下列需求：  
  
-   傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
-   宣告不可包含任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數。  
  
 傳回 `yield` 或 <xref:System.Collections.IEnumerable> 的 <xref:System.Collections.IEnumerator> 類型迭代器為 `object`。  如果迭代器傳回 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.Generic.IEnumerator%601>，則 `yield return` 陳述式中必須進行從運算式類型轉換成泛型類型參數的隱含轉換。  
  
 具有下列特性的方法中不可包含 `yield return` 或 `yield break` 陳述式：  
  
-   匿名方法。 如需詳細資訊，請參閱[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。  
  
-   包含不安全區塊的方法。 如需詳細資訊，請參閱 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)。  
  
## <a name="exception-handling"></a>例外狀況處理  
 `yield return` 陳述式不能位於 try-catch 區塊內。 `yield return` 陳述式可以位於 try-finally 陳述式的 try 區塊內。  
  
 `yield break` 陳述式可以位於 try 區塊或 catch 區塊中，但是不可位於 finally 區塊中。  
  
 如果 `foreach` 主體 (在 Iterator 方法之外) 擲回例外狀況，則會執行 Iterator 方法中的 `finally` 區塊。  
  
## <a name="technical-implementation"></a>技術實作  
 下列程式碼會從 Iterator 方法傳回 `IEnumerable<string>`，然後逐一查看其元素。  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 對 `MyIteratorMethod` 的呼叫不會執行方法的主體。 呼叫會改為將 `IEnumerable<string>` 傳回至 `elements` 變數中。  
  
 在 `foreach` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。 這個呼叫會執行 `MyIteratorMethod` 的主體，直到下一個 `yield return` 陳述式為止。 `yield return` 陳述式所傳回的運算式不僅會判斷迴圈主體所使用之 `element` 變數的值，也會判斷元素的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性，該屬性會是 `IEnumerable<string>`。  
  
 在 `foreach` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `yield return` 陳述式時再次停止。 當 Iterator 方法結束或到達 `foreach` 陳述式時，`yield break` 迴圈便完成。  
  
## <a name="example"></a>範例  
 下列範例中的陳述式 `yield return` 位於 `for` 迴圈內。 `foreach` 中 `Process` 陳述式主體的每個反覆項目都會建立對 `Power` Iterator 函式的呼叫。 每次呼叫 Iterator 函式都會執行下一個 `yield return` 陳述式，這會在 `for` 迴圈的下一個反覆項目期間發生。  
  
 Iterator 方法的傳回類型是 <xref:System.Collections.IEnumerable>，其為 Iterator 介面類型。 呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。  
  
 [!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例將示範本身為迭代器的 `get` 存取子。 在這個範例中，每個 `yield return` 陳述式都會傳回使用者定義類別的執行個體。  
  
 [!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)

