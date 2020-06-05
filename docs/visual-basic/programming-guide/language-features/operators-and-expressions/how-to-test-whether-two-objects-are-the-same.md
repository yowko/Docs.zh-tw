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
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403417"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="500c9-102">如何：測試兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="500c9-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="500c9-103">如果您有兩個參考物件的變數，您可以使用 `Is` or `IsNot` 運算子（或兩者）來判斷它們是否參考相同的實例。</span><span class="sxs-lookup"><span data-stu-id="500c9-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="500c9-104">測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="500c9-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="500c9-105">使用[Is 運算子](../../../language-reference/operators/is-operator.md)或[IsNot 運算子](../../../language-reference/operators/isnot-operator.md)，並將兩個變數當做運算元。</span><span class="sxs-lookup"><span data-stu-id="500c9-105">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="500c9-106">根據兩個物件是否參考相同的實例而定，您可能會想要採取特定動作。</span><span class="sxs-lookup"><span data-stu-id="500c9-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="500c9-107">上述範例會 `c` 針對表單上的現用控制項比較控制項 `f` 。</span><span class="sxs-lookup"><span data-stu-id="500c9-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="500c9-108">如果沒有作用中的控制項，或有一個，但它與不是相同的控制項實例，則 `c` `If` 語句會失敗，而程式會傳回而不會進一步處理。</span><span class="sxs-lookup"><span data-stu-id="500c9-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="500c9-109">無論您使用 `Is` 或， `IsNot` 都是您個人的便利性。</span><span class="sxs-lookup"><span data-stu-id="500c9-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="500c9-110">在指定的運算式中，可能比另一個更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="500c9-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500c9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="500c9-111">See also</span></span>

- [<span data-ttu-id="500c9-112">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="500c9-112">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
