---
title: "^ 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^ 運算子 (Visual Basic)
數目自乘至另一個數字乘冪。  
  
## <a name="syntax"></a>語法  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>組件  
 `number`  
 必要項。 任何數值運算式。  
  
 `exponent`  
 必要項。 任何數值運算式。  
  
## <a name="result"></a>結果  
 結果是`number`乘冪`exponent`，一律為`Double`值。  
  
## <a name="supported-types"></a>支援的型別  
 `Double`. 任何其他類型的運算元都轉換成`Double`。  
  
## <a name="remarks"></a>備註  
 Visual Basic 一律會執行中的乘冪[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)。  
  
 值`exponent`可以是分數，負數，或兩者。  
  
 在單一運算式中，執行一個以上的乘冪時`^`運算子時發現從左到右評估。  
  
> [!NOTE]
>  `^`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`^`運算子引發的數字的指數乘冪。 結果會是第一個運算元的乘冪的第二個。  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 上述範例會產生下列結果：  
  
 `exp1`設為 4 (平方 2)。  
  
 `exp2`設定為 19683 (3 立方，然後該值立方)。  
  
 `exp3`設定為-125 (立方-5)。  
  
 `exp4`設定為 625 (第四個的乘冪-5)。  
  
 `exp5`設定為 2 （8 個的立方根）。  
  
 `exp6`設定為 0.5 (除以 8 的立方根 1.0)。  
  
 請注意在上述範例中的運算式中的括弧的重要性。 因為*運算子優先順序*，通常會先執行 Visual Basic`^`運算子，再執行其他的即使是一元`–`運算子。 如果`exp4`和`exp6`已計算沒有括號，則可能產生下列結果：  
  
 `exp4 = -5 ^ 4`會計算為 (第四個的乘冪 5)，這會導致-625。  
  
 `exp6 = 8 ^ -1.0 / 3.0`將計算成 (8 – 1 乘冪或 0.125) 除以可得到 0.041666666666666666666666666666667 3.0。  
  
## <a name="see-also"></a>另請參閱  
 [^= 運算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
