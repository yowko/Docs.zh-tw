---
title: 如何：將程式傳遞至另一個進程
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345253"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>如何：在 Visual Basic 中將程序傳遞至其他程序
這個範例會示範如何使用委派將程式傳遞至另一個程式。  
  
 委派是一種類型，您可以像 Visual Basic 中的任何其他類型一樣使用它。 `AddressOf` 運算子套用至程式名稱時，會傳回委派物件。  
  
 這個範例有一個程式，其中包含可參考另一個程式（使用 `AddressOf` 運算子取得）的委派參數。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和比對程式  
  
1. 建立名為 `MathOperator`的委派。  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. 建立名為 `AddNumbers` 的程式，其中包含符合 `MathOperator`的參數和傳回值，使簽章相符。  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. 使用符合 `MathOperator`的簽章，建立名為 `SubtractNumbers` 的程式。  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. 建立一個名為 `DelegateTest` 的程式，接受委派做為參數。  
  
     此程式可以接受 `AddNumbers` 或 `SubtractNumbers`的參考，因為其簽章符合 `MathOperator` 簽章。  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. 建立名為 `Test` 的程式，其會使用做為參數的 `AddNumbers` 委派呼叫 `DelegateTest` 一次，並使用 `SubtractNumbers` 的委派做為參數。  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     呼叫 `Test` 時，它會先顯示 `AddNumbers` 作用於 `5` 和 `3`（也就是8）的結果。 然後會顯示 `SubtractNumbers` 作用於 `9` 和 `3` 的結果，也就是6。  
  
## <a name="see-also"></a>請參閱

- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [如何：叫用委派方法](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
