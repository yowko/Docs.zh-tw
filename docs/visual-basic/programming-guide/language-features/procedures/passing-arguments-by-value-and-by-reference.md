---
title: 以傳值和傳址方式傳遞引數
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 28e59753a35ab67b15fbc549df5bb8a3489aba5a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352611"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="06f13-102">以傳值和傳址方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06f13-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="06f13-103">在 Visual Basic 中，您可以透過*值*或傳*址*方式將引數傳遞給程式。</span><span class="sxs-lookup"><span data-stu-id="06f13-103">In Visual Basic, you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="06f13-104">這就是所謂的*傳遞機制*，它會判斷程式是否可以修改呼叫程式碼中引數基礎的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="06f13-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="06f13-105">程式宣告會藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字，來判斷每個參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="06f13-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="06f13-106">加以</span><span class="sxs-lookup"><span data-stu-id="06f13-106">Distinctions</span></span>  
 <span data-ttu-id="06f13-107">將引數傳遞至程式時，請留意幾個彼此互動的不同區別：</span><span class="sxs-lookup"><span data-stu-id="06f13-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
- <span data-ttu-id="06f13-108">基礎程式設計項目是否為可修改或不可修改</span><span class="sxs-lookup"><span data-stu-id="06f13-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
- <span data-ttu-id="06f13-109">引數本身是否為可修改或不可變</span><span class="sxs-lookup"><span data-stu-id="06f13-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
- <span data-ttu-id="06f13-110">引數是以傳值方式或依參考方式傳遞</span><span class="sxs-lookup"><span data-stu-id="06f13-110">Whether the argument is being passed by value or by reference</span></span>  
  
- <span data-ttu-id="06f13-111">引數資料類型是否為實數值型別或參考型別</span><span class="sxs-lookup"><span data-stu-id="06f13-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="06f13-112">如需詳細資訊，請參閱可[修改的和不可變的引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)，以及透過[值和傳址方式傳遞引數的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="06f13-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="06f13-113">選擇傳遞機制</span><span class="sxs-lookup"><span data-stu-id="06f13-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="06f13-114">您應該針對每個引數仔細選擇傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="06f13-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
- <span data-ttu-id="06f13-115">**保護**。</span><span class="sxs-lookup"><span data-stu-id="06f13-115">**Protection**.</span></span> <span data-ttu-id="06f13-116">在兩個傳遞機制之間選擇時，最重要的條件是公開呼叫變數以進行變更。</span><span class="sxs-lookup"><span data-stu-id="06f13-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="06f13-117">傳遞引數 `ByRef` 的優點是程式可以透過該引數將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="06f13-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="06f13-118">傳遞引數 `ByVal` 的優點是它會保護變數，使其不會被程式變更。</span><span class="sxs-lookup"><span data-stu-id="06f13-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
- <span data-ttu-id="06f13-119">**效能**。</span><span class="sxs-lookup"><span data-stu-id="06f13-119">**Performance**.</span></span> <span data-ttu-id="06f13-120">雖然傳遞機制可能會影響您程式碼的效能，但兩者之間的差異通常不明顯。</span><span class="sxs-lookup"><span data-stu-id="06f13-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="06f13-121">其中一個例外狀況是傳遞 `ByVal`的實值型別。</span><span class="sxs-lookup"><span data-stu-id="06f13-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="06f13-122">在此情況下，Visual Basic 會複製引數的整個資料內容。</span><span class="sxs-lookup"><span data-stu-id="06f13-122">In this case, Visual Basic copies the entire data contents of the argument.</span></span> <span data-ttu-id="06f13-123">因此，對於大型實數值型別（例如結構），將它傳遞 `ByRef`會更有效率。</span><span class="sxs-lookup"><span data-stu-id="06f13-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="06f13-124">針對參考型別，只會複製資料的指標（32位平臺上的四個位元組，64位平臺上為8個位元組）。</span><span class="sxs-lookup"><span data-stu-id="06f13-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="06f13-125">因此，您可以將類型 `String` 或 `Object` 的引數傳遞給值，而不會犧牲效能。</span><span class="sxs-lookup"><span data-stu-id="06f13-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="06f13-126">判斷傳遞機制</span><span class="sxs-lookup"><span data-stu-id="06f13-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="06f13-127">程式宣告會指定每個參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="06f13-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="06f13-128">呼叫程式碼無法覆寫 `ByVal` 機制。</span><span class="sxs-lookup"><span data-stu-id="06f13-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="06f13-129">如果參數是使用 `ByRef`所宣告，則呼叫程式碼可以藉由在呼叫的括弧中括住引數名稱，強制將機制 `ByVal`。</span><span class="sxs-lookup"><span data-stu-id="06f13-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="06f13-130">如需詳細資訊，請參閱[如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="06f13-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="06f13-131">Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="06f13-131">The default in Visual Basic is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="06f13-132">以傳值方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="06f13-132">When to Pass an Argument by Value</span></span>  
  
