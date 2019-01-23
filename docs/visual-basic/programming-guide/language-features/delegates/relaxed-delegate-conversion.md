---
title: 寬鬆委派轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: e2838b6473b8c00927073a530b4b49870fcfa9c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600373"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>寬鬆委派轉換 (Visual Basic)
寬鬆的委派轉換，可讓您將 sub 和函式指派給委派或處理常式，即使它們的簽章並不相同。 因此，委派繫結會變成一致與繫結中允許的方法引動過程。  
  
## <a name="parameters-and-return-type"></a>參數和傳回類型  
 簽章完全相符項目，取代寬鬆的轉換必須符合下列條件時`Option Strict`設為`On`:  
  
-   擴展轉換至指派的函式的對應參數的資料類型時，必須從每個委派參數的資料型別或`Sub`。 在下列範例中，委派`Del1`有一個參數， `Integer`。 參數`m`中指派的 lambda 運算式必須具有擴展轉換的資料類型`Integer`，例如`Long`或`Double`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     縮小轉換允許時，才`Option Strict`設為`Off`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   擴展轉換必須存在於相反的方向，從指派的函式的傳回型別或`Sub`委派的傳回型別。 在下列範例中，每個指派的 lambda 運算式的主體必須評估為資料類型可擴展成`Integer`的傳回類型，因為`del1`是`Integer`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 如果`Option Strict`設為`Off`、 擴展限制兩個方向中已移除。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>省略參數規格  
 寬鬆的委派也可讓您完全略過指派方法中的參數規格：  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 請注意，您無法指定一些參數並省略其他人。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 省略參數的能力是很有幫助的情況下，例如定義事件處理常式，其中牽涉到多個複雜參數。 不會使用一些事件處理常式的引數。 相反地，處理常式直接存取的控制項的事件註冊，並會忽略引數的狀態。 寬鬆的委派可讓您略過這類宣告時沒有模稜兩可的結果中的引數。 在下列範例中，完整指定的方法`OnClick`可以重寫為`RelaxedOnClick`。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 範例  
 前一個範例中所用 lambda 運算式，以方便看到的類型關聯性。 不過，允許使用的委派指派相同 relaxations `AddressOf`， `Handles`，或`AddHandler`。  
  
 在下列範例中，函式`f1`， `f2`， `f3`，以及`f4`所有可指派給`Del1`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 下列範例是時才有效`Option Strict`設為`Off`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>卸除函數會傳回  
 寬鬆的委派轉換可讓您指派的函式`Sub`委派，有效地略過函式的傳回值。 不過，您無法指派`Sub`函式委派。 在下列範例中，函式的位址`doubler`指派給`Sub`委派`Del3`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>另請參閱
- [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [如何：傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
