---
title: Yield 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 57b36bb32e1a575a645f7a15045bf0898dd10dfd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582208"
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
|`expression`|必要項。 運算式，可隱含地轉換成包含 `Yield` 語句之反覆運算器函數或 `Get` 存取子的類型。|  
  
## <a name="remarks"></a>備註  
 @No__t_0 語句一次會傳回集合的一個元素。 @No__t_0 語句會包含在 iterator 函式或 `Get` 存取子中，這會在集合上執行自訂反復專案。  
  
 您可以使用 For Each 的來取用 iterator 函數 ... [下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)或 LINQ 查詢。 @No__t_0 迴圈的每個反復專案都會呼叫 iterator 函數。 當反覆運算器函式中到達 `Yield` 語句時，會傳回 `expression`，並保留程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 隱含轉換必須存在於 `Yield` 語句中的 `expression` 類型，到反覆運算器的傳回型別中。  
  
 您可以使用 `Exit Function` 或 `Return` 語句來結束反復專案。  
  
 "Yield" 不是保留字，只有在 `Iterator` 函式或 `Get` 存取子中使用時，才具有特殊意義。  
  
 如需 iterator 函數和 `Get` 存取子的詳細資訊，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="iterator-functions-and-get-accessors"></a>Iterator 函數和 Get 存取子  
 反覆運算器函數或 `Get` 存取子的宣告必須符合下列需求：  
  
- 它必須包含[Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)修飾詞。  
  
- 傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
- 它不能有任何 `ByRef` 參數。  
  
 反覆運算器函式不能出現在事件、實例的函數、靜態的函式或靜態的析構函數中。  
  
 Iterator 函數可以是匿名函式。 如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="exception-handling"></a>例外狀況處理  
 @No__t_0 語句可以在 Try 的 `Try` 區塊內 ... [Catch 。Finally 語句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 具有 `Yield` 語句的 `Try` 區塊可以有 `Catch` 區塊，而且可以有 `Finally` 區塊。  
  
 @No__t_0 語句不能在 `Catch` 區塊或 `Finally` 區塊內。  
  
 如果 `For Each` 主體（iterator 函數之外）擲回例外狀況，則不會執行 iterator 函式中的 `Catch` 區塊，但會執行 iterator 函式中的 `Finally` 區塊。 Iterator 函式內的 `Catch` 區塊只會攔截在 iterator 函式內發生的例外狀況。  
  
## <a name="technical-implementation"></a>技術實作  
 下列程式碼會從 iterator 函式傳回 `IEnumerable (Of String)`，然後逐一查看 `IEnumerable (Of String)` 的元素。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 @No__t_0 的呼叫不會執行函式的主體。 呼叫會改為將 `IEnumerable(Of String)` 傳回至 `elements` 變數中。  
  
 在 `For Each` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。 這個呼叫會執行 `MyIteratorFunction` 的主體，直到下一個 `Yield` 陳述式為止。 @No__t_0 語句傳回的運算式，不僅會判斷迴圈主體所使用之 `element` 變數的值，也會決定元素的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性，這是 `IEnumerable (Of String)`。  
  
 在 `For Each` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `Yield` 陳述式時再次停止。 當反覆運算器函數或 `Return` 或 `Exit Function` 語句的結尾達到時，`For Each` 迴圈就會完成。  
  
## <a name="example"></a>範例  
 下列範例中的 `Yield` 語句位於[For 。下一個](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 @No__t_1 中[每](../../../visual-basic/language-reference/statements/for-each-next-statement.md)個語句主體的每個反復專案都會建立對 `Power` iterator 函數的呼叫。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 反覆運算器方法的傳回型別是 <xref:System.Collections.Generic.IEnumerable%601>，也就是反覆運算器介面型別。 呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>範例  
 下列範例將示範本身為迭代器的 `Get` 存取子。 屬性宣告包含 `Iterator` 的修飾詞。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 如需其他範例，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="see-also"></a>請參閱

- [陳述式](../../../visual-basic/language-reference/statements/index.md)
