---
title: HOW TO：防止程序引數的值變更 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 70378b57c6d3af5a98e0ba9c6e3aebc319561b1b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837776"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="69fc0-102">HOW TO：防止程序引數的值變更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69fc0-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="69fc0-103">如果程序宣告做為參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 提供的程序程式碼基礎中呼叫的程式碼的引數的程式設計項目直接參考。</span><span class="sxs-lookup"><span data-stu-id="69fc0-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="69fc0-104">這可讓程序來變更基礎呼叫程式碼中的引數的值。</span><span class="sxs-lookup"><span data-stu-id="69fc0-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="69fc0-105">在某些情況下呼叫程式碼可能會想要防止這類變更。</span><span class="sxs-lookup"><span data-stu-id="69fc0-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="69fc0-106">您一律可以保護變更引數，藉由宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序中。</span><span class="sxs-lookup"><span data-stu-id="69fc0-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="69fc0-107">如果您想要能夠變更在某些情況下，而不是其他指定的引數，您可以將它宣告`ByRef`並讓呼叫的程式碼，判斷每個呼叫中的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="69fc0-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="69fc0-108">它會藉由以傳值的括號括住相對應的引數，或不以傳址方式傳遞它的括號括住它。</span><span class="sxs-lookup"><span data-stu-id="69fc0-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="69fc0-109">如需詳細資訊，請參閱[如何：強制以傳值方式傳遞的引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="69fc0-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69fc0-110">範例</span><span class="sxs-lookup"><span data-stu-id="69fc0-110">Example</span></span>  
 <span data-ttu-id="69fc0-111">下列範例會顯示取得陣列變數和操作的兩個程序，其項目上。</span><span class="sxs-lookup"><span data-stu-id="69fc0-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="69fc0-112">`increase`程序只需新增至每個項目。</span><span class="sxs-lookup"><span data-stu-id="69fc0-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="69fc0-113">`replace`程序會將新的陣列指派給參數`a()`，然後新增一個每個項目。</span><span class="sxs-lookup"><span data-stu-id="69fc0-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="69fc0-114">不過，重新指派不會影響呼叫端程式碼中的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="69fc0-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="69fc0-115">第一個`MsgBox`呼叫會顯示 「 increase(n) 之後：11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="69fc0-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="69fc0-116">因為陣列`n`是參考型別`increase`即使的傳遞機制，可以變更其成員， `ByVal`。</span><span class="sxs-lookup"><span data-stu-id="69fc0-116">Because the array `n` is a reference type, `increase` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="69fc0-117">第二個`MsgBox`呼叫會顯示 「 replace(n) 之後：11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="69fc0-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="69fc0-118">因為`n`傳遞`ByVal`，`replace`不能修改變數`n`中呼叫的程式碼，將新的陣列指派給它。</span><span class="sxs-lookup"><span data-stu-id="69fc0-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="69fc0-119">當`replace`建立新的陣列執行個體`k`並將它指派給區域變數`a`，就會失去參考`n`傳入呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="69fc0-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="69fc0-120">它會變更的成員`a`，只有本機陣列`k`會受到影響。</span><span class="sxs-lookup"><span data-stu-id="69fc0-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="69fc0-121">因此，`replace`不會遞增的值陣列的`n`中呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="69fc0-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69fc0-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="69fc0-122">Compiling the Code</span></span>  
 <span data-ttu-id="69fc0-123">在 Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="69fc0-123">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="69fc0-124">不過，它是良好的程式設計方式來包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="69fc0-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="69fc0-125">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="69fc0-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69fc0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69fc0-126">See also</span></span>

- [<span data-ttu-id="69fc0-127">程序</span><span class="sxs-lookup"><span data-stu-id="69fc0-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="69fc0-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="69fc0-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="69fc0-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="69fc0-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="69fc0-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="69fc0-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="69fc0-131">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="69fc0-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="69fc0-132">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="69fc0-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="69fc0-133">如何：程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="69fc0-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="69fc0-134">如何：強制以傳值方式傳遞的引數</span><span class="sxs-lookup"><span data-stu-id="69fc0-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="69fc0-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="69fc0-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="69fc0-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="69fc0-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
