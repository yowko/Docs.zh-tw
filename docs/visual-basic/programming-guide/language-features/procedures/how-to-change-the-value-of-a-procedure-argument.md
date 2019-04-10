---
title: HOW TO：變更值的程序引數 (Visual Basic)
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: a56bdf888163c9559b87e857abb33522c547ed45
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316618"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="2f4e4-102">HOW TO：變更值的程序引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f4e4-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="2f4e4-103">當您呼叫程序時，您提供每個引數會對應至其中一個程序中所定義的參數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="2f4e4-104">在某些情況下，程序程式碼可以變更基礎呼叫程式碼中的引數的值。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="2f4e4-105">在其他情況下，此程序可以變更其本機複本的引數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="2f4e4-106">當您呼叫程序時，Visual Basic 可讓每個傳遞的引數的本機副本[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="2f4e4-107">每個引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 提供的程序程式碼基礎中呼叫的程式碼的引數的程式設計項目直接參考。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="2f4e4-108">如果呼叫程式碼對應的項目是可修改的項目，並傳遞引數`ByRef`，程序程式碼可以使用直接參考變更呼叫的程式碼中的項目的值。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="2f4e4-109">變更基礎值</span><span class="sxs-lookup"><span data-stu-id="2f4e4-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="2f4e4-110">若要變更基礎值的程序中的引數呼叫的程式碼</span><span class="sxs-lookup"><span data-stu-id="2f4e4-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="2f4e4-111">在程序宣告中，指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)參數對應到引數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="2f4e4-112">在呼叫的程式碼，做為引數會傳遞可修改的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="2f4e4-113">在呼叫的程式碼中，未將引數清單中的括號括住的引數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="2f4e4-114">在程序程式碼中，使用參數名稱來指派值給呼叫程式碼對應的項目。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="2f4e4-115">範例，請參閱稍後如需示範。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="2f4e4-116">變更本機複本</span><span class="sxs-lookup"><span data-stu-id="2f4e4-116">Changing Local Copies</span></span>  
 <span data-ttu-id="2f4e4-117">如果呼叫程式碼對應的項目是不可修改的項目，或如果引數傳遞`ByVal`，程序不能變更其呼叫的程式碼中的值。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="2f4e4-118">不過，此程序可以變更這類引數的本機複本。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="2f4e4-119">若要變更的程序程式碼中的程序引數的複本</span><span class="sxs-lookup"><span data-stu-id="2f4e4-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="2f4e4-120">在程序宣告中，指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)參數對應到引數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="2f4e4-121">-或-</span><span class="sxs-lookup"><span data-stu-id="2f4e4-121">-or-</span></span>  
  
     <span data-ttu-id="2f4e4-122">在呼叫的程式碼中，括住的引數清單中的括號括住的引數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="2f4e4-123">這會強制 Visual Basic，以傳遞引數的值，即使對應的參數會指定`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="2f4e4-124">在程序程式碼中，使用參數名稱來指派值給引數的本機副本。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="2f4e4-125">不會變更呼叫程式碼中的對應值。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f4e4-126">範例</span><span class="sxs-lookup"><span data-stu-id="2f4e4-126">Example</span></span>  
 <span data-ttu-id="2f4e4-127">下列範例會顯示取得陣列變數和操作的兩個程序，其項目上。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="2f4e4-128">`increase`程序只需新增至每個項目。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="2f4e4-129">`replace`程序會將新的陣列指派給參數`a()`，然後新增一個每個項目。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="2f4e4-130">第一個`MsgBox`呼叫會顯示 「 increase(n) 之後：11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="2f4e4-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="2f4e4-131">因為陣列`n`是參考型別`replace`即使的傳遞機制，可以變更其成員， `ByVal`。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="2f4e4-132">第二個`MsgBox`呼叫會顯示 「 replace(n) 之後：101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="2f4e4-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="2f4e4-133">因為`n`傳遞`ByRef`，`replace`可以修改變數`n`呼叫的程式碼中指派給它的新陣列。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="2f4e4-134">因為`n`是參考型別，`replace`也可以變更它的成員。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="2f4e4-135">您可以防止程序修改呼叫程式碼本身的變數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="2f4e4-136">請參閱[如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f4e4-137">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2f4e4-137">Compiling the Code</span></span>  
 <span data-ttu-id="2f4e4-138">當您參考所傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="2f4e4-139">在 Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="2f4e4-140">不過，它是良好的程式設計方式來包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="2f4e4-141">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2f4e4-142">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="2f4e4-142">.NET Framework Security</span></span>  
 <span data-ttu-id="2f4e4-143">允許的程序來變更基礎呼叫程式碼中的引數的值中一律會有潛在的風險。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="2f4e4-144">請確定您預期此值變更，並準備好使用之前，先將這些資料檢查有效性。</span><span class="sxs-lookup"><span data-stu-id="2f4e4-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4e4-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f4e4-145">See also</span></span>

- [<span data-ttu-id="2f4e4-146">程序</span><span class="sxs-lookup"><span data-stu-id="2f4e4-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2f4e4-147">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="2f4e4-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2f4e4-148">HOW TO：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="2f4e4-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="2f4e4-149">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="2f4e4-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="2f4e4-150">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="2f4e4-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="2f4e4-151">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="2f4e4-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="2f4e4-152">HOW TO：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="2f4e4-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="2f4e4-153">HOW TO：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="2f4e4-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="2f4e4-154">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="2f4e4-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="2f4e4-155">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="2f4e4-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
