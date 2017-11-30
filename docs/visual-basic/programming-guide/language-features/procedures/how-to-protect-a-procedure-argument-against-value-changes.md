---
title: "如何：防止程序引數的值變更 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="f999f-102">如何：防止程序引數的值變更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f999f-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="f999f-103">如果程序宣告為參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供程序程式碼直接呼叫程式碼中的引數的基礎的程式設計項目參考。</span><span class="sxs-lookup"><span data-stu-id="f999f-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="f999f-104">這可讓程序來變更呼叫的程式碼中引數的基礎值。</span><span class="sxs-lookup"><span data-stu-id="f999f-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="f999f-105">在某些情況下呼叫的程式碼可能會想要防止這類變更。</span><span class="sxs-lookup"><span data-stu-id="f999f-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="f999f-106">您一律可以保護在變更引數，藉由宣告的對應參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序中。</span><span class="sxs-lookup"><span data-stu-id="f999f-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="f999f-107">如果您想要能夠變更在某些情況下，而不是其他指定的引數，您可以將它宣告`ByRef`，並讓呼叫的程式碼，判斷每個呼叫中的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="f999f-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="f999f-108">它會由封閉式括號，以傳值，對應的引數，或不將其括在括號，以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="f999f-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="f999f-109">如需詳細資訊，請參閱[如何： 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="f999f-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f999f-110">範例</span><span class="sxs-lookup"><span data-stu-id="f999f-110">Example</span></span>  
 <span data-ttu-id="f999f-111">下列範例會示範兩個程序的方式取得陣列變數和操作其項目上。</span><span class="sxs-lookup"><span data-stu-id="f999f-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="f999f-112">`increase`程序只會加入一個，以便每個項目。</span><span class="sxs-lookup"><span data-stu-id="f999f-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="f999f-113">`replace`程序會將新的陣列指派給參數`a()`再加入一個，以便每個項目。</span><span class="sxs-lookup"><span data-stu-id="f999f-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="f999f-114">不過，重新指派不會影響呼叫的程式碼中的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="f999f-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 <span data-ttu-id="f999f-115">第一個`MsgBox`呼叫顯示"之後 increase(n): 11、 21、 31、 41"。</span><span class="sxs-lookup"><span data-stu-id="f999f-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="f999f-116">因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="f999f-116">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="f999f-117">第二個`MsgBox`呼叫顯示"之後 replace(n): 11、 21、 31、 41"。</span><span class="sxs-lookup"><span data-stu-id="f999f-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="f999f-118">因為`n`傳遞`ByVal`，`replace`無法修改變數`n`指定新的陣列，讓呼叫的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="f999f-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="f999f-119">當`replace`建立新的陣列執行個體`k`並將它指派給本機變數`a`，就會失去參考`n`傳入呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="f999f-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="f999f-120">它會變更的成員`a`，只有本機陣列`k`會受到影響。</span><span class="sxs-lookup"><span data-stu-id="f999f-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="f999f-121">因此，`replace`不會遞增的值陣列的`n`呼叫的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="f999f-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f999f-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f999f-122">Compiling the Code</span></span>  
 <span data-ttu-id="f999f-123">中的預設值[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="f999f-123">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="f999f-124">不過，它是良好的程式設計作法中包含  [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="f999f-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="f999f-125">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="f999f-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f999f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f999f-126">See Also</span></span>  
 [<span data-ttu-id="f999f-127">程序</span><span class="sxs-lookup"><span data-stu-id="f999f-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f999f-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="f999f-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f999f-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="f999f-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="f999f-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="f999f-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="f999f-131">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="f999f-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="f999f-132">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="f999f-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="f999f-133">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="f999f-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="f999f-134">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="f999f-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="f999f-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="f999f-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="f999f-136">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="f999f-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
