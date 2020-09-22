---
title: AndAlso 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: aff4621b8f415b9441ad1edf537b9b0736892bb8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874853"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso 運算子 (Visual Basic)

在兩個運算式上執行最少運算邏輯結合。  
  
## <a name="syntax"></a>Syntax  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`result`|必要。 任何 `Boolean` 運算式。 結果是 `Boolean` 這兩個運算式的比較結果。|  
|`expression1`|必要。 任何 `Boolean` 運算式。|  
|`expression2`|必要。 任何 `Boolean` 運算式。|  
  
## <a name="remarks"></a>備註  

 如果已編譯的程式碼可以略過一個運算式的評估（視另一個運算式的結果而 *定）* ，則邏輯運算稱為「最少運算」。 如果評估的第一個運算式的結果決定作業的最後結果，則不需要評估第二個運算式，因為它無法變更最後的結果。 如果略過的運算式很複雜，或是牽涉到程序呼叫，則最少運算可以改善效能。  
  
 如果兩個運算式都評估為 `True` ， `result` 就是 `True` 。 下表說明如何 `result` 決定。  
  
|如果 `expression1` 為 |而且 `expression2` 是|的值 `result` 為|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|未評估 () |`False`|  
  
## <a name="data-types"></a>資料類型  

 `AndAlso`運算子只會定義為[布林資料類型](../data-types/boolean-data-type.md)。 Visual Basic 會在評估運算式之前，視需要將每個運算元轉換成 `Boolean` 。 如果您將結果指派給數值型別，Visual Basic 會將它從轉換 `Boolean` 成該型別，如此 `False` 就會變成 `0` 和 `True` 成為 `-1` 。
如需詳細資訊，請參閱布林型別 [轉換](../data-types/boolean-data-type.md#type-conversions)。
  
## <a name="overloading"></a>多載化  

 [And 運算子](and-operator.md)和[IsFalse 運算子](isfalse-operator.md)可以多載，這表示當運算元具有該類別或結構的型別*時，類別*或結構可以重新定義其行為。 多載 `And` 和 `IsFalse` 運算子會影響運算子的行為 `AndAlso` 。 如果您的程式碼在多載 `AndAlso` 和的類別或結構上使用 `And` `IsFalse` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `AndAlso` 運算子，在兩個運算式上執行邏輯結合。 結果是一個 `Boolean` 值，表示整個如何運算式是否為 true。 如果第一個運算式是 `False` ，則不會評估第二個運算式。  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 上述範例會 `True` 分別產生、 `False` 和的結果 `False` 。 在的計算中 `secondCheck` ，不會評估第二個運算式，因為第一個運算式已經是 `False` 。 但是，第二個運算式會在的計算中進行評估 `thirdCheck` 。  
  
## <a name="example"></a>範例  

 下列範例顯示的 `Function` 程式會在陣列的元素之間搜尋指定的值。 如果陣列是空的，或已超過陣列長度， `While` 語句就不會針對搜尋值測試陣列元素。  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [And 運算子](and-operator.md)
- [IsFalse 運算子](isfalse-operator.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
