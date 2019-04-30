---
title: HOW TO：傳遞至另一個程序，在 Visual Basic 中的程序
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973275"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="873a1-102">HOW TO：傳遞至另一個程序，在 Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="873a1-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="873a1-103">此範例示範如何使用委派傳遞至其他程序的程序。</span><span class="sxs-lookup"><span data-stu-id="873a1-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="873a1-104">委派是您可以使用 Visual Basic 中的其他任何類型的類型。</span><span class="sxs-lookup"><span data-stu-id="873a1-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="873a1-105">`AddressOf`運算子會傳回委派物件時套用至程序名稱。</span><span class="sxs-lookup"><span data-stu-id="873a1-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="873a1-106">這個範例包含具有 delegate 參數可接受的另一個程序，以取得參考的程序`AddressOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="873a1-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="873a1-107">建立委派和比對程序</span><span class="sxs-lookup"><span data-stu-id="873a1-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="873a1-108">建立名為委派`MathOperator`。</span><span class="sxs-lookup"><span data-stu-id="873a1-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="873a1-109">建立名為程序`AddNumbers`使用參數和傳回值，符合`MathOperator`，如此一來，簽章相符。</span><span class="sxs-lookup"><span data-stu-id="873a1-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="873a1-110">建立名為程序`SubtractNumbers`簽章符合`MathOperator`。</span><span class="sxs-lookup"><span data-stu-id="873a1-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="873a1-111">建立名為程序`DelegateTest`會做為參數的委派。</span><span class="sxs-lookup"><span data-stu-id="873a1-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="873a1-112">此程序可接受的參考`AddNumbers`或是`SubtractNumbers`，因為它們的簽章相符`MathOperator`簽章。</span><span class="sxs-lookup"><span data-stu-id="873a1-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="873a1-113">建立名為程序`Test`它會呼叫`DelegateTest`另一次使用的委派`AddNumbers`做為參數，並再次使用的委派`SubtractNumbers`做為參數。</span><span class="sxs-lookup"><span data-stu-id="873a1-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="873a1-114">當`Test`是呼叫，它顯示的第一次的結果`AddNumbers`處理`5`和`3`，這是 8。</span><span class="sxs-lookup"><span data-stu-id="873a1-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="873a1-115">結果`SubtractNumbers`作`9`和`3`隨即顯示，這是 6。</span><span class="sxs-lookup"><span data-stu-id="873a1-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873a1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="873a1-116">See also</span></span>

- [<span data-ttu-id="873a1-117">委派</span><span class="sxs-lookup"><span data-stu-id="873a1-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="873a1-118">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="873a1-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="873a1-119">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="873a1-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="873a1-120">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="873a1-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
