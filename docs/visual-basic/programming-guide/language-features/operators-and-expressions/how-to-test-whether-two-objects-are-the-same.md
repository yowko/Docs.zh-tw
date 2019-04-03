---
title: HOW TO：測試兩個物件是否相同 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: dbb268175d197e7b931af45a98f3a273c593e5a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819105"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="ebf0f-102">HOW TO：測試兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebf0f-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="ebf0f-103">如果您有兩個參考物件的變數，您可以使用`Is`或`IsNot`運算子，或兩者，以判斷它們是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="ebf0f-104">若要測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="ebf0f-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="ebf0f-105">使用[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)或[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)搭配兩個變數，做為運算元。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="ebf0f-106">您可以採取特定動作取決於兩個物件是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="ebf0f-107">上述範例會比較控制項`c`針對表單上的現用控制項`f`。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="ebf0f-108">如果沒有任何作用中的控制項，或如果有一個，但它不是相同的控制項執行個體`c`，則`If`陳述式失敗，且程序傳回不會進一步處理。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="ebf0f-109">您是否使用`Is`或`IsNot`是您的個人比較方便。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="ebf0f-110">一個可能比其他指定的運算式中讀取的工作變得更容易。</span><span class="sxs-lookup"><span data-stu-id="ebf0f-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf0f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf0f-111">See also</span></span>

- [<span data-ttu-id="ebf0f-112">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="ebf0f-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
