---
title: "Relaxed Delegate Conversion (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "relaxed delegate conversion [Visual Basic]"
  - "delegates [Visual Basic], relaxed conversion"
  - "conversions, relaxed delegate"
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Relaxed Delegate Conversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

即使在簽章不同的情況下，寬鬆委派轉換仍可讓您將子函數和函式指派給委派或處理常式。因此，委派的繫結就會與方法引動中允許的繫結一致。  
  
## 參數和傳回型別  
 寬鬆轉換不需要簽章完全相符，而要求在 `Option Strict` 設定為 `On` 時符合下列條件：  
  
-   擴展轉換必須存在，方向是從每個委派參數的資料型別到指派之函式或 `Sub` 相對應參數的資料型別。  在下列範例中，委派 `Del1` 有一個 `Integer` 參數。  所指派之 Lambda 運算式中的參數 `m`，其資料型別必須可從 `Integer` \(例如 `Long` 或 `Double`\) 執行擴展轉換。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#2)]  
  
     只有在 `Option Strict` 設定為 `Off` 時，才允許縮小轉換。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module2.vb#8)]  
  
-   反方向的擴展轉換必須存在，方向是從指派之函式或 `Sub` 的傳回型別到委派的傳回型別。  在下列範例中，因為 `del1` 的傳回型別為 `Integer`，每個指派之 Lambda 運算式的主體都必須評估為擴展至 `Integer` 的資料型別。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#3)]  
  
 如果 `Option Strict` 設定為 `Off`，則會移除雙向擴展限制。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module2.vb#4)]  
  
## 省略參數規格  
 寬鬆委派也可讓您在指派的方法中，完全省略參數規格：  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#6)]  
  
 請注意，您不能指定部分參數而省略其他參數。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#15)]  
  
 在定義事件處理常式這類牽涉到多個複雜參數的情況下，省略參數將很有幫助。  有時不會用到某些事件處理常式的引數，  而是處理常式直接存取註冊事件之控制項的狀態，並忽略引數。  寬鬆委派可讓您在不會造成模稜兩可 \(Ambiguity\) 的情況下，於此類宣告中省略引數。  在下列範例中，完整指定的方法 `OnClick` 可以重新撰寫為 `RelaxedOnClick`。  
  
```vb#  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## AddressOf 範例  
 透過上述範例中 Lambda 運算式的用法，您可以輕易看出型別關聯性。  不過，您也可以針對使用 `AddressOf`、`Handles` 或 `AddHandler` 的委派指派，使用相同的寬鬆原則。  
  
 在下列範例中，`f1`、`f2`、`f3` 和 `f4` 函式都可指派至 `Del1`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#9)]  
  
 下列範例只有在 `Option Strict` 設定為 `Off` 時才有效。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module2.vb#14)]  
  
## 置放函式傳回  
 寬鬆委派轉換可讓您將函式指派給 `Sub` 委派，進而有效地忽略函式的傳回值。  不過，您無法將 `Sub` 指派給函式委派。  在下列範例中，`doubler` 函式的位址已指派給 `Sub` 委派 `Del3`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/visualbasic/VbVbalrRelaxedDelegates/Module1.vb#11)]  
  
## 請參閱  
 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)