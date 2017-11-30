---
title: "\\ 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38718b109b4b3865238267039908ea1d51d06229
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
 所有數字類型，包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="result"></a>結果  
 結果是整數商數的`expression1`除以`expression2`，它會捨棄任何其餘部分，並保留只有整數部分。 這稱為*截斷*。  
  
 結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱中的 「 整數算術 」 資料表[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
 [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整的商數，其中保留的小數部分中的其餘部分。  
  
## <a name="remarks"></a>備註  
 然後再執行除法運算，Visual Basic 會嘗試轉換到任何浮點數值運算式`Long`。 如果`Option Strict`是`On`，就會發生編譯器錯誤。 如果`Option Strict`是`Off`、<xref:System.OverflowException>值超出範圍時才可以執行[Long 資料型別](../../../visual-basic/language-reference/data-types/long-data-type.md)。 轉換為`Long`也*銀行進位*。 如需詳細資訊，請參閱"小數部分 」 中[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 如果`expression1`或`expression2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試的除以零  
 如果`expression2`判斷值為零，`\`運算子就會擲回<xref:System.DivideByZeroException>例外狀況。 這是所有的數值資料類型的運算元，則為 true。  
  
> [!NOTE]
>  `\`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`\`執行整數除法運算子。 結果為整數，表示兩個運算元的整數商數捨棄餘數。  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 在上述範例中的運算式會分別傳回值 2、 3、 33 與-22。  
  
## <a name="see-also"></a>另請參閱  
 [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
