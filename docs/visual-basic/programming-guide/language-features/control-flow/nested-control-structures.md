---
title: "巢狀控制結構 (Visual Basic) |Microsoft 文件"
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
- Visual Basic code, control flow
- control structures, nested
- conditional statements, nested
- statements [Visual Basic], control flow
- control flow, nested control statements
- structures, nested control
- nested control statements
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
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
ms.openlocfilehash: 4afc0afc2ad63d03f2c4251640d3682b2b184504
ms.lasthandoff: 03/13/2017

---
# <a name="nested-control-structures-visual-basic"></a>巢狀控制結構 (Visual Basic)
您可以在放置控制陳述其他控制陳述式，例如`If...Then...Else`內封鎖`For...Next`迴圈。 控制陳述式置於另一個控制陳述式即為*巢狀*。  
  
## <a name="nesting-levels"></a>巢狀層級  
 控制項中的結構[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可以巢狀層級所要。 它是常見的做法進行縮排的每個主體，讓巢狀的結構更容易閱讀。 整合式的開發環境 (IDE) 編輯器會自動執行此。  
  
 在下列範例中，此程序`sumRows`同時新增矩陣的每個資料列的正面的項目。  
  
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
  
 在上述範例中，第一個`Next`陳述式會關閉內部`For`迴圈，而最後`Next`陳述式會關閉外部`For`迴圈。  
  
 同樣地，在巢狀`If`陳述式，`End If`陳述式將自動套用至最接近的前一次`If`陳述式。 巢狀`Do`以類似的方式，最內層的迴圈運作`Loop`陳述式對應至最內層`Do`陳述式。  
  
> [!NOTE]
>  許多控制項結構，當您按一下關鍵字，所有的關鍵字，在結構中反白顯示。 比方說，當您按一下`If`中`If...Then...Else`建構，而所有執行個體的`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。 若要移至下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>不同種類的控制結構的巢狀結構  
 您可以巢狀控制結構內的另一種的一種。 下列範例會使用`With`內封鎖`For Each`迴圈和巢狀`If`內封鎖`With`區塊。  
  
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
  
## <a name="overlapping-control-structures"></a>重疊的控制結構  
 您不能重疊控制結構。 這表示任何巢狀的結構必須完全包含在下一個最內層結構內。 例如，下列的排列方式不正確因為`For`迴圈終止之前內部`With`區塊會終止。  
  
 ![無效的巢狀處理示意圖](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
無效的巢狀結構和結構  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器偵測到這類重疊的控制結構，並發出編譯時期錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
