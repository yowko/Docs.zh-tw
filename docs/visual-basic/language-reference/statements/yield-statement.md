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
ms.openlocfilehash: f938ad29df54ade6722f3de33e931c851ade8c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="yield-statement-visual-basic"></a>Yield 陳述式 (Visual Basic)
傳送至集合的下一個項目`For Each...Next`陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>參數  
  
|詞彙|定義|  
|---|---|  
|`expression`|必要。 隱含轉換為迭代器函式類型的運算式或`Get`存取子，其包含`Yield`陳述式。|  
  
## <a name="remarks"></a>備註  
 `Yield`陳述式會傳回一次集合中的一個項目。 `Yield`陳述式會包含在迭代器函式或`Get`存取子，在集合上執行自訂反覆項目。  
  
 您可以使用迭代器函式使用[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)或 LINQ 查詢。 每個反覆項目`For Each`迴圈就會呼叫 iterator 函式。 當`Yield`iterator 函式，在到達陳述式時`expression`傳回，並保留程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 類型必須有隱含的轉換`expression`中`Yield`陳述式的傳回類型迭代器。  
  
 您可以使用`Exit Function`或`Return`陳述式結束反覆項目。  
  
 」 產生 「 不是保留的字，而且只有在使用中時，具有特殊意義`Iterator`函式或`Get`存取子。  
  
 如需有關迭代器函式和`Get`存取子中，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="iterator-functions-and-get-accessors"></a>Iterator 函式和 Get 存取子  
 迭代器函式宣告或`Get`存取子必須符合下列需求：  
  
-   它必須包括[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)修飾詞。  
  
-   傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
-   它不能有任何`ByRef`參數。  
  
 Iterator 函式不能出現在事件、 執行個體建構函式、 靜態的建構函式或靜態的解構函式。  
  
 Iterator 函式可以是匿名函式。 如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="exception-handling"></a>例外狀況處理  
 A`Yield`陳述式可以是內部`Try`區塊[再試一次...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 A`Try`區塊具有`Yield`陳述式可以有`Catch`封鎖了，而且可以有`Finally`區塊。  
  
 A`Yield`陳述式不能在`Catch`區塊或`Finally`區塊。  
  
 如果`For Each`（之外的迭代器函式） 的主體就會擲回例外狀況， `Catch` iterator 函式中的區塊不會執行，但`Finally`就會執行 iterator 函式中的區塊。 A`Catch`迭代器函式內的區塊會攔截迭代器函式內發生的例外狀況。  
  
## <a name="technical-implementation"></a>技術實作  
 下列程式碼會傳回`IEnumerable (Of String)`從 iterator 函式，然後逐一查看的項目`IEnumerable (Of String)`。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 若要呼叫`MyIteratorFunction`不會執行函式主體。 呼叫會改為將 `IEnumerable(Of String)` 傳回至 `elements` 變數中。  
  
 在 `For Each` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。 這個呼叫會執行 `MyIteratorFunction` 的主體，直到下一個 `Yield` 陳述式為止。 `Yield`陳述式傳回決定不僅值的運算式`element`迴圈主體所消耗的變數，但也<xref:System.Collections.Generic.IEnumerator%601.Current%2A>屬性的項目，這是`IEnumerable (Of String)`。  
  
 在 `For Each` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `Yield` 陳述式時再次停止。 `For Each`迴圈完成時的結尾迭代器函式或`Return`或`Exit Function`陳述式為止。  
  
## <a name="example"></a>範例  
 下列範例具有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 每個反覆項目[每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式主體中的`Main`建立呼叫`Power`iterator 函式。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 Iterator 方法的傳回型別是<xref:System.Collections.Generic.IEnumerable%601>，迭代器介面類型。 呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例將示範本身為迭代器的 `Get` 存取子。 屬性宣告包含`Iterator`修飾詞。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 如需其他範例，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../../../visual-basic/language-reference/statements/index.md)
