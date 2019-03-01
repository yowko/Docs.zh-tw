---
title: HOW TO：傳遞至另一個程序，在 Visual Basic 中的程序
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: e9e6165414db00e7d7182e204d86d23debfbf4f6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967733"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>HOW TO：傳遞至另一個程序，在 Visual Basic 中的程序
此範例示範如何使用委派傳遞至其他程序的程序。  
  
 委派是您可以使用 Visual Basic 中的其他任何類型的類型。 `AddressOf`運算子會傳回委派物件時套用至程序名稱。  
  
 這個範例包含具有 delegate 參數可接受的另一個程序，以取得參考的程序`AddressOf`運算子。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和比對程序  
  
1.  建立名為委派`MathOperator`。  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2.  建立名為程序`AddNumbers`使用參數和傳回值，符合`MathOperator`，如此一來，簽章相符。  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3.  建立名為程序`SubtractNumbers`簽章符合`MathOperator`。  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4.  建立名為程序`DelegateTest`會做為參數的委派。  
  
     此程序可接受的參考`AddNumbers`或是`SubtractNumbers`，因為它們的簽章相符`MathOperator`簽章。  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5.  建立名為程序`Test`它會呼叫`DelegateTest`另一次使用的委派`AddNumbers`做為參數，並再次使用的委派`SubtractNumbers`做為參數。  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     當`Test`是呼叫，它顯示的第一次的結果`AddNumbers`處理`5`和`3`，這是 8。 結果`SubtractNumbers`作`9`和`3`隨即顯示，這是 6。  
  
## <a name="see-also"></a>另請參閱
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [如何：叫用委派方法](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
