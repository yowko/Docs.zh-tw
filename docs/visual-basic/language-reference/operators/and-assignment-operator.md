---
title: '&amp;= 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 9b77c44aa77afd59e36e1d21451205d3929ef527
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874878"
---
# <a name="amp-operator-visual-basic"></a>&amp;= 運算子 (Visual Basic) 

將 `String` 運算式串連至 `String` 變數或屬性，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 任何 `String` 變數或屬性。  
  
 `expression`  
 必要。 任何 `String` 運算式。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `&=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。 運算子會將 `&=` `String` 其右邊的運算式串連至 `String` 其左邊的變數或屬性，並將結果指派給其左邊的變數或屬性。  
  
## <a name="overloading"></a>多載化  

 您可以多載 [& 運算子](concatenation-operator.md) ，這表示當運算元的類型為該類別或結構 *時，類別*或結構可以重新定義其行為。 多載 `&` 運算子會影響運算子的行為 `&=` 。 如果您的程式碼在多載的 `&=` 類別或結構上使用 `&` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `&=` 運算子來串連兩個 `String` 變數，並將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [& 運算子](concatenation-operator.md)
- [+ = 運算子](addition-assignment-operator.md)
- [指派運算子](assignment-operators.md)
- [串連運算子](concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
