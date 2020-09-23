---
title: 如何：將程序傳遞至其他程序
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 3a7a653bbf238b50e3c7339da76df0f68ab9b59f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085785"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="d3fa4-102">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="d3fa4-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>

<span data-ttu-id="d3fa4-103">此範例示範如何使用委派，將程式傳遞至另一個程式。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="d3fa4-104">委派是一種型別，您可以像 Visual Basic 中的任何其他型別一樣使用它。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="d3fa4-105">`AddressOf`當運算子套用至程式名稱時，運算子會傳回委派物件。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="d3fa4-106">此範例的程式具有可參考另一個程式（使用運算子取得）的委派參數 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="d3fa4-107">建立委派和相符程式</span><span class="sxs-lookup"><span data-stu-id="d3fa4-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="d3fa4-108">建立名為的委派 `MathOperator` 。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="d3fa4-109">`AddNumbers`使用符合這些參數的參數和傳回值建立名為的程式 `MathOperator` ，讓簽章相符。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="d3fa4-110">使用符合的簽章來建立名為的程式 `SubtractNumbers` `MathOperator` 。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="d3fa4-111">建立名為 `DelegateTest` 的程式，該程式會接受委派做為參數。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="d3fa4-112">此程式可接受或的參考 `AddNumbers` ，因為它們的簽章與簽章 `SubtractNumbers` 相符 `MathOperator` 。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="d3fa4-113">建立名為 `Test` 的程式，該程式會呼叫 `DelegateTest` 一次，並以的委派 `AddNumbers` 做為參數，並再次使用的委派 `SubtractNumbers` 做為參數。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="d3fa4-114">當 `Test` 呼叫時，它會先顯示 `AddNumbers` 作用於和的 `5` 結果 `3` ，也就是8。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="d3fa4-115">然後 `SubtractNumbers` 會顯示對和採取行動的結果 `9` `3` ，也就是6。</span><span class="sxs-lookup"><span data-stu-id="d3fa4-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fa4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3fa4-116">See also</span></span>

- [<span data-ttu-id="d3fa4-117">委派</span><span class="sxs-lookup"><span data-stu-id="d3fa4-117">Delegates</span></span>](index.md)
- [<span data-ttu-id="d3fa4-118">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="d3fa4-118">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="d3fa4-119">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="d3fa4-119">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="d3fa4-120">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="d3fa4-120">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)
