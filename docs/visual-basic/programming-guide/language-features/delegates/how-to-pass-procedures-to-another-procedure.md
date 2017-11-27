---
title: "如何：在 Visual Basic 中將程序傳遞至其他程序"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>如何：在 Visual Basic 中將程序傳遞至其他程序
這個範例示範如何使用委派來將傳遞至另一個程序的程序。  
  
 委派是您可以使用中的其他任何類型的型別[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。 `AddressOf`運算子會傳回委派物件時套用至程序名稱。  
  
 這個範例有與委派參數可接受另一個程序，取得與參考的程序`AddressOf`運算子。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和比對程序  
  
1.  建立名為委派`MathOperator`。  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  建立名為程序`AddNumbers`使用參數和傳回值，符合`MathOperator`，如此一來，簽章相符。  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  建立名為程序`SubtractNumbers`的簽章來符合`MathOperator`。  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  建立名為程序`DelegateTest`接受委派做為參數。  
  
     此程序可接受的參考`AddNumbers`或`SubtractNumbers`，因為它們的簽章相符`MathOperator`簽章。  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  建立名為程序`Test`呼叫`DelegateTest`另一次使用的委派`AddNumbers`做為參數，再使用的委派`SubtractNumbers`做為參數。  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     當`Test`是呼叫，它顯示的第一次的結果`AddNumbers`做角色上`5`和`3`，這是 8。 結果`SubtractNumbers`代表`9`和`3`隨即顯示，這是 6。  
  
## <a name="see-also"></a>另請參閱  
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [如何：叫用委派方法](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
