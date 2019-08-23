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
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941678"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="82115-102">巢狀控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82115-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="82115-103">您可以將控制語句放在其他控制語句中, 例如`If...Then...Else` `For...Next`迴圈內的區塊。</span><span class="sxs-lookup"><span data-stu-id="82115-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="82115-104">放在另一個控制項語句內的控制語句稱為「已*嵌套*」。</span><span class="sxs-lookup"><span data-stu-id="82115-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="82115-105">嵌套層級</span><span class="sxs-lookup"><span data-stu-id="82115-105">Nesting Levels</span></span>  
 <span data-ttu-id="82115-106">Visual Basic 中的控制結構可以嵌套成您想要的多個層級。</span><span class="sxs-lookup"><span data-stu-id="82115-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="82115-107">一般做法是將每個結構的主體縮排, 使其更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="82115-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="82115-108">整合式開發環境 (IDE) 編輯器會自動執行此工作。</span><span class="sxs-lookup"><span data-stu-id="82115-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="82115-109">在下列範例中, `sumRows`程式會將矩陣的每個資料列的正元素加在一起。</span><span class="sxs-lookup"><span data-stu-id="82115-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="82115-110">在上述範例中, 第一個`Next`語句會關閉內部`For`迴圈, 而最後`Next`一個語句會關閉`For`外部迴圈。</span><span class="sxs-lookup"><span data-stu-id="82115-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="82115-111">同樣地, 在`If` nested 語句中`End If` , 語句會自動套用至最`If`接近的先前語句。</span><span class="sxs-lookup"><span data-stu-id="82115-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="82115-112">嵌套`Do`迴圈的工作方式類似, 最內層`Loop`的語句與最內層`Do`的語句相符。</span><span class="sxs-lookup"><span data-stu-id="82115-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82115-113">對於許多控制項結構而言, 當您按一下關鍵字時, 結構中的所有關鍵詞都會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="82115-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="82115-114">`If`例如, 當您`If...Then...Else`在`If`結構中按一下時, 會反白顯示`Then`結構中`Else`、、 `End If` `ElseIf`、和的所有實例。</span><span class="sxs-lookup"><span data-stu-id="82115-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="82115-115">若要移至下一個或上一個反白顯示的關鍵字, 請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="82115-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="82115-116">嵌套不同種類的控制結構</span><span class="sxs-lookup"><span data-stu-id="82115-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="82115-117">您可以在另一種類型中嵌套一種控制結構。</span><span class="sxs-lookup"><span data-stu-id="82115-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="82115-118">`With`下列範例會使用`For Each`迴圈內的區塊和區塊內`If`的`With`嵌套區塊。</span><span class="sxs-lookup"><span data-stu-id="82115-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="82115-119">重迭的控制項結構</span><span class="sxs-lookup"><span data-stu-id="82115-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="82115-120">您不能重迭控制結構。</span><span class="sxs-lookup"><span data-stu-id="82115-120">You cannot overlap control structures.</span></span> <span data-ttu-id="82115-121">這表示任何嵌套的結構都必須完全包含在下一個最內層的結構內。</span><span class="sxs-lookup"><span data-stu-id="82115-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="82115-122">例如, 下列相片順序無效, 因為`For`迴圈會在內部`With`區塊終止之前終止。</span><span class="sxs-lookup"><span data-stu-id="82115-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![顯示無效嵌套範例的圖表。](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 <span data-ttu-id="82115-124">Visual Basic 編譯器會偵測到這類重迭的控制項結構, 併發出編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="82115-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82115-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82115-125">See also</span></span>

- [<span data-ttu-id="82115-126">控制流程</span><span class="sxs-lookup"><span data-stu-id="82115-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="82115-127">決策結構</span><span class="sxs-lookup"><span data-stu-id="82115-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="82115-128">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="82115-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="82115-129">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="82115-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
