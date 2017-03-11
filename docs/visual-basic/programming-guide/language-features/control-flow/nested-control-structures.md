---
title: "Nested Control Structures (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, control flow"
  - "control structures, nested"
  - "conditional statements, nested"
  - "statements [Visual Basic], control flow"
  - "control flow, nested control statements"
  - "structures, nested control"
  - "nested control statements"
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Nested Control Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以在其他控制陳述式中放置控制陳述式，例如在 `For...Next` 迴圈中放置 `If...Then...Else` 區塊。  在其他控制陳述式中放置控制陳述式的動作稱為「*巢狀化*」\(Nested\)。  
  
## 巢狀層次  
 在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的控制結構可使用巢狀型態，層次數目可依您而定。  這是一種常見的方式，藉由縮排每個結構的主體，使巢狀結構更具可讀性。  整合式開發環境 \(IDE\) 編輯器會自動執行此動作。  
  
 在下列範例中，程序 `sumRows` 將矩陣中每一列的正值項目加總。  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 在前述範例中，第一個 `Next` 陳述式關閉內層 `For` 迴圈 \(Loop\)，而最後一個 `Next` 陳述式關閉外層 `For` 迴圈。  
  
 同樣的，在巢狀 `If` 陳述式中，`End If` 陳述式會自動套用至之前最接近的 `If` 陳述式。  巢狀 `Do` 迴圈也以相似的形式來運作，它是以最內層的 `Loop` 陳述式對應至最內層的 `Do` 陳述式。  
  
> [!NOTE]
>  對於許多控制結構來說，當您按一下關鍵字時，就會將該結構中的所有關鍵字反白顯示。  例如，當您按一下 `If...Then...Else` 建構中的 `If` 時，就會將該建構中 `If`、`Then`、`ElseIf`、`Else` 和  `End If` 的所有執行個體反白顯示。  若要移至下一個或上一個反白顯示的關鍵字，請按 CTRL\+SHIFT\+向下鍵或 CTRL\+SHIFT\+向上鍵。  
  
## 在不同種類的控制結構中使用巢狀結構  
 您可以在其他種類的控制結構內使用巢狀控制結構。  下列範例使用 `For Each` 迴圈中的 `With` 區塊，以及 `With` 區塊中的巢狀 `If` 區塊。  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## 重疊控制結構  
 您不能重疊控制結構。  這表示任何巢狀結構都必須完全包含在下一個最內層結構之內。  例如，下列安排有效之原因是 `For` 迴圈在內層 `With` 區塊結束前結束。  
  
 ![無效巢狀處理示意圖](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.png "NestExampleInvalid")  
無效的 For 和 With 巢狀結構  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會偵測此類重疊的控制結構，並發出編譯時期錯誤的訊息。  
  
## 請參閱  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)