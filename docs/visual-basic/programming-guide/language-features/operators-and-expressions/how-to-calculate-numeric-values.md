---
title: 如何：計算數值 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 322e2c9fe7f668e08a42cd707c5d81090aca627c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>如何：計算數值 (Visual Basic)
您可以計算數字的值，透過使用數值運算式。 A*數值運算式*是運算式包含常值、 常數和變數代表數字的值，並執行以這些值的運算子。  
  
## <a name="calculating-numeric-values"></a>計算數值  
  
#### <a name="to-calculate-a-numeric-value"></a>若要計算數字的值  
  
-   結合的數值運算式的一或多個數值常值、 常數和變數。 下列範例顯示一些有效的數值運算式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三個行顯示常值、 常數和變數。 每個本身構成有效的數值運算式。 最後一行示範具有兩個常值的變數的組合。  
  
     請注意數值的運算式不會構成完整的 Visual Basic 陳述式本身。 您必須使用運算式做為完整的陳述式的一部分。  
  
#### <a name="to-store-a-numeric-value"></a>若要儲存數字的值  
  
-   您可以使用在指派陳述式指派值給變數，數值運算式所表示，如下列範例所示。  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     在上述範例中，「 等於 」 運算子右邊的運算式值 (`=`) 指派給變數`j`運算子左側讓`j`276 評估結果。  
  
     如需詳細資訊，請參閱[陳述式](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多個運算子  
 如果數字的運算式包含多個運算子，它們的評估的順序取決於運算子優先順序的規則。 若要覆寫的運算子優先順序的規則，您括住運算式括號，如同上述範例中。會先評估括住的運算式。  
  
#### <a name="to-override-normal-operator-precedence"></a>若要覆寫一般運算子優先順序  
  
-   您可以使用括號括住您想要先執行的作業。 下列範例會示範兩個不同的結果，具有相同的運算元和運算子。  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     在上述範例中，計算`j`執行加法運算子 (`+`) 第一個因為前後的括號`(67 + i)`一般優先順序，以及指派給的值會覆寫`j`是 276 (4 次 69)。 計算`k`執行其一般優先順序的運算子 (`*`之前`+`)，並指派給的值`k`為 270 （268 加上 2）。  
  
     如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另請參閱  
 [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)  
 [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
