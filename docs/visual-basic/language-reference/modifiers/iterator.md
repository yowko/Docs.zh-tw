---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351528"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
指定函數或 `Get` 存取子是反覆運算器。  
  
## <a name="remarks"></a>備註  
 *反覆運算器*會在集合上執行自訂反復專案。 反覆運算器會使用[Yield](../../../visual-basic/language-reference/statements/yield-statement.md)語句，一次傳回集合中的每個元素。 當到達 `Yield` 語句時，會保留程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 反覆運算器可以實作為函數，或當做屬性定義的 `Get` 存取子來執行。 `Iterator` 修飾詞會出現在 iterator 函數或 `Get` 存取子的宣告中。  
  
 您可以從用戶端程式代碼呼叫反覆運算器，方法是使用[For Each 。下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 Iterator 函數或 `Get` 存取子的傳回類型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
 反覆運算器不能有任何 `ByRef` 參數。  
  
 迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。  
  
 Iterator 可以是匿名函式。 如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="usage"></a>使用方式  
 `Iterator` 修飾詞可用於以下內容：  
  
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>範例  
 下列範例示範反覆運算器函數。 Iterator 函數的 `Yield` 語句位於[For 。下一個](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 `Main` 中[每](../../../visual-basic/language-reference/statements/for-each-next-statement.md)個語句主體的每個反復專案都會建立對 `Power` iterator 函數的呼叫。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>範例  
 下列範例將示範本身為迭代器的 `Get` 存取子。 `Iterator` 修飾詞位於屬性宣告中。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 如需其他範例，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [迭代器](../../programming-guide/concepts/iterators.md)
- [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)
