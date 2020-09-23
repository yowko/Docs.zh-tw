---
title: 如何：將程序傳遞至其他程序
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 3a7a653bbf238b50e3c7339da76df0f68ab9b59f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085785"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>如何：在 Visual Basic 中將程序傳遞至其他程序

此範例示範如何使用委派，將程式傳遞至另一個程式。  
  
 委派是一種型別，您可以像 Visual Basic 中的任何其他型別一樣使用它。 `AddressOf`當運算子套用至程式名稱時，運算子會傳回委派物件。  
  
 此範例的程式具有可參考另一個程式（使用運算子取得）的委派參數 `AddressOf` 。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和相符程式  
  
1. 建立名為的委派 `MathOperator` 。  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. `AddNumbers`使用符合這些參數的參數和傳回值建立名為的程式 `MathOperator` ，讓簽章相符。  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. 使用符合的簽章來建立名為的程式 `SubtractNumbers` `MathOperator` 。  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. 建立名為 `DelegateTest` 的程式，該程式會接受委派做為參數。  
  
     此程式可接受或的參考 `AddNumbers` ，因為它們的簽章與簽章 `SubtractNumbers` 相符 `MathOperator` 。  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. 建立名為 `Test` 的程式，該程式會呼叫 `DelegateTest` 一次，並以的委派 `AddNumbers` 做為參數，並再次使用的委派 `SubtractNumbers` 做為參數。  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     當 `Test` 呼叫時，它會先顯示 `AddNumbers` 作用於和的 `5` 結果 `3` ，也就是8。 然後 `SubtractNumbers` 會顯示對和採取行動的結果 `9` `3` ，也就是6。  
  
## <a name="see-also"></a>另請參閱

- [委派](index.md)
- [AddressOf 運算子](../../../language-reference/operators/addressof-operator.md)
- [Delegate 陳述式](../../../language-reference/statements/delegate-statement.md)
- [如何：叫用委派方法](how-to-invoke-a-delegate-method.md)
