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
ms.openlocfilehash: ff7cbb02a9a10dbe11450491e93fd85fd77b44ba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370657"
---
# <a name="-operator-visual-basic"></a>\<\<= 運算子（Visual Basic）
在變數或屬性的值上執行算術左移位，並將結果指派回變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 整數類資料類型的變數或屬性（ `SByte` 、 `Byte` 、、、 `Short` `UShort` `Integer` 、 `UInteger` 、 `Long` 或 `ULong` ）。  
  
 `amount`  
 必要。 擴展至之資料類型的數值運算式 `Integer` 。  
  
## <a name="remarks"></a>備註  
 運算子左邊的元素 `<<=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../modifiers/readonly.md)。  
  
 `<<=`運算子會先在變數或屬性的值上執行算術左移位。 然後，運算子會將該作業的結果指派回該變數或屬性。  
  
 算術移位不是迴圈的，這表示不會在另一端重新進入從結果的一端移位的位。 在算術左移位中，會捨棄超出結果資料類型範圍的位，而且右邊空出的位位置會設定為零。  
  
## <a name="overloading"></a>多載化  
 [<< 運算子](left-shift-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `<<` 運算子會影響運算子的行為 `<<=` 。 如果您的程式碼在多載 `<<=` 的類別或結構上使用 `<<` ，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `<<=` 運算子，將變數的位模式 `Integer` 向左移位指定的數量，並將結果指派給變數。  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>另請參閱

- [<< 運算子](left-shift-operator.md)
- [指派運算子](assignment-operators.md)
- [位元移位運算子](bit-shift-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
