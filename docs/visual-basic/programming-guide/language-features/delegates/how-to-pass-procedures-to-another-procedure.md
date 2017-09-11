---
title: "如何︰ 將程序傳遞至另一個程序在 Visual Basic |Microsoft 文件"
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
- AddressOf operator
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
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
ms.openlocfilehash: 95cbcf836b0dad875851052a367666c00cd54e37
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="060e6-102">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="060e6-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="060e6-103">這個範例示範如何使用委派，以傳遞至另一個程序的程序。</span><span class="sxs-lookup"><span data-stu-id="060e6-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="060e6-104">委派是您可以使用其他任何類型中的型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="060e6-104">A delegate is a type that you can use like any other type in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="060e6-105">`AddressOf`運算子會傳回委派物件時套用至程序名稱。</span><span class="sxs-lookup"><span data-stu-id="060e6-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="060e6-106">這個範例有具有可參考另一個程序，以取得委派參數的程序`AddressOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="060e6-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="060e6-107">建立委派和比對程序</span><span class="sxs-lookup"><span data-stu-id="060e6-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="060e6-108">建立名為委派`MathOperator`。</span><span class="sxs-lookup"><span data-stu-id="060e6-108">Create a delegate named `MathOperator`.</span></span>  
  
     <span data-ttu-id="060e6-109">[!code-vb[VbVbalrDelegates #&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="060e6-109">[!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]</span></span>  
  
2.  <span data-ttu-id="060e6-110">建立名為程序`AddNumbers`使用參數和傳回值，符合`MathOperator`，以便簽章相符。</span><span class="sxs-lookup"><span data-stu-id="060e6-110">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     <span data-ttu-id="060e6-111">[!code-vb[VbVbalrDelegates #&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="060e6-111">[!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]</span></span>  
  
3.  <span data-ttu-id="060e6-112">建立名為程序`SubtractNumbers`使用簽章符合`MathOperator`。</span><span class="sxs-lookup"><span data-stu-id="060e6-112">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     <span data-ttu-id="060e6-113">[!code-vb[VbVbalrDelegates #&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="060e6-113">[!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]</span></span>  
  
4.  <span data-ttu-id="060e6-114">建立名為程序`DelegateTest`接受委派做為參數。</span><span class="sxs-lookup"><span data-stu-id="060e6-114">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="060e6-115">此程序可接受的參考`AddNumbers`或`SubtractNumbers`，因為它們的簽章相符`MathOperator`簽章。</span><span class="sxs-lookup"><span data-stu-id="060e6-115">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     <span data-ttu-id="060e6-116">[!code-vb[VbVbalrDelegates #&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="060e6-116">[!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]</span></span>  
  
5.  <span data-ttu-id="060e6-117">建立名為程序`Test`呼叫`DelegateTest`另一次使用的委派`AddNumbers`做為參數，然後再次使用的委派`SubtractNumbers`做為參數。</span><span class="sxs-lookup"><span data-stu-id="060e6-117">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     <span data-ttu-id="060e6-118">[!code-vb[VbVbalrDelegates #&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="060e6-118">[!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]</span></span>  
  
     <span data-ttu-id="060e6-119">當`Test`是呼叫，它顯示的第一次的結果`AddNumbers`上之`5`和`3`，這是 8。</span><span class="sxs-lookup"><span data-stu-id="060e6-119">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="060e6-120">結果`SubtractNumbers`作用於`9`和`3`顯示時，這是 6。</span><span class="sxs-lookup"><span data-stu-id="060e6-120">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060e6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="060e6-121">See Also</span></span>  
 <span data-ttu-id="060e6-122">[委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="060e6-122">[Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="060e6-123"> [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="060e6-123"> [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="060e6-124"> [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="060e6-124"> [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="060e6-125"> [如何：叫用委派方法](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span><span class="sxs-lookup"><span data-stu-id="060e6-125"> [How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span></span>
