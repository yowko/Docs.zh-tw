---
title: "/ 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 71b4f64f6deeb334412c87131ccd9480620f284f
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>/ 運算子 (Visual Basic)
將兩個數值相除，傳回浮點結果。  
  
## <a name="syntax"></a>語法  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要項。 任何數值運算式。  
  
 `expression2`  
 必要項。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  
 所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="result"></a>結果  
 結果是完整的商數`expression1`除以`expression2`，包括任何其餘部分。  
  
 [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回整數商數，這會卸除其餘部分。  
  
## <a name="remarks"></a>備註  
 結果的資料類型取決於運算元的類型。 下表顯示如何決定結果的資料型別。  
  
|運算元資料類型|結果資料類型|  
|------------------------|----------------------|  
|這兩個運算式都是整數類資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)， [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|一個運算式[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)資料類型和其他不是[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|一個運算式[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料類型和其他不是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|任何一個運算式[雙](../../../visual-basic/language-reference/data-types/double-data-type.md)資料類型|`Double`|  
  
 任何整數的數值運算式執行除法之前，會擴展為`Double`。 如果結果為整數類資料型別時，Visual Basic 會嘗試將轉換的結果`Double`為該型別。 如果結果不符合該類型，這可以擲回例外狀況。 這個說明網頁，特別是，請參閱 」 嘗試以零為除數 」。  
  
 如果`expression1`或`expression2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試的除以零  
 如果`expression2`判斷值為零，`/`運算子具有不同行為不同的運算元資料類型。 下表顯示可能的行為。  
  
|運算元資料類型|行為如果`expression2`為零|  
|------------------------|---------------------------------------|  
|浮點數 (`Single`或`Double`)|傳回無限大 (<xref:System.Double.PositiveInfinity>或<xref:System.Double.NegativeInfinity>)，或<xref:System.Double.NaN>（不是數字） 如果`expression1`也是零</xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity>|  
|`Decimal`|擲回<xref:System.DivideByZeroException></xref:System.DivideByZeroException>|  
|整數 （帶正負號或不帶正負號）|嘗試轉換回整數類資料類型會擲回<xref:System.OverflowException>無法接受整數類資料類型，所以<xref:System.Double.PositiveInfinity>， <xref:System.Double.NegativeInfinity>，或<xref:System.Double.NaN></xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></xref:System.OverflowException>|  
  
> [!NOTE]
>  `/`運算子可以*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用此運算子在這種類別或結構，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`/`來執行浮點除法運算子。 結果是兩個運算元的商。  
  
 [!code-vb[VbVbalrOperators #&16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 在上述範例中的運算式會傳回 2.5 和 3.333333 的值。 請注意結果一定是浮點 (`Double`)，即使這兩個運算元都是整數常數。  
  
## <a name="see-also"></a>另請參閱  
 [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

