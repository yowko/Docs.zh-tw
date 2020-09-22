---
title: Yield 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 783785f2a078b6ad8f975846c44ee4e716a12773
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866505"
---
# <a name="yield-statement-visual-basic"></a>Yield 陳述式 (Visual Basic)

將集合的下一個元素傳送至 `For Each...Next` 語句。  
  
## <a name="syntax"></a>語法  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>參數  
  
|詞彙|定義|  
|---|---|  
|`expression`|必要。 可隱含轉換成反覆運算器函式類型的運算式，或 `Get` 包含語句的存取子 `Yield` 。|  
  
## <a name="remarks"></a>備註  

 `Yield`語句會一次傳回集合的一個元素。 `Yield`語句包含在反覆運算器函數或 `Get` 存取子中，它會對集合執行自訂反復專案。  
  
 您可以使用 For Each 的來取用 iterator 函數 ... [Next 語句](for-each-next-statement.md) 或 LINQ 查詢。 迴圈的每個反復專案都會 `For Each` 呼叫 iterator 函數。 當 `Yield` 反覆運算器函式中到達語句時， `expression` 會傳回，而且會保留程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 從語句的類型 `expression` `Yield` 到反覆運算器的傳回型別都必須有隱含轉換。  
  
 您可以使用 `Exit Function` 或 `Return` 語句來結束反復專案。  
  
 "Yield" 不是保留字，只有在函式或存取子中使用時，才具有特殊意義 `Iterator` `Get` 。  
  
 如需 iterator 函數和存取子的詳細資訊 `Get` ，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="iterator-functions-and-get-accessors"></a>Iterator 函數和 Get 存取子  

 反覆運算器函數或存取子的宣告 `Get` 必須符合下列需求：  
  
- 它必須包含 [Iterator](../modifiers/iterator.md) 修飾詞。  
  
- 傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
- 它不能有任何 `ByRef` 參數。  
  
 反覆運算器函數不能出現在事件、實例的函式、靜態函式或靜態的函式中。  
  
 Iterator 函數可以是匿名函數。 如需詳細資訊，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="exception-handling"></a>例外狀況處理  

 `Yield`語句可以在 `Try` Try 的區塊內 ... [抓住。。。Finally 語句](try-catch-finally-statement.md)。 `Try`具有語句的區塊 `Yield` 可以有 `Catch` 區塊，而且可以有 `Finally` 區塊。  
  
 `Yield`語句不能在 `Catch` 區塊或 `Finally` 區塊內。  
  
 如果在 `For Each` 反覆運算器函式之外 (主體) 擲回例外狀況， `Catch` 則不會執行 iterator 函數中的區塊，但 `Finally` 會執行 iterator 函數中的區塊。 `Catch`反覆運算器函式內的區塊只會捕捉反覆運算器函式內發生的例外狀況。  
  
## <a name="technical-implementation"></a>技術實作  

 下列程式碼會 `IEnumerable (Of String)` 從 iterator 函數傳回，然後逐一查看的元素 `IEnumerable (Of String)` 。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 的呼叫 `MyIteratorFunction` 不會執行函數的主體。 呼叫會改為將 `IEnumerable(Of String)` 傳回至 `elements` 變數中。  
  
 在 `For Each` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。 這個呼叫會執行 `MyIteratorFunction` 的主體，直到下一個 `Yield` 陳述式為止。 語句會傳回 `Yield` 運算式，該運算式不僅會判斷 `element` 迴圈主體所耗用量的變數值，也會決定專案的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性，也就是 `IEnumerable (Of String)` 。  
  
 在 `For Each` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `Yield` 陳述式時再次停止。 `For Each`當到達 iterator 函數或或語句的結尾時，迴圈 `Return` `Exit Function` 就會完成。  
  
## <a name="example"></a>範例  

 下列範例 `Yield` 中的語句位於 [For .。。Next](for-next-statement.md) 迴圈。 [每個語句主體](for-each-next-statement.md)的每個反復專案 `Main` 都會建立 `Power` iterator 函數的呼叫。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 Iterator 方法的傳回型別是 <xref:System.Collections.Generic.IEnumerable%601> ，iterator 介面型別。 呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>範例  

 下列範例將示範本身為迭代器的 `Get` 存取子。 屬性宣告包含修飾詞 `Iterator` 。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 如需其他範例，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="see-also"></a>另請參閱

- [陳述式](index.md)
