---
title: "寬鬆委派轉換 (Visual Basic) |Microsoft 文件"
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
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
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
ms.openlocfilehash: c0160165d3df9755481b89570b4cd135b3a990a2
ms.lasthandoff: 03/13/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a>寬鬆委派轉換 (Visual Basic)
寬鬆的委派轉換可讓您將函式和函式指派給委派或處理常式，即使它們的簽章不相同。 因此，委派繫結可與已經達到所允許的方法引動過程的繫結一致。  
  
## <a name="parameters-and-return-type"></a>參數和傳回型別  
 簽章完全相符項目，取代寬鬆的轉換所需符合下列條件時`Option Strict`設為`On`:  
  
-   擴展轉換必須從每個委派參數的資料型別指派函式的對應參數的資料型別或`Sub`。 在下列範例中，委派`Del1`具有一個參數， `Integer`。 參數`m`在指派的 lambda 運算式必須具有擴展轉換為資料類型`Integer`，例如`Long`或`Double`。  
  
     [!code-vb[VbVbalrRelaxedDelegates #&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates #&2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     縮小轉換時，才允許`Option Strict`設為`Off`。  
  
     [!code-vb[VbVbalrRelaxedDelegates #&8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   擴展轉換必須存在於相反的方向，從指定的函式的傳回型別或`Sub`委派的傳回型別。 在下列範例中，每個指派的 lambda 運算式的主體必須評估為資料型別擴展至`Integer`因為傳回型別`del1`是`Integer`。  
  
     [!code-vb[VbVbalrRelaxedDelegates #&3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 如果`Option Strict`設為`Off`、 擴展限制已移除兩個方向。  
  
 [!code-vb[VbVbalrRelaxedDelegates #&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>省略參數規格  
 寬鬆的委派也可讓您完全省略參數規格中指定的方法︰  
  
 [!code-vb[VbVbalrRelaxedDelegates #&5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates #&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 請注意您無法指定一些參數，並省略其他人。  
  
 [!code-vb[VbVbalrRelaxedDelegates #&15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 省略參數的能力是很有幫助的情況下，例如定義事件處理常式，其中牽涉到多個複雜參數。 不會使用一些事件處理常式的引數。 相反地，此處理常式直接存取的控制項的事件註冊，並忽略引數的狀態。 寬鬆的委派可讓您省略此類宣告時沒有模稜兩可的結果中的引數。 在下列範例中，完整指定方法`OnClick`可以重寫為`RelaxedOnClick`。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 範例  
 上一個範例中所用 lambda 運算式，可讓您輕鬆查看的型別關聯性。 不過，相同 relaxations 則可以使用的委派指派`AddressOf`， `Handles`，或`AddHandler`。  
  
 在下列範例中，函式`f1`， `f2`， `f3`，和`f4`所有可指派給`Del1`。  
  
 [!code-vb[VbVbalrRelaxedDelegates #&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates #&7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates #&9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 下列範例是時才有效`Option Strict`設為`Off`。  
  
 [!code-vb[VbVbalrRelaxedDelegates #&14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>卸除函式傳回  
 寬鬆的委派轉換可讓您將函式來指派`Sub`委派，進而有效地忽略函式的傳回值。 不過，您無法指派`Sub`函式委派。 在下列範例中，函式的位址`doubler`指派給`Sub`委派`Del3`。  
  
 [!code-vb[VbVbalrRelaxedDelegates #&10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates #&11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [如何︰ 將傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
