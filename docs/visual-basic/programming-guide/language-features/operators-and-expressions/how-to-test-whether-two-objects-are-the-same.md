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
ms.openlocfilehash: d29d1b0026b3f62d47859cd5b4b7a601532e27b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071686"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="386cc-102">如何：測試兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="386cc-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>

<span data-ttu-id="386cc-103">如果您有兩個參考物件的變數，您可以使用 `Is` or `IsNot` 運算子（或兩者）來判斷它們是否參考相同的實例。</span><span class="sxs-lookup"><span data-stu-id="386cc-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="386cc-104">測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="386cc-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="386cc-105">使用 as [運算子](../../../language-reference/operators/is-operator.md) 或 [IsNot 運算子](../../../language-reference/operators/isnot-operator.md) ，並將兩個變數做為運算元。</span><span class="sxs-lookup"><span data-stu-id="386cc-105">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="386cc-106">您可能會想要根據兩個物件是否參考相同的實例，採取特定動作。</span><span class="sxs-lookup"><span data-stu-id="386cc-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="386cc-107">上述範例會將控制項 `c` 與表單上的作用中控制項進行比較 `f` 。</span><span class="sxs-lookup"><span data-stu-id="386cc-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="386cc-108">如果沒有作用中的控制項，或者有一個控制項不是相同的控制項實例 `c` ，則 `If` 語句會失敗，而且程式會傳回而不會進一步處理。</span><span class="sxs-lookup"><span data-stu-id="386cc-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="386cc-109">無論您 `Is` 是使用或， `IsNot` 都能為您提供個人的便利性。</span><span class="sxs-lookup"><span data-stu-id="386cc-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="386cc-110">在給定的運算式中，可能比另一個更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="386cc-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386cc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="386cc-111">See also</span></span>

- [<span data-ttu-id="386cc-112">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="386cc-112">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