- <span data-ttu-id="06f13-133">如果引數基礎的呼叫程式碼元素是無法修改的元素，請宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="06f13-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="06f13-134">沒有任何程式碼可以變更無法修改的元素值。</span><span class="sxs-lookup"><span data-stu-id="06f13-134">No code can change the value of a nonmodifiable element.</span></span>  
  
- <span data-ttu-id="06f13-135">如果基礎元素是可修改的，但您不想讓程式能夠變更其值，請 `ByVal`宣告參數。</span><span class="sxs-lookup"><span data-stu-id="06f13-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="06f13-136">只有呼叫程式碼可以變更以傳值方式傳遞之可修改元素的值。</span><span class="sxs-lookup"><span data-stu-id="06f13-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="06f13-137">以傳址方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="06f13-137">When to Pass an Argument by Reference</span></span>  
  
- <span data-ttu-id="06f13-138">如果程式確實需要變更呼叫程式碼中的基礎元素，請宣告對應的參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="06f13-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
- <span data-ttu-id="06f13-139">如果程式碼的正確執行取決於變更呼叫程式碼中基礎元素的程式，請 `ByRef`宣告參數。</span><span class="sxs-lookup"><span data-stu-id="06f13-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="06f13-140">如果您以傳值方式傳遞它，或是呼叫程式碼藉由以括弧括住引數來覆寫 `ByRef` 傳遞機制，則程序呼叫可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="06f13-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f13-141">範例</span><span class="sxs-lookup"><span data-stu-id="06f13-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="06f13-142">描述</span><span class="sxs-lookup"><span data-stu-id="06f13-142">Description</span></span>  
 <span data-ttu-id="06f13-143">下列範例說明何時以傳值方式傳遞引數，以及何時以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="06f13-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="06f13-144">程式 `Calculate` 同時具有 `ByVal` 和 `ByRef` 參數。</span><span class="sxs-lookup"><span data-stu-id="06f13-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="06f13-145">假設有利率、`rate`和 money 的總和，`debt`，程式的工作就是為 `debt` 計算新的值，這是將利率套用至原始 `debt`值的結果。</span><span class="sxs-lookup"><span data-stu-id="06f13-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="06f13-146">因為 `debt` 是 `ByRef` 參數，所以新的總計會反映在呼叫程式碼中對應至 `debt`的引數值。</span><span class="sxs-lookup"><span data-stu-id="06f13-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="06f13-147">參數 `rate` 是 `ByVal` 參數，因為 `Calculate` 不應變更其值。</span><span class="sxs-lookup"><span data-stu-id="06f13-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="06f13-148">程式碼</span><span class="sxs-lookup"><span data-stu-id="06f13-148">Code</span></span>  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="06f13-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="06f13-149">See also</span></span>

- [<span data-ttu-id="06f13-150">程序</span><span class="sxs-lookup"><span data-stu-id="06f13-150">Procedures</span></span>](./index.md)
- [<span data-ttu-id="06f13-151">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="06f13-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="06f13-152">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="06f13-152">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="06f13-153">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="06f13-153">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="06f13-154">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="06f13-154">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="06f13-155">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="06f13-155">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="06f13-156">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="06f13-156">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="06f13-157">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="06f13-157">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
