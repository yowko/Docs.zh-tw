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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="f11e3-102">巢狀控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f11e3-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="f11e3-103">您可以將控制語句放置在其他控制語句中，例如`If...Then...Else``For...Next`迴圈中的塊。</span><span class="sxs-lookup"><span data-stu-id="f11e3-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="f11e3-104">放置在另一個控制語句中的控制語句*表示嵌套。*</span><span class="sxs-lookup"><span data-stu-id="f11e3-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="f11e3-105">嵌套級別</span><span class="sxs-lookup"><span data-stu-id="f11e3-105">Nesting Levels</span></span>  
 <span data-ttu-id="f11e3-106">Visual Basic 中的控制項結構可以嵌套到所需的盡可能多的級別。</span><span class="sxs-lookup"><span data-stu-id="f11e3-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="f11e3-107">通常的做法是通過縮進每個結構的主體來使嵌套結構更具可讀性。</span><span class="sxs-lookup"><span data-stu-id="f11e3-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="f11e3-108">整合式開發環境 （IDE） 編輯器會自動這樣做。</span><span class="sxs-lookup"><span data-stu-id="f11e3-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="f11e3-109">在下面的示例中，該過程`sumRows`將矩陣每行的正元素相加。</span><span class="sxs-lookup"><span data-stu-id="f11e3-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="f11e3-110">在前面的示例中，第一個`Next`語句關閉內部`For`迴圈，最後一`Next`個語句關閉外部`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f11e3-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="f11e3-111">同樣，在嵌套`If`語句中，`End If`語句會自動應用於最近的先前`If`語句。</span><span class="sxs-lookup"><span data-stu-id="f11e3-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="f11e3-112">嵌套`Do`迴圈的工作方式類似，其中最`Loop`裡面的語句與最`Do`裡面的語句匹配。</span><span class="sxs-lookup"><span data-stu-id="f11e3-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f11e3-113">對於許多控制項結構，當您按一下關鍵字時，結構中的所有關鍵字都會突出顯示。</span><span class="sxs-lookup"><span data-stu-id="f11e3-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="f11e3-114">例如`If`，當您在`If...Then...Else`構造中按一下時，構造`If``Then``ElseIf``Else``End If`中的所有實例將突出顯示。</span><span class="sxs-lookup"><span data-stu-id="f11e3-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="f11e3-115">要移動到下一個或上一個突出顯示的關鍵字，請按 CTRL_SHIFT_向下箭頭或 CTRL_SHIFT_UP 箭頭。</span><span class="sxs-lookup"><span data-stu-id="f11e3-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="f11e3-116">嵌套不同類型的控制結構</span><span class="sxs-lookup"><span data-stu-id="f11e3-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="f11e3-117">可以將一種控制結構嵌套在另一種類型中。</span><span class="sxs-lookup"><span data-stu-id="f11e3-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="f11e3-118">下面的`With`示例使用`For Each`迴圈中的塊和塊內的`If``With`嵌套塊。</span><span class="sxs-lookup"><span data-stu-id="f11e3-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="f11e3-119">重疊的控制結構</span><span class="sxs-lookup"><span data-stu-id="f11e3-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="f11e3-120">不能重疊控制結構。</span><span class="sxs-lookup"><span data-stu-id="f11e3-120">You cannot overlap control structures.</span></span> <span data-ttu-id="f11e3-121">這意味著任何嵌套結構都必須完全包含在下一個最內部結構中。</span><span class="sxs-lookup"><span data-stu-id="f11e3-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="f11e3-122">例如，以下排列無效，`For`因為迴圈在內部`With`塊終止之前終止。</span><span class="sxs-lookup"><span data-stu-id="f11e3-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![顯示無效嵌套示例的圖表。](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="f11e3-124">Visual Basic 編譯器檢測此類重疊的控制結構，併發出編譯時錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="f11e3-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11e3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11e3-125">See also</span></span>

- [<span data-ttu-id="f11e3-126">控制流程</span><span class="sxs-lookup"><span data-stu-id="f11e3-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="f11e3-127">決策結構</span><span class="sxs-lookup"><span data-stu-id="f11e3-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="f11e3-128">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="f11e3-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="f11e3-129">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="f11e3-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
