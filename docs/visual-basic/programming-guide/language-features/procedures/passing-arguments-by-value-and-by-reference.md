---
title: 以傳值和傳址方式傳遞引數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: c23ca51322f57dc13a85c3ea94e0d335dc50ca13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830353"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="ddaac-102">以傳值和傳址方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddaac-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="ddaac-103">在 Visual Basic 中，您可以將引數傳遞至程序*值所*或是*傳址*。</span><span class="sxs-lookup"><span data-stu-id="ddaac-103">In Visual Basic, you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="ddaac-104">這就所謂*傳遞機制*，它決定程序是否可以修改基礎呼叫程式碼中的引數的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ddaac-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="ddaac-105">程序宣告會決定每個參數的傳遞機制，藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ddaac-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="ddaac-106">差異</span><span class="sxs-lookup"><span data-stu-id="ddaac-106">Distinctions</span></span>  
 <span data-ttu-id="ddaac-107">將引數傳遞至程序時, 留意彼此互動的數個不同差異：</span><span class="sxs-lookup"><span data-stu-id="ddaac-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="ddaac-108">基礎的程式設計項目是否為可修改</span><span class="sxs-lookup"><span data-stu-id="ddaac-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="ddaac-109">引數本身是否為可修改</span><span class="sxs-lookup"><span data-stu-id="ddaac-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="ddaac-110">傳值或傳址是否傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ddaac-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="ddaac-111">引數資料類型是否為實值類型或參考型別</span><span class="sxs-lookup"><span data-stu-id="ddaac-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="ddaac-112">如需詳細資訊，請參閱 <<c0> [ 修改之間的差異和不可修改引數](./differences-between-modifiable-and-nonmodifiable-arguments.md)並[差異之間傳遞的引數的值和傳址](./differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ddaac-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="ddaac-113">選擇的傳遞機制</span><span class="sxs-lookup"><span data-stu-id="ddaac-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="ddaac-114">您應該選擇仔細的每個引數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="ddaac-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="ddaac-115">**保護**。</span><span class="sxs-lookup"><span data-stu-id="ddaac-115">**Protection**.</span></span> <span data-ttu-id="ddaac-116">在選擇兩種傳遞機制之間，最重要的準則會是呼叫來變更變數的風險。</span><span class="sxs-lookup"><span data-stu-id="ddaac-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="ddaac-117">傳遞引數的好處`ByRef`是程序可以傳回呼叫的程式碼，透過該引數的值。</span><span class="sxs-lookup"><span data-stu-id="ddaac-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="ddaac-118">傳遞引數的好處`ByVal`是無法變更程序所保護的變數。</span><span class="sxs-lookup"><span data-stu-id="ddaac-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="ddaac-119">**效能**。</span><span class="sxs-lookup"><span data-stu-id="ddaac-119">**Performance**.</span></span> <span data-ttu-id="ddaac-120">雖然的傳遞機制可能會影響您的程式碼的效能，差別在於通常並不顯著。</span><span class="sxs-lookup"><span data-stu-id="ddaac-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="ddaac-121">唯一的例外是傳遞實值型別`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="ddaac-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="ddaac-122">在此情況下，Visual Basic 會複製整個資料內容的引數。</span><span class="sxs-lookup"><span data-stu-id="ddaac-122">In this case, Visual Basic copies the entire data contents of the argument.</span></span> <span data-ttu-id="ddaac-123">因此，對於大數值類型，例如結構，它可能會更有效率，將它傳遞`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="ddaac-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="ddaac-124">若是參考類型，資料指標是複製 （四位元組在 32 位元平台，在 64 位元平台上的八個位元組）。</span><span class="sxs-lookup"><span data-stu-id="ddaac-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="ddaac-125">因此，您可以在其中傳遞的型別引數`String`或`Object`值而不損害效能。</span><span class="sxs-lookup"><span data-stu-id="ddaac-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="ddaac-126">判斷的傳遞機制</span><span class="sxs-lookup"><span data-stu-id="ddaac-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="ddaac-127">程序宣告會指定每個參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="ddaac-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="ddaac-128">呼叫端程式碼無法覆寫`ByVal`機制。</span><span class="sxs-lookup"><span data-stu-id="ddaac-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="ddaac-129">如果參數以宣告`ByRef`，呼叫程式碼可以強制機制`ByVal`方法中呼叫中的括號括住引數名稱。</span><span class="sxs-lookup"><span data-stu-id="ddaac-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="ddaac-130">如需詳細資訊，請參閱[如何：強制以傳值方式傳遞的引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="ddaac-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="ddaac-131">在 Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="ddaac-131">The default in Visual Basic is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="ddaac-132">傳值方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="ddaac-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="ddaac-133">如果引數呼叫的程式碼項目是不可修改的項目，將宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="ddaac-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="ddaac-134">程式碼不可以變更不可修改元素的值。</span><span class="sxs-lookup"><span data-stu-id="ddaac-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="ddaac-135">如果對應的項目是可修改，但您不想要能夠將其值變更的程序，將參數宣告`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="ddaac-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="ddaac-136">呼叫程式碼可以變更可修改的項目，以傳值方式傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="ddaac-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="ddaac-137">傳址方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="ddaac-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="ddaac-138">如果程序確實需要變更呼叫程式碼對應的項目，將對應的參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="ddaac-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="ddaac-139">如果正確執行的程式碼相依於程序來變更呼叫程式碼對應的項目，將參數宣告`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="ddaac-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="ddaac-140">如果您傳遞的值，或如果呼叫程式碼會覆寫`ByRef`傳遞機制，藉由將引數括在括號中的程序呼叫可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="ddaac-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddaac-141">範例</span><span class="sxs-lookup"><span data-stu-id="ddaac-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ddaac-142">描述</span><span class="sxs-lookup"><span data-stu-id="ddaac-142">Description</span></span>  
 <span data-ttu-id="ddaac-143">下列範例會說明何時以傳值方式傳遞引數，以及何時傳址方式傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="ddaac-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="ddaac-144">程序`Calculate`同時具有`ByVal`和`ByRef`參數。</span><span class="sxs-lookup"><span data-stu-id="ddaac-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="ddaac-145">指定的利率， `rate`，和總金額， `debt`，程序的工作是計算的新值`debt`結果的原始值上套用利率的`debt`。</span><span class="sxs-lookup"><span data-stu-id="ddaac-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="ddaac-146">因為`debt`已`ByRef`參數，對應至呼叫端程式碼中的引數的值會反映新的總數`debt`。</span><span class="sxs-lookup"><span data-stu-id="ddaac-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="ddaac-147">參數`rate`已`ByVal`參數因為`Calculate`不應該變更其值。</span><span class="sxs-lookup"><span data-stu-id="ddaac-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ddaac-148">程式碼</span><span class="sxs-lookup"><span data-stu-id="ddaac-148">Code</span></span>  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="ddaac-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddaac-149">See also</span></span>

- [<span data-ttu-id="ddaac-150">程序</span><span class="sxs-lookup"><span data-stu-id="ddaac-150">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ddaac-151">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="ddaac-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ddaac-152">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="ddaac-152">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="ddaac-153">如何：程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="ddaac-153">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="ddaac-154">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="ddaac-154">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="ddaac-155">如何：強制以傳值方式傳遞的引數</span><span class="sxs-lookup"><span data-stu-id="ddaac-155">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="ddaac-156">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ddaac-156">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="ddaac-157">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="ddaac-157">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
