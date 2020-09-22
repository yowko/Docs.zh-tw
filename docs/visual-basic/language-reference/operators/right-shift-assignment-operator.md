---
title: '>>= 運算子'
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
ms.openlocfilehash: a1c2331791644155504183d3cf5767470a3bf17b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873352"
---
# <a name="-operator-visual-basic"></a>>>= 運算子 (Visual Basic) 

在變數或屬性的值上執行算術右移位，並將結果指派回變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 整數類資料類型的變數或屬性 (、、、、、、 `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 或 `ULong`) 。  
  
 `amount`  
 必要。 擴大至之資料類型的數值運算式 `Integer` 。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `>>=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 `>>=`運算子會先在變數或屬性的值上執行算術右移位。 然後，運算子會將該作業的結果指派回變數或屬性。  
  
 算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。 在算術右移位中，會捨棄超過最右邊位位置的位，並將最左邊的位傳播到左側空出的位位置。 這表示如果的 `variableorproperty` 值為負值，空出的位置會設定為1。 如果 `variableorproperty` 是正數，或其資料類型為不帶正負號的類型，空出的位置會設定為零。  
  
## <a name="overloading"></a>多載化  

 您可以多載 [>> 運算子](right-shift-operator.md) ，這表示當運算元的類型為該類別或結構 *時，類別*或結構可以重新定義其行為。 多載 `>>` 運算子會影響運算子的行為 `>>=` 。 如果您的程式碼在多載的 `>>=` 類別或結構上使用 `>>` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用運算子，將 `>>=` 變數的位模式向 `Integer` 右移動指定的數量，並將結果指派給變數。  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [>> 運算子](right-shift-operator.md)
- [指派運算子](assignment-operators.md)
- [位元移位運算子](bit-shift-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
