---
title: "如何：測試兩個物件是否相同 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="8b3d0-102">如何：測試兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b3d0-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="8b3d0-103">如果您有兩個參考物件的變數，您可以使用`Is`或`IsNot`運算子，或兩者，以判斷它們是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="8b3d0-104">若要測試這兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="8b3d0-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="8b3d0-105">使用[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)或[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)與兩個變數做為運算元。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="8b3d0-106">您可能想要採取某些動作根據兩個物件是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="8b3d0-107">上述範例會比較控制項`c`針對表單上的現用控制項`f`。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="8b3d0-108">如果沒有使用中的控制項，或如果沒有其中一個，但它不是相同的控制項執行個體`c`，然後在`If`陳述式失敗，且此程序傳回而不需進一步處理。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="8b3d0-109">不論您是使用`Is`或`IsNot`是您的個人起見。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="8b3d0-110">一個可能更方便閱讀比另一個則指定運算式中。</span><span class="sxs-lookup"><span data-stu-id="8b3d0-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3d0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b3d0-111">See Also</span></span>  
 [<span data-ttu-id="8b3d0-112">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="8b3d0-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
