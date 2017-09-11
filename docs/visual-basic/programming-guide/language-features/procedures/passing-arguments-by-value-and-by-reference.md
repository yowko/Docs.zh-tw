---
title: "傳遞引數以傳值或傳址 (Visual Basic) |Microsoft 文件"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 44107171d6f24e22614788470c65cf7ad8d28640
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="ebbee-102">以傳值和傳址方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebbee-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="ebbee-103">在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，您可以將引數傳遞至程序*值*或*傳*。</span><span class="sxs-lookup"><span data-stu-id="ebbee-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="ebbee-104">這稱為*傳遞機制*，它決定程序是否可以修改呼叫程式碼中的引數的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ebbee-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="ebbee-105">程序宣告判斷每個參數的傳遞機制，藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ebbee-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="ebbee-106">差異</span><span class="sxs-lookup"><span data-stu-id="ebbee-106">Distinctions</span></span>  
 <span data-ttu-id="ebbee-107">在將引數傳遞至程序，請注意數個彼此互動的不同差異︰</span><span class="sxs-lookup"><span data-stu-id="ebbee-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="ebbee-108">基礎的程式設計項目是否為可修改</span><span class="sxs-lookup"><span data-stu-id="ebbee-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="ebbee-109">引數本身是否為可修改</span><span class="sxs-lookup"><span data-stu-id="ebbee-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="ebbee-110">傳值或傳址是否傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ebbee-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="ebbee-111">引數資料型別是否為實值類型或參考型別</span><span class="sxs-lookup"><span data-stu-id="ebbee-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="ebbee-112">如需詳細資訊，請參閱[修改之間的差異和不可修改引數](./differences-between-modifiable-and-nonmodifiable-arguments.md)和[差異之間傳遞引數的值和傳址](./differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ebbee-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="ebbee-113">選擇的傳遞機制</span><span class="sxs-lookup"><span data-stu-id="ebbee-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="ebbee-114">您應該選擇每個引數仔細的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="ebbee-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="ebbee-115">**保護**。</span><span class="sxs-lookup"><span data-stu-id="ebbee-115">**Protection**.</span></span> <span data-ttu-id="ebbee-116">在兩種傳遞機制之間選擇，最重要的準則是呼叫變更變數的風險。</span><span class="sxs-lookup"><span data-stu-id="ebbee-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="ebbee-117">傳遞引數的好處`ByRef`是程序可以傳回呼叫程式碼，透過該引數的值。</span><span class="sxs-lookup"><span data-stu-id="ebbee-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="ebbee-118">傳遞引數的好處`ByVal`是它可以避免變數被更改程序。</span><span class="sxs-lookup"><span data-stu-id="ebbee-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="ebbee-119">**效能**。</span><span class="sxs-lookup"><span data-stu-id="ebbee-119">**Performance**.</span></span> <span data-ttu-id="ebbee-120">雖然傳遞機制會影響您的程式碼的效能，差別在於通常並不顯著。</span><span class="sxs-lookup"><span data-stu-id="ebbee-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="ebbee-121">唯一的例外是傳遞實值型別`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="ebbee-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="ebbee-122">在此情況下，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]複製整個資料內容的引數。</span><span class="sxs-lookup"><span data-stu-id="ebbee-122">In this case, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the entire data contents of the argument.</span></span> <span data-ttu-id="ebbee-123">因此，例如結構是大型值型別，它可能會更有效率，將它傳遞`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="ebbee-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="ebbee-124">參考類型的資料指標是複製 （四個位元組 32 位元平台，在 64 位元平台上的 8 個位元組）。</span><span class="sxs-lookup"><span data-stu-id="ebbee-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="ebbee-125">因此，您可以將型別的引數傳遞`String`或`Object`值而不會損害效能。</span><span class="sxs-lookup"><span data-stu-id="ebbee-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="ebbee-126">判斷的傳遞機制</span><span class="sxs-lookup"><span data-stu-id="ebbee-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="ebbee-127">程序宣告會指定每個參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="ebbee-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="ebbee-128">呼叫程式碼無法覆寫`ByVal`機制。</span><span class="sxs-lookup"><span data-stu-id="ebbee-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="ebbee-129">如果參數以宣告`ByRef`，呼叫程式碼可以強制機制`ByVal`引數名稱括在括號內呼叫。</span><span class="sxs-lookup"><span data-stu-id="ebbee-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="ebbee-130">如需詳細資訊，請參閱[如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="ebbee-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="ebbee-131">在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="ebbee-131">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="ebbee-132">傳值方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="ebbee-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="ebbee-133">如果引數呼叫的程式碼項目是不可修改的項目，將對應的參數宣告[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="ebbee-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="ebbee-134">程式碼不可以變更不可修改的元素的值。</span><span class="sxs-lookup"><span data-stu-id="ebbee-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="ebbee-135">如果對應的項目是可修改，但您不想要能夠變更其值的程序，將參數宣告`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="ebbee-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="ebbee-136">呼叫程式碼可以變更可修改的項目，以傳值方式傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="ebbee-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="ebbee-137">傳址方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="ebbee-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="ebbee-138">如果程序確實需要變更對應的項目，在呼叫程式碼中，宣告對應參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="ebbee-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="ebbee-139">如果正確執行的程式碼相依於程序來變更呼叫的程式碼對應的項目，將參數宣告`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="ebbee-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="ebbee-140">如果您傳遞的值，或如果呼叫程式碼會覆寫`ByRef`傳遞機制，透過以括號括住引數的程序呼叫可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="ebbee-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebbee-141">範例</span><span class="sxs-lookup"><span data-stu-id="ebbee-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ebbee-142">描述</span><span class="sxs-lookup"><span data-stu-id="ebbee-142">Description</span></span>  
 <span data-ttu-id="ebbee-143">下列範例會說明何時以傳值方式傳遞引數以及何時參考傳遞給它們。</span><span class="sxs-lookup"><span data-stu-id="ebbee-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="ebbee-144">程序`Calculate`同時具有`ByVal`和`ByRef`參數。</span><span class="sxs-lookup"><span data-stu-id="ebbee-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="ebbee-145">指定利率， `rate`，和總金額， `debt`，程序的工作是計算的新值`debt`也就是套用利率的原始值的結果`debt`。</span><span class="sxs-lookup"><span data-stu-id="ebbee-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="ebbee-146">因為`debt`是`ByRef`參數，呼叫對應的程式碼中的引數的值會反映新總計`debt`。</span><span class="sxs-lookup"><span data-stu-id="ebbee-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="ebbee-147">參數`rate`是`ByVal`參數因為`Calculate`不應該變更其值。</span><span class="sxs-lookup"><span data-stu-id="ebbee-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ebbee-148">程式碼</span><span class="sxs-lookup"><span data-stu-id="ebbee-148">Code</span></span>  
 <span data-ttu-id="ebbee-149">[!code-vb[VbVbcnProcedures #&74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ebbee-149">[!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbee-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebbee-150">See Also</span></span>  
 <span data-ttu-id="ebbee-151">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-151">[Procedures](./index.md) </span></span>  
<span data-ttu-id="ebbee-152"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="ebbee-153"> [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-153"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="ebbee-154"> [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-154"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="ebbee-155"> [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="ebbee-156"> [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="ebbee-157"> [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="ebbee-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="ebbee-158"> [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="ebbee-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
