---
title: OrElse 運算子
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: edac3eeaef5d0127f10a0d570ca27c8158806ff3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866723"
---
# <a name="orelse-operator-visual-basic"></a>OrElse 運算子 (Visual Basic)

在兩個運算式上執行最少運算內含邏輯分離。  
  
## <a name="syntax"></a>Syntax  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 任何 `Boolean` 運算式。  
  
 `expression1`  
 必要。 任何 `Boolean` 運算式。  
  
 `expression2`  
 必要。 任何 `Boolean` 運算式。  
  
## <a name="remarks"></a>備註  

 如果已編譯的程式碼可以略過一個運算式的評估（視另一個運算式的結果而 *定）* ，則邏輯運算稱為「最少運算」。 如果評估的第一個運算式的結果決定作業的最後結果，則不需要評估第二個運算式，因為它無法變更最後的結果。 如果略過的運算式很複雜，或是牽涉到程序呼叫，則最少運算可以改善效能。  
  
 如果任一個或兩個運算式都評估為 `True` ， `result` 就是 `True` 。 下表說明如何 `result` 決定。  
  
|如果 `expression1` 為 |而且 `expression2` 是|的值 `result` 為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|未評估 () |`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>資料類型  

 `OrElse`運算子只會定義為[布林資料類型](../data-types/boolean-data-type.md)。 Visual Basic 會在評估運算式之前，視需要將每個運算元轉換成 `Boolean` 。 如果您將結果指派給數值型別，Visual Basic 會將它從轉換 `Boolean` 成該型別，如此 `False` 就會變成 `0` 和 `True` 成為 `-1` 。
如需詳細資訊，請參閱布林型別 [轉換](../data-types/boolean-data-type.md#type-conversions)。
  
## <a name="overloading"></a>多載化  

 可以多載 [Or 運算子](or-operator.md) 和 [IsTrue 運算子](istrue-operator.md) ，這表示當運算元具有該類別或結構的型別 *時，類別*或結構可以重新定義其行為。 多載 `Or` 和 `IsTrue` 運算子會影響運算子的行為 `OrElse` 。 如果您的程式碼在多載 `OrElse` 和的類別或結構上使用 `Or` `IsTrue` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `OrElse` 運算子，在兩個運算式上執行邏輯分離。 結果是一個 `Boolean` 值，表示兩個運算式的任一個是否為 true。 如果第一個運算式是 `True` ，則不會評估第二個運算式。  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 上述範例會 `True` 分別產生、 `True` 和的結果 `False` 。 在的計算中 `firstCheck` ，不會評估第二個運算式，因為第一個運算式已經是 `True` 。 但是，第二個運算式會在的計算中進行評估 `secondCheck` 。  
  
## <a name="example"></a>範例  

 下列範例顯示 `If` `Then` 包含兩個程序呼叫的 ... 語句。 如果第一個呼叫傳回 `True` ，則不會呼叫第二個程式。 如果第二個程式執行的重要工作是在程式碼的這個區段執行時一律執行，這可能會產生非預期的結果。  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Or 運算子](or-operator.md)
- [IsTrue 運算子](istrue-operator.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
