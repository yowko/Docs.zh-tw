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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8275a0628c8593d9e6c55ef27adcde2acec31547
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="ffec6-102">巢狀控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffec6-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="ffec6-103">您可以在放置控制陳述其他控制陳述式，例如`If...Then...Else`內封鎖`For...Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="ffec6-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="ffec6-104">控制陳述式置於另一個控制陳述式即為*巢狀*。</span><span class="sxs-lookup"><span data-stu-id="ffec6-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="ffec6-105">巢狀層級</span><span class="sxs-lookup"><span data-stu-id="ffec6-105">Nesting Levels</span></span>  
 <span data-ttu-id="ffec6-106">控制項中的結構[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可以巢狀層級所要。</span><span class="sxs-lookup"><span data-stu-id="ffec6-106">Control structures in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can be nested to as many levels as you want.</span></span> <span data-ttu-id="ffec6-107">它是常見的做法進行縮排的每個主體，讓巢狀的結構更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="ffec6-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="ffec6-108">整合式的開發環境 (IDE) 編輯器會自動執行此。</span><span class="sxs-lookup"><span data-stu-id="ffec6-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="ffec6-109">在下列範例中，此程序`sumRows`同時新增矩陣的每個資料列的正面的項目。</span><span class="sxs-lookup"><span data-stu-id="ffec6-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="ffec6-110">在上述範例中，第一個`Next`陳述式會關閉內部`For`迴圈，而最後`Next`陳述式會關閉外部`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="ffec6-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="ffec6-111">同樣地，在巢狀`If`陳述式，`End If`陳述式將自動套用至最接近的前一次`If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ffec6-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="ffec6-112">巢狀`Do`以類似的方式，最內層的迴圈運作`Loop`陳述式對應至最內層`Do`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ffec6-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffec6-113">許多控制項結構，當您按一下關鍵字，所有的關鍵字，在結構中反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ffec6-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="ffec6-114">比方說，當您按一下`If`中`If...Then...Else`建構，而所有執行個體的`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ffec6-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="ffec6-115">若要移至下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="ffec6-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="ffec6-116">不同種類的控制結構的巢狀結構</span><span class="sxs-lookup"><span data-stu-id="ffec6-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="ffec6-117">您可以巢狀控制結構內的另一種的一種。</span><span class="sxs-lookup"><span data-stu-id="ffec6-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="ffec6-118">下列範例會使用`With`內封鎖`For Each`迴圈和巢狀`If`內封鎖`With`區塊。</span><span class="sxs-lookup"><span data-stu-id="ffec6-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="ffec6-119">重疊的控制結構</span><span class="sxs-lookup"><span data-stu-id="ffec6-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="ffec6-120">您不能重疊控制結構。</span><span class="sxs-lookup"><span data-stu-id="ffec6-120">You cannot overlap control structures.</span></span> <span data-ttu-id="ffec6-121">這表示任何巢狀的結構必須完全包含在下一個最內層結構內。</span><span class="sxs-lookup"><span data-stu-id="ffec6-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="ffec6-122">例如，下列的排列方式不正確因為`For`迴圈終止之前內部`With`區塊會終止。</span><span class="sxs-lookup"><span data-stu-id="ffec6-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="ffec6-123">![無效的巢狀處理示意圖](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="ffec6-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="ffec6-124">無效的巢狀結構和結構</span><span class="sxs-lookup"><span data-stu-id="ffec6-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="ffec6-125">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器偵測到這類重疊的控制結構，並發出編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="ffec6-125">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffec6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffec6-126">See Also</span></span>  
 <span data-ttu-id="ffec6-127">[控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="ffec6-127">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="ffec6-128"> [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="ffec6-128"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="ffec6-129"> [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="ffec6-129"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="ffec6-130"> [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)</span><span class="sxs-lookup"><span data-stu-id="ffec6-130"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)</span></span>
