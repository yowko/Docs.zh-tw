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
ms.openlocfilehash: 539ad639320615c1e53176fe47e5468864aa21d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414385"
---
# <a name="nested-control-structures-visual-basic"></a>巢狀控制結構 (Visual Basic)
您可以將控制語句放在其他控制語句中，例如 `If...Then...Else` 迴圈內的區塊 `For...Next` 。 放在另一個控制項語句內的控制語句稱為「已*嵌套*」。  
  
## <a name="nesting-levels"></a>嵌套層級  
 Visual Basic 中的控制結構可以嵌套成您想要的多個層級。 一般做法是將每個結構的主體縮排，使其更容易閱讀。 整合式開發環境（IDE）編輯器會自動執行此工作。  
  
 在下列範例中，程式會 `sumRows` 將矩陣的每個資料列的正元素加在一起。  
  
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
  
 在上述範例中，第一個 `Next` 語句會關閉內部 `For` 迴圈，而最後一個 `Next` 語句會關閉外部 `For` 迴圈。  
  
 同樣地，在 nested `If` 語句中， `End If` 語句會自動套用至最接近的先前 `If` 語句。 嵌套 `Do` 迴圈的工作方式類似，最內層的 `Loop` 語句與最內層的 `Do` 語句相符。  
  
> [!NOTE]
> 對於許多控制項結構而言，當您按一下關鍵字時，結構中的所有關鍵詞都會反白顯示。 例如，當您 `If` 在結構中按一下時 `If...Then...Else` ， `If` 會反 `Then` `ElseIf` `Else` `End If` 白顯示結構中、、、和的所有實例。 若要移至下一個或上一個反白顯示的關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>嵌套不同種類的控制結構  
 您可以在另一種類型中嵌套一種控制結構。 下列範例會使用 `With` 迴圈內的區塊 `For Each` 和 `If` 區塊內的嵌套區塊 `With` 。  
  
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
  
## <a name="overlapping-control-structures"></a>重迭的控制項結構  
 您不能重迭控制結構。 這表示任何嵌套的結構都必須完全包含在下一個最內層的結構內。 例如，下列相片順序無效，因為迴圈會在 `For` 內部 `With` 區塊終止之前終止。  
  
 ![顯示無效嵌套範例的圖表。](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Visual Basic 編譯器會偵測到這類重迭的控制項結構，併發出編譯時期錯誤。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](index.md)
- [決策結構](decision-structures.md)
- [迴圈結構](loop-structures.md)
- [其他控制結構](other-control-structures.md)
