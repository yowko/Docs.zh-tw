---
title: <<= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 72fc842002586a4d5e48bc39b5c785fc6a9e9451
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866905"
---
# <a name="-operator-visual-basic"></a>\<\<= 運算子 (Visual Basic) 

在變數或屬性的值上執行算術左移位，並將結果指派回變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 整數類資料類型的變數或屬性 (、、、、、、 `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 或 `ULong`) 。  
  
 `amount`  
 必要。 擴大至之資料類型的數值運算式 `Integer` 。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `<<=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 `<<=`運算子會先在變數或屬性的值上執行算術左移位。 然後，運算子會將該操作的結果指派回該變數或屬性。  
  
 算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。 在算術左移位中，會捨棄超出結果資料類型範圍的位，而且右邊的位位置會設定為零。  
  
## <a name="overloading"></a>多載化  

 您可以多載 [<< 運算子](left-shift-operator.md) ，這表示當運算元的類型為該類別或結構 *時，類別*或結構可以重新定義其行為。 多載 `<<` 運算子會影響運算子的行為 `<<=` 。 如果您的程式碼在多載的 `<<=` 類別或結構上使用 `<<` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用運算子，將 `<<=` 變數的位模式向 `Integer` 左移位指定的數量，並將結果指派給變數。  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>另請參閱

- [<< 運算子](left-shift-operator.md)
- [指派運算子](assignment-operators.md)
- [位元移位運算子](bit-shift-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
