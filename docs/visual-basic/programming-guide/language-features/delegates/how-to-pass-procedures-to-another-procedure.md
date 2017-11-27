---
title: "如何：在 Visual Basic 中將程序傳遞至其他程序"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="39739-102">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="39739-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="39739-103">這個範例示範如何使用委派來將傳遞至另一個程序的程序。</span><span class="sxs-lookup"><span data-stu-id="39739-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="39739-104">委派是您可以使用中的其他任何類型的型別[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="39739-104">A delegate is a type that you can use like any other type in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="39739-105">`AddressOf`運算子會傳回委派物件時套用至程序名稱。</span><span class="sxs-lookup"><span data-stu-id="39739-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="39739-106">這個範例有與委派參數可接受另一個程序，取得與參考的程序`AddressOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="39739-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="39739-107">建立委派和比對程序</span><span class="sxs-lookup"><span data-stu-id="39739-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="39739-108">建立名為委派`MathOperator`。</span><span class="sxs-lookup"><span data-stu-id="39739-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="39739-109">建立名為程序`AddNumbers`使用參數和傳回值，符合`MathOperator`，如此一來，簽章相符。</span><span class="sxs-lookup"><span data-stu-id="39739-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="39739-110">建立名為程序`SubtractNumbers`的簽章來符合`MathOperator`。</span><span class="sxs-lookup"><span data-stu-id="39739-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="39739-111">建立名為程序`DelegateTest`接受委派做為參數。</span><span class="sxs-lookup"><span data-stu-id="39739-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="39739-112">此程序可接受的參考`AddNumbers`或`SubtractNumbers`，因為它們的簽章相符`MathOperator`簽章。</span><span class="sxs-lookup"><span data-stu-id="39739-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="39739-113">建立名為程序`Test`呼叫`DelegateTest`另一次使用的委派`AddNumbers`做為參數，再使用的委派`SubtractNumbers`做為參數。</span><span class="sxs-lookup"><span data-stu-id="39739-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="39739-114">當`Test`是呼叫，它顯示的第一次的結果`AddNumbers`做角色上`5`和`3`，這是 8。</span><span class="sxs-lookup"><span data-stu-id="39739-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="39739-115">結果`SubtractNumbers`代表`9`和`3`隨即顯示，這是 6。</span><span class="sxs-lookup"><span data-stu-id="39739-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39739-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39739-116">See Also</span></span>  
 [<span data-ttu-id="39739-117">委派</span><span class="sxs-lookup"><span data-stu-id="39739-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="39739-118">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="39739-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="39739-119">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="39739-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="39739-120">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="39739-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
