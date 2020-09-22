---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 0b459a16317b8ba55886e52ecadb227ddf2fee83
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875440"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)

指定函數或存取子 `Get` 是反覆運算器。  
  
## <a name="remarks"></a>備註  

 *反覆運算器*會在集合上執行自訂反復專案。 反覆運算器會使用 [Yield](../statements/yield-statement.md) 語句，一次傳回集合中的每個元素。 當 `Yield` 到達語句時，會保留程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 反覆運算器可以實作為函式或 `Get` 屬性定義的存取子。 `Iterator`修飾詞會出現在 iterator 函數或存取子的宣告中 `Get` 。  
  
 您可以使用 For Each 的，從用戶端程式代碼呼叫反覆運算器。 [下一個語句](../statements/for-each-next-statement.md)。  
  
 Iterator 函數或存取子的傳回型別 `Get` 可以是 <xref:System.Collections.IEnumerable> 、 <xref:System.Collections.Generic.IEnumerable%601> 、 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 。  
  
 反覆運算器不能有任何 `ByRef` 參數。  
  
 迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。  
  
 反覆運算器可以是匿名函數。 如需詳細資訊，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="usage"></a>使用方式  

 `Iterator` 修飾詞可用於以下內容：  
  
- [Function 陳述式](../statements/function-statement.md)  
  
- [Property Statement](../statements/property-statement.md)  
  
## <a name="example"></a>範例  

 下列範例示範 iterator 函數。 反覆運算器函式的 `Yield` 語句位於 [For .。。Next](../statements/for-next-statement.md) 迴圈。 [每個語句主體](../statements/for-each-next-statement.md)的每個反復專案 `Main` 都會建立 `Power` iterator 函數的呼叫。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>範例  

 下列範例將示範本身為迭代器的 `Get` 存取子。 `Iterator`修飾詞位於屬性宣告中。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 如需其他範例，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [迭代器](../../programming-guide/concepts/iterators.md)
- [Yield 陳述式](../statements/yield-statement.md)
