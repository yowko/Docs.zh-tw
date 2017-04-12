---
title: "如何︰ 計算數值 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d844e2af3892d897125e21d3fd7047a8b295d10a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>如何：計算數值 (Visual Basic)
您可以計算數字的值，透過使用數值運算式。 A*數值運算式*運算式包含常值、 常數和變數表示數字的值，並處理那些值的運算子。  
  
## <a name="calculating-numeric-values"></a>計算數值  
  
#### <a name="to-calculate-a-numeric-value"></a>若要計算數值  
  
-   結合的數值運算式的一個或多個數值常值、 常數和變數。 下列範例顯示一些有效的數值運算式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行顯示常值、 常數和變數。 每個本身構成有效的數值運算式。 最後一行會顯示兩個常值的變數的組合。  
  
     請注意，數值的運算式不會構成完整[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式本身。 您必須使用運算式做為完整的陳述式的一部分。  
  
#### <a name="to-store-a-numeric-value"></a>若要儲存數值  
  
-   您可以使用在指派陳述式來指派給變數，數值運算式所代表的值，如下列範例所示。  
  
     [!code-vb[VbVbalrOperators #&82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     在上述範例中，「 等於 」 運算子的右邊顯示運算式的值 (`=`) 指派給變數`j`運算子的左邊，`j`評估為 276。  
  
     如需詳細資訊，請參閱[陳述式](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多個運算子  
 如果數值的運算式包含多個運算子，它們的評估的順序取決於運算子優先順序的規則。 若要覆寫運算子優先順序規則，您運算式括號括住，如上述範例中;會先評估括住的運算式。  
  
#### <a name="to-override-normal-operator-precedence"></a>若要覆寫一般運算子優先順序  
  
-   您可以使用括號括住您想要先執行的作業。 下列範例顯示具有相同的運算元和運算子的兩個不同的結果。  
  
     [!code-vb[VbVbalrOperators #&83;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     在上述範例中，計算`j`執行加法運算子 (`+`) 第一個因為前後的括號`(67 + i)`覆寫一般優先順序，與指派給值`j`為 276 (4 次 69)。 其計算方式`k`運算子會執行其一般優先順序 (`*`之前`+`)，並指派給值`k`為 270 （268 加 2）。  
  
     如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另請參閱  
 [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [值的比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)   
 [在 Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
