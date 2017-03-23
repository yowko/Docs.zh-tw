---
title: "決策結構 (Visual Basic) |Microsoft 文件"
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
- statements [Visual Basic], control flow
- If statement, decision structures
- If statement, If...Then...Else
- control flow, decision structures
- decision structures
- conditional statements, decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c69b487322dc75ae8d54f42c1c62f8f5cc35757d
ms.lasthandoff: 03/13/2017

---
# <a name="decision-structures-visual-basic"></a>決策結構 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可讓您測試條件，並執行不同的作業，根據該測試的結果。 您可以測試條件為 true 或 false，針對各種不同值的運算式，或當您執行一系列的陳述式時，產生的各種例外狀況。  
  
 下圖顯示測試條件為 true，會採用不同的動作，取決於為 true 或 false 的決策結構。  
  
 ![If 的流程圖...然後...其他建構](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
條件為 true，而且是 false 時，採取不同動作  
  
## <a name="ifthenelse-construction"></a>如果...然後...其他建構  
 `If...Then...Else`語法結構，可讓您測試一個或多個條件，並執行一或多個陳述式，根據每個條件。 您可以測試條件，並以下列方式採取動作︰  
  
-   如果條件為，執行一或多個陳述式`True`  
  
-   如果條件為，執行一或多個陳述式`False`  
  
-   執行某些陳述式，如果條件為`True`和其他人是否`False`  
  
-   如果先前的條件是，測試其他狀況`False`  
  
 提供所有這些可能性的控制結構是[如果...然後...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。 如果您有一個測試和執行一個陳述式，您可以使用單行版本。 如果您有一組更複雜的條件和動作，您可以使用多行版本。  
  
## <a name="selectcase-construction"></a>選取 [...]Case 建構  
 `Select...Case`建構可讓您評估運算式一次，並執行不同的陳述式，根據不同的可能值。 如需詳細資訊，請參閱[選取...Case 陳述式](../../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## <a name="trycatchfinally-construction"></a>請嘗試...Catch...最後的建構  
 `Try...Catch...Finally`語法結構，可讓您執行一組保留控制項，如果任何一個陳述式會導致例外狀況的環境下的陳述式。 您可以採取不同的例外狀況的不同動作。 您可以選擇性地指定一段程式碼執行之前結束整個`Try...Catch...Finally`建構，不論執行的動作。 如需詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  許多控制項結構，當您按一下關鍵字，所有的關鍵字，在結構中反白顯示。 比方說，當您按一下`If`中`If...Then...Else`建構，而所有執行個體的`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。 若要移至下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。  
  
## <a name="see-also"></a>另請參閱  
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [巢狀的控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [If 運算子](../../../../visual-basic/language-reference/operators/if-operator.md)
