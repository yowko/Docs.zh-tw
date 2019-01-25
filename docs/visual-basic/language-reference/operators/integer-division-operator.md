---
title: '\ 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: ac306038aefba4ca0e0f13fa2945d01c27c0804d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654681"
---
# <a name="-operator-visual-basic"></a>\ 運算子 (Visual Basic)
兩數相除並傳回整數結果。  
  
## <a name="syntax"></a>語法  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要項。 任何數值運算式。  
  
 `expression2`  
 必要項。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  
 所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="result"></a>結果  
 結果是整數商數`expression1`除以`expression2`，它會捨棄任何餘數，並保留只有整數部分。 這就所謂*截斷*。  
  
 將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
 [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整商數，仍會保留其餘部分中的小數部分。  
  
## <a name="remarks"></a>備註  
 然後再執行除法運算，Visual Basic 會嘗試轉換到任何浮點數值運算式`Long`。 如果`Option Strict`是`On`，就會發生編譯器錯誤。 如果`Option Strict`是`Off`，則<xref:System.OverflowException>如果值超出範圍，就可能[Long 資料型別](../../../visual-basic/language-reference/data-types/long-data-type.md)。 轉換成`Long`也受限於*銀行進位*。 如需詳細資訊，請參閱 「 小數點後的組件 」 中[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 如果`expression1`或是`expression2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試的除以零  
 如果`expression2`評估為零，`\`運算子則會擲回<xref:System.DivideByZeroException>例外狀況。 這是所有的數值資料類型的運算元，則為 true。  
  
> [!NOTE]
>  `\`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`\`執行整數除法運算子。 結果是一個整數，表示兩個運算元的整數商數，捨棄餘數。  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 在上述範例中的運算式會分別傳回值 2、 3、 33 與-22。  
  
## <a name="see-also"></a>另請參閱
- [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
