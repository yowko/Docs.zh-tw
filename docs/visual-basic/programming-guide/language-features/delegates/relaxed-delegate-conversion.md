---
title: 寬鬆委派轉換
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345223"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>寬鬆委派轉換 (Visual Basic)
寬鬆委派轉換可讓您將子函數和函式指派給委派或處理常式，即使其簽章不相同也是一樣。 因此，系結至委派會與已允許方法調用的系結一致。  
  
## <a name="parameters-and-return-type"></a>參數和傳回型別  
 為了取代完全相符的簽章，當 `Option Strict` 設定為 `On`時，寬鬆的轉換需要符合下列條件：  
  
- 擴輾轉換必須從每個委派參數的資料類型，到指派之函數或 `Sub`之對應參數的資料類型。 在下列範例中，委派 `Del1` 有一個參數，也就是 `Integer`。 指派之 lambda 運算式中的參數 `m` 必須具有從 `Integer`擴輾轉換的資料類型，例如 `Long` 或 `Double`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     只有當 `Option Strict` 設定為 `Off`時，才允許縮小轉換。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- 擴輾轉換必須與指派之函式的傳回型別，或 `Sub` 與委派的傳回型別相反的方向存在。 在下列範例中，每個指派的 lambda 運算式的主體都必須評估為擴大為 `Integer` 的資料類型，因為 `del1` 的傳回類型是 `Integer`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 如果 `Option Strict` 設定為 `Off`，則會同時移除這兩個方向的擴展限制。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>省略參數規格  
 寬鬆委派也可以讓您完全省略指派方法中的參數規格：  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 請注意，您不能指定某些參數，並省略其他參數。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 省略參數的功能在定義事件處理常式（其中牽涉到數個複雜參數）的情況下很有説明。 不會使用某些事件處理常式的引數。 相反地，處理常式會直接存取已註冊事件之控制項的狀態，並忽略引數。 寬鬆的委派可讓您在沒有不明確的結果時，省略這類宣告中的引數。 在下列範例中，完整指定的方法 `OnClick` 可以重寫為 `RelaxedOnClick`。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 範例  
 在先前的範例中，會使用 Lambda 運算式，讓型別關聯性變得更容易查看。 不過，使用 `AddressOf`、`Handles`或 `AddHandler`的委派指派，允許相同的 relaxations。  
  
 在下列範例中，`f1`、`f2`、`f3`和 `f4` 函數都可以指派給 `Del1`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 只有當 `Option Strict` 設定為 `Off`時，下列範例才有效。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>卸載函式傳回  
 寬鬆委派轉換可讓您將函式指派給 `Sub` 委派，以有效地忽略函數的傳回值。 不過，您無法將 `Sub` 指派給函數委派。 在下列範例中，會將函數 `doubler` 的位址指派給 `Sub` 委派 `Del3`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>請參閱

- [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [如何：在 Visual Basic 中將程序傳遞至其他程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
