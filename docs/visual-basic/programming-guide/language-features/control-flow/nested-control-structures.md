---
title: 巢狀控制結構
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266920"
---
# <a name="nested-control-structures-visual-basic"></a>巢狀控制結構 (Visual Basic)
您可以將控制語句放置在其他控制語句中，例如`If...Then...Else``For...Next`迴圈中的塊。 放置在另一個控制語句中的控制語句*表示嵌套。*  
  
## <a name="nesting-levels"></a>嵌套級別  
 Visual Basic 中的控制項結構可以嵌套到所需的盡可能多的級別。 通常的做法是通過縮進每個結構的主體來使嵌套結構更具可讀性。 整合式開發環境 （IDE） 編輯器會自動這樣做。  
  
 在下面的示例中，該過程`sumRows`將矩陣每行的正元素相加。  
  
```vb
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
  
 在前面的示例中，第一個`Next`語句關閉內部`For`迴圈，最後一`Next`個語句關閉外部`For`迴圈。  
  
 同樣，在嵌套`If`語句中，`End If`語句會自動應用於最近的先前`If`語句。 嵌套`Do`迴圈的工作方式類似，其中最`Loop`裡面的語句與最`Do`裡面的語句匹配。  
  
> [!NOTE]
> 對於許多控制項結構，當您按一下關鍵字時，結構中的所有關鍵字都會突出顯示。 例如`If`，當您在`If...Then...Else`構造中按一下時，構造`If``Then``ElseIf``Else``End If`中的所有實例將突出顯示。 要移動到下一個或上一個突出顯示的關鍵字，請按 CTRL_SHIFT_向下箭頭或 CTRL_SHIFT_UP 箭頭。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>嵌套不同類型的控制結構  
 可以將一種控制結構嵌套在另一種類型中。 下面的`With`示例使用`For Each`迴圈中的塊和塊內的`If``With`嵌套塊。  
  
```vb
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
  
## <a name="overlapping-control-structures"></a>重疊的控制結構  
 不能重疊控制結構。 這意味著任何嵌套結構都必須完全包含在下一個最內部結構中。 例如，以下排列無效，`For`因為迴圈在內部`With`塊終止之前終止。  
  
 ![顯示無效嵌套示例的圖表。](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Visual Basic 編譯器檢測此類重疊的控制結構，併發出編譯時錯誤信號。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
