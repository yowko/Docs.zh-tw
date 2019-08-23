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
ms.openlocfilehash: 276071fef3632d1a617f177b6fe18026b290103a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917243"
---
# <a name="-operator-visual-basic"></a>\ 運算子 (Visual Basic)
將兩個數字相除並傳回整數結果。  
  
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
 所有數數值型別, 包括不帶正負號的和浮點類型`Decimal`, 以及。  
  
## <a name="result"></a>結果  
 結果是`expression1` `expression2`除以的整數商, 這會捨棄任何餘數, 而且只會保留整數部分。 這就是所謂的*截斷*。  
  
 結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。  
  
 [/運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)會傳回完整商, 這會保留分數部分中的餘數。  
  
## <a name="remarks"></a>備註  
 在執行除法之前, Visual Basic 嘗試將任何浮點數值運算式轉換成`Long`。 如果`Option Strict` 為`On`, 則會發生編譯器錯誤。 如果`Option Strict` <xref:System.OverflowException>是`Off`, 如果值超出[LONG 資料型別](../../../visual-basic/language-reference/data-types/long-data-type.md)的範圍, 就可能發生。 轉換為`Long`時, 也會受限於四*進位*。 如需詳細資訊, 請參閱[類型轉換函數](../../../visual-basic/language-reference/functions/type-conversion-functions.md)中的「小數部分」。  
  
 如果`expression1` 或`expression2`評估為[沒有任何](../../../visual-basic/language-reference/nothing.md)值, 則會將它視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試除數為零  
 如果`expression2`評估為零, 則`\`運算子<xref:System.DivideByZeroException>會擲回例外狀況。 這適用于運算元的所有數值資料類型。  
  
> [!NOTE]
> 運算子可以多載, 這表示當運算元具有該類別或結構的類型時, 類別或結構可以重新定義其行為。 `\` 如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`\`運算子來執行整數除法。 結果是一個整數, 代表兩個運算元的整數商, 餘數會被捨棄。  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 上述範例中的運算式會分別傳回2、3、33和-22 的值。  
  
## <a name="see-also"></a>另請參閱

- [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
