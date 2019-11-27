---
title: 如何：測試兩個物件是否相同
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343624"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="c2e53-102">如何：測試兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2e53-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="c2e53-103">如果您有兩個參考物件的變數，您可以使用 `Is` 或 `IsNot` 運算子（或兩者）來判斷它們是否參考相同的實例。</span><span class="sxs-lookup"><span data-stu-id="c2e53-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="c2e53-104">測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="c2e53-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="c2e53-105">使用[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)或[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)，並將兩個變數當做運算元。</span><span class="sxs-lookup"><span data-stu-id="c2e53-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="c2e53-106">根據兩個物件是否參考相同的實例而定，您可能會想要採取特定動作。</span><span class="sxs-lookup"><span data-stu-id="c2e53-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="c2e53-107">上述範例會針對表單 `f`上的現用控制項比較控制項 `c`。</span><span class="sxs-lookup"><span data-stu-id="c2e53-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="c2e53-108">如果沒有作用中的控制項，或有一個，但它與 `c`的控制項實例不同，則 `If` 語句會失敗，而程式會傳回而不會進行進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="c2e53-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="c2e53-109">無論您是使用 `Is` 或 `IsNot`，都是您個人的便利性。</span><span class="sxs-lookup"><span data-stu-id="c2e53-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="c2e53-110">在指定的運算式中，可能比另一個更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="c2e53-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e53-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e53-111">See also</span></span>

- [<span data-ttu-id="c2e53-112">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="c2e53-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
