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
ms.openlocfilehash: b7430b209f53a0a924ec587a0097178baf0075e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059210"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="9790c-102">以傳值和傳址方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9790c-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>

<span data-ttu-id="9790c-103">在 Visual Basic 中，您可以透過傳 *值* 或傳 *址*方式將引數傳遞給程式。</span><span class="sxs-lookup"><span data-stu-id="9790c-103">In Visual Basic, you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="9790c-104">這就是所謂的 *傳遞機制*，它會判斷程式是否可以修改呼叫程式碼中引數的基礎程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="9790c-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="9790c-105">程式聲明會藉由指定 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) 關鍵字來判斷每個參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="9790c-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="9790c-106">區別</span><span class="sxs-lookup"><span data-stu-id="9790c-106">Distinctions</span></span>  

 <span data-ttu-id="9790c-107">將引數傳遞給程式時，請注意幾個不同的差異，這些差異會彼此互動：</span><span class="sxs-lookup"><span data-stu-id="9790c-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
- <span data-ttu-id="9790c-108">基礎程式設計專案是否可修改或不可修改</span><span class="sxs-lookup"><span data-stu-id="9790c-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
- <span data-ttu-id="9790c-109">引數本身是否可修改或不可修改</span><span class="sxs-lookup"><span data-stu-id="9790c-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
- <span data-ttu-id="9790c-110">引數是否以傳值或傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="9790c-110">Whether the argument is being passed by value or by reference</span></span>  
  
- <span data-ttu-id="9790c-111">引數資料類型是否為實值型別或參考型別</span><span class="sxs-lookup"><span data-stu-id="9790c-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="9790c-112">如需詳細資訊，請參閱可 [修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md) ，以及透過 [傳值和傳址方式傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="9790c-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="9790c-113">傳遞機制的選擇</span><span class="sxs-lookup"><span data-stu-id="9790c-113">Choice of Passing Mechanism</span></span>  

 <span data-ttu-id="9790c-114">您應該為每個引數選擇謹慎的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="9790c-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
