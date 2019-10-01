---
title: '>>= 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 08d4e251a96ca387a709319e752351db6825d9e8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701349"
---
# <a name="-operator-visual-basic"></a>> > = 運算子（Visual Basic）
在變數或屬性的值上執行算術右移，並將結果指派回變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 整數類資料類型的變數或屬性（`SByte`、`Byte`、@no__t 2、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`）。  
  
 `amount`  
 必要項。 擴展為 `Integer` 之資料類型的數值運算式。  
  
## <a name="remarks"></a>備註  
 @No__t-0 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 @No__t-0 運算子會先在變數或屬性的值上執行算術右移位。 然後，運算子會將該作業的結果指派回變數或屬性。  
  
 算術移位不是迴圈的，這表示不會在另一端重新進入從結果的一端移位的位。 在算術右移位中，會捨棄超出最右邊位位置的位，而最左邊的位會傳播到左側空出的位位置。 這表示如果 `variableorproperty` 的值為負值，則空出的位置會設定為一個。 如果 `variableorproperty` 是正數，或其資料類型是不帶正負號的類型，則空出的位置會設定為零。  
  
## <a name="overloading"></a>多載化  
 [> > 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)*可以多載，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `>>` 運算子會影響 `>>=` 運算子的行為。 如果您的程式碼在多載 `>>` 的類別或結構上使用 `>>=`，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `>>=` 運算子，將 @no__t 1 變數的位模式右移指定的數量，並將結果指派給該變數。  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [>> 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
