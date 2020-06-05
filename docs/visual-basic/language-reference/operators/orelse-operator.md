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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401403"
---
# <a name="orelse-operator-visual-basic"></a>OrElse 運算子 (Visual Basic)
在兩個運算式上執行最少運算（含）運算邏輯分離。  
  
## <a name="syntax"></a>語法  
  
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
 *如果已*編譯的程式碼可以根據另一個運算式的結果，略過一個運算式的評估，則邏輯作業稱為「最少運算」。 如果第一個運算式評估的結果決定了作業的最後結果，就不需要評估第二個運算式，因為它無法變更最終的結果。 如果略過的運算式很複雜，或如果它牽涉到程序呼叫，則最少運算可以改善效能。  
  
 如果任一個或兩個運算式都評估為 `True` ， `result` 則為 `True` 。 下表說明如何 `result` 決定。  
  
|如果 `expression1` 為 |和 `expression2` 為|的值 `result` 為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|（未評估）|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>資料類型  
 `OrElse`運算子只會針對[布林資料類型](../data-types/boolean-data-type.md)來定義。 Visual Basic 在評估運算式之前，會視需要將每個運算元轉換成 `Boolean` 。 如果您將結果指派給數數值型別，Visual Basic 會將它從轉換 `Boolean` 成該類型， `False` 使變成 `0` ，而成為 `True` `-1` 。
如需詳細資訊，請參閱布林型別[轉換](../data-types/boolean-data-type.md#type-conversions)。
  
## <a name="overloading"></a>多載化  
 [Or 運算子](or-operator.md)和[IsTrue 運算子](istrue-operator.md)可以多載，這表示當運算元具有該類別或結構的類型*時，類別*或結構可以重新定義其行為。 多載 `Or` 和 `IsTrue` 運算子會影響運算子的行為 `OrElse` 。 如果您的程式碼在多載 `OrElse` 和的類別或結構上使用 `Or` `IsTrue` ，請確定您瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `OrElse` 運算子，在兩個運算式上執行邏輯分離。 結果會是一個 `Boolean` 值，表示兩個運算式的其中一個是否為 true。 如果第一個運算式為 `True` ，則不會評估第二個。  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 上述範例會 `True` 分別產生、 `True` 和的結果 `False` 。 在的計算中 `firstCheck` ，因為第一個運算式已經是，所以不會進行評估 `True` 。 不過，會在的計算中評估第二個運算式 `secondCheck` 。  
  
## <a name="example"></a>範例  
 下列範例顯示 `If` `Then` 包含兩個程序呼叫的 ... 語句。 如果第一次呼叫傳回 `True` ，則不會呼叫第二個程式。 如果第二個程式執行程式碼的這個區段時一定要執行的重要工作，這可能會產生非預期的結果。  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Or 運算子](or-operator.md)
- [IsTrue 運算子](istrue-operator.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
