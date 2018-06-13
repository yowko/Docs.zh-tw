---
title: 巢狀控制結構 (Visual Basic)
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
ms.openlocfilehash: ec3d4d477290480cdfa0f5b1c88aa82c81040d11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648067"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="0a275-102">巢狀控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a275-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="0a275-103">您可以將放控制陳述式內部的其他控制陳述式，例如`If...Then...Else`區塊內`For...Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="0a275-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="0a275-104">放在另一個控制陳述式內的控制陳述式即為*巢狀*。</span><span class="sxs-lookup"><span data-stu-id="0a275-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="0a275-105">巢狀層級</span><span class="sxs-lookup"><span data-stu-id="0a275-105">Nesting Levels</span></span>  
 <span data-ttu-id="0a275-106">在 Visual Basic 中的控制結構可以是巢狀的層級您的需要。</span><span class="sxs-lookup"><span data-stu-id="0a275-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="0a275-107">它是常見的作法是藉由縮排每一個主體，讓巢狀的結構更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="0a275-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="0a275-108">整合式的開發環境 (IDE) 編輯器會自動執行此。</span><span class="sxs-lookup"><span data-stu-id="0a275-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="0a275-109">在下列範例中，此程序`sumRows`一起正值會將元素加入每個資料列的矩陣。</span><span class="sxs-lookup"><span data-stu-id="0a275-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="0a275-110">在上述範例中，第一個`Next`陳述式會關閉內部`For`迴圈和最後一個`Next`陳述式會關閉外部`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="0a275-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="0a275-111">同樣地，在巢狀`If`陳述式，`End If`陳述式會自動套用至最接近之前`If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a275-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="0a275-112">巢狀`Do`適用於類似的方式，最內層的迴圈`Loop`陳述式比對最內層`Do`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a275-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a275-113">許多控制項結構，當您按一下關鍵字，所有的結構中的關鍵字會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="0a275-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="0a275-114">比方說，當您按一下`If`中`If...Then...Else`建構的所有執行個體`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="0a275-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="0a275-115">若要移至下一頁或上一頁反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="0a275-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="0a275-116">巢狀方式置於不同種類的控制結構</span><span class="sxs-lookup"><span data-stu-id="0a275-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="0a275-117">您可以巢狀控制結構中其他類型的一種。</span><span class="sxs-lookup"><span data-stu-id="0a275-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="0a275-118">下列範例會使用`With`封鎖內`For Each`迴圈及巢狀`If`封鎖內`With`區塊。</span><span class="sxs-lookup"><span data-stu-id="0a275-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="0a275-119">重疊的控制結構</span><span class="sxs-lookup"><span data-stu-id="0a275-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="0a275-120">您不能重疊控制結構。</span><span class="sxs-lookup"><span data-stu-id="0a275-120">You cannot overlap control structures.</span></span> <span data-ttu-id="0a275-121">這表示任何巢狀的結構必須完全包含在下一個最內層結構內。</span><span class="sxs-lookup"><span data-stu-id="0a275-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="0a275-122">例如，下列的排列方式不正確因為`For`迴圈終止之前內部`With`區塊會結束。</span><span class="sxs-lookup"><span data-stu-id="0a275-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="0a275-123">![無效巢狀處理示意圖](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="0a275-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="0a275-124">無效的巢狀結構和結構</span><span class="sxs-lookup"><span data-stu-id="0a275-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="0a275-125">Visual Basic 編譯器會偵測這類重疊的控制結構，並發出編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a275-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a275-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a275-126">See Also</span></span>  
 [<span data-ttu-id="0a275-127">控制流程</span><span class="sxs-lookup"><span data-stu-id="0a275-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="0a275-128">決策結構</span><span class="sxs-lookup"><span data-stu-id="0a275-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="0a275-129">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="0a275-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="0a275-130">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="0a275-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
