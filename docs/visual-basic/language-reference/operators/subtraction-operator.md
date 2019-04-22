---
title: '- 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 1a5c47a2f1bc8a8b9e1b0263b90006a0e58e17bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830665"
---
# <a name="--operator-visual-basic"></a>- 運算子 (Visual Basic)
傳回兩個數值運算式或負數值運算式的值之間的差異。  
  
## <a name="syntax"></a>語法  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要項。 任何數值運算式。  
  
 `expression2`  
 除非`–`運算子會計算為負數值。 任何數值運算式。  
  
## <a name="result"></a>結果  
 結果是之間的差異`expression1`並`expression2`，或已變換正負號的值`expression1`。  
  
 將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="supported-types"></a>支援的型別  
 所有數值類型。 這包括的不帶正負號和浮點類型和`Decimal`。  
  
## <a name="remarks"></a>備註  
 在先前所示的語法中顯示的第一個使用方式`–`操作員*二進位*算術減法運算子的兩個數值運算式之間的差異。  
  
 在先前所示的語法中顯示的第二個使用方式`–`操作員*一元*負運算子的運算式的負值。 在這種情況下，否定包含反轉的正負號`expression1`讓，則結果為正數如果`expression1`為負數。  
  
 如果任一個運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，則`–`運算子會將它視為零。  
  
> [!NOTE]
>  `–`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`–`運算子來計算並傳回兩個數字，之間的差異，然後要變換正負號數字。  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 遵循這些陳述式中，執行`binaryResult`包含 124.45 和`unaryResult`包含 –334.90。  
  
## <a name="see-also"></a>另請參閱

- [-= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
