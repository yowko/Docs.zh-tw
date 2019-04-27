---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 499949d1f4c20e1f465355bd076ba39f1496779b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920714"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
指定函式或`Get`存取子是迭代器。  
  
## <a name="remarks"></a>備註  
 *迭代器*對集合執行自訂反覆項目。 迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回一次一個集合中的每個項目。 當`Yield`到達陳述式時，保留在程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 迭代器可以實作為函式或`Get`屬性定義存取子。 `Iterator`修飾詞會出現在迭代器函式宣告或`Get`存取子。  
  
 從用戶端程式碼呼叫迭代器使用[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 迭代器函式的傳回型別或`Get`存取子可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。  
  
 迭代器不能有任何`ByRef`參數。  
  
 迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。  
  
 迭代器可以是匿名函式。 如需詳細資訊，請參閱 [Iterator](../../programming-guide/concepts/iterators.md)。  
  
## <a name="usage"></a>使用量  
 `Iterator` 修飾詞可用於以下內容：  
  
-   [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>範例  
 下列範例示範的迭代器函式。 迭代器函式具有`Yield`內的陳述式[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 每次反覆運算[針對每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)中的陳述式主體`Main`建立呼叫`Power`迭代器函式。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>範例  
 下列範例將示範本身為迭代器的 `Get` 存取子。 `Iterator`修飾詞是屬性宣告中。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 如需其他範例，請參閱 <<c0> [ 迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [迭代器](../../programming-guide/concepts/iterators.md)
- [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)