- <span data-ttu-id="9790c-115">**保護**。</span><span class="sxs-lookup"><span data-stu-id="9790c-115">**Protection**.</span></span> <span data-ttu-id="9790c-116">在兩個傳遞機制之間進行選擇時，最重要的準則是暴露呼叫變數以進行變更。</span><span class="sxs-lookup"><span data-stu-id="9790c-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="9790c-117">傳遞引數的優點是，程式 `ByRef` 可以透過該引數將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="9790c-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="9790c-118">傳遞引數的優點 `ByVal` 是它會保護變數，使其無法被程式變更。</span><span class="sxs-lookup"><span data-stu-id="9790c-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
- <span data-ttu-id="9790c-119">**效能**。</span><span class="sxs-lookup"><span data-stu-id="9790c-119">**Performance**.</span></span> <span data-ttu-id="9790c-120">雖然傳遞機制可能會影響程式碼的效能，但差異通常不重要。</span><span class="sxs-lookup"><span data-stu-id="9790c-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="9790c-121">其中一個例外狀況是傳遞的實值型別 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="9790c-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="9790c-122">在此情況下，Visual Basic 會複製引數的整個資料內容。</span><span class="sxs-lookup"><span data-stu-id="9790c-122">In this case, Visual Basic copies the entire data contents of the argument.</span></span> <span data-ttu-id="9790c-123">因此，針對大型數值型別（例如結構），傳遞它可能更有效率 `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="9790c-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="9790c-124">若為參考型別，則只會將資料指標複製到32位平臺上的四個位元組 (四個位元組，) 64 位平臺上的8個位元組。</span><span class="sxs-lookup"><span data-stu-id="9790c-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="9790c-125">因此，您可以傳遞類型或傳值的引數， `String` `Object` 而不會犧牲效能。</span><span class="sxs-lookup"><span data-stu-id="9790c-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="9790c-126">判斷傳遞機制</span><span class="sxs-lookup"><span data-stu-id="9790c-126">Determination of the Passing Mechanism</span></span>  

 <span data-ttu-id="9790c-127">程式聲明會指定每個參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="9790c-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="9790c-128">呼叫程式碼無法覆寫 `ByVal` 機制。</span><span class="sxs-lookup"><span data-stu-id="9790c-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="9790c-129">如果以宣告參數 `ByRef` ，呼叫程式碼可以在 `ByVal` 呼叫中將引數名稱括在括弧中，以強制執行機制。</span><span class="sxs-lookup"><span data-stu-id="9790c-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="9790c-130">如需詳細資訊，請參閱 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="9790c-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="9790c-131">Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="9790c-131">The default in Visual Basic is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="9790c-132">以傳值方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="9790c-132">When to Pass an Argument by Value</span></span>  
  
- <span data-ttu-id="9790c-133">如果引數基礎的呼叫程式碼專案是不可修改的元素，請宣告對應的參數 [ByVal](../../../language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="9790c-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="9790c-134">沒有任何程式碼可以變更不可變更元素的值。</span><span class="sxs-lookup"><span data-stu-id="9790c-134">No code can change the value of a nonmodifiable element.</span></span>  
  
- <span data-ttu-id="9790c-135">如果基礎元素是可修改的，但您不想讓程式變更其值，請宣告參數 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="9790c-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="9790c-136">只有呼叫程式碼可以變更以傳值方式傳遞的可修改元素值。</span><span class="sxs-lookup"><span data-stu-id="9790c-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="9790c-137">以傳址方式傳遞引數的時機</span><span class="sxs-lookup"><span data-stu-id="9790c-137">When to Pass an Argument by Reference</span></span>  
  
- <span data-ttu-id="9790c-138">如果程式真的需要變更呼叫程式碼中的基礎元素，請宣告對應的參數 [ByRef](../../../language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="9790c-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../language-reference/modifiers/byref.md).</span></span>  
  
- <span data-ttu-id="9790c-139">如果正確的程式碼執行取決於變更呼叫程式碼中基礎專案的程式，請宣告參數 `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="9790c-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="9790c-140">如果您以傳值方式傳遞，或呼叫 `ByRef` 程式碼以括弧括住引數來覆寫傳遞機制，則程序呼叫可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="9790c-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9790c-141">範例</span><span class="sxs-lookup"><span data-stu-id="9790c-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9790c-142">描述</span><span class="sxs-lookup"><span data-stu-id="9790c-142">Description</span></span>  

 <span data-ttu-id="9790c-143">下列範例說明何時以傳值方式傳遞引數，以及何時以傳址方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="9790c-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="9790c-144">程式 `Calculate` 同時有 `ByVal` 和 `ByRef` 參數。</span><span class="sxs-lookup"><span data-stu-id="9790c-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="9790c-145">如果有利率和 money 的總和，程式的工作 `rate` `debt` 就是計算的新值， `debt` 這是將利率套用至原始值的結果 `debt` 。</span><span class="sxs-lookup"><span data-stu-id="9790c-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="9790c-146">因為 `debt` 是 `ByRef` 參數，所以新的總計會反映在呼叫程式碼中對應至的引數值 `debt` 。</span><span class="sxs-lookup"><span data-stu-id="9790c-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="9790c-147">參數 `rate` 是 `ByVal` 參數，因為 `Calculate` 不應該變更其值。</span><span class="sxs-lookup"><span data-stu-id="9790c-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9790c-148">程式碼</span><span class="sxs-lookup"><span data-stu-id="9790c-148">Code</span></span>  

 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="9790c-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9790c-149">See also</span></span>

- [<span data-ttu-id="9790c-150">程序</span><span class="sxs-lookup"><span data-stu-id="9790c-150">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9790c-151">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="9790c-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9790c-152">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="9790c-152">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="9790c-153">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="9790c-153">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="9790c-154">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="9790c-154">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="9790c-155">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="9790c-155">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="9790c-156">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="9790c-156">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="9790c-157">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="9790c-157">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
