---
title: 與 Visual Basic 運算子一起執行的一般工作
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], logical
- operators [Visual Basic], string concatenation
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- operators [Visual Basic], arithmetic
- operators [Visual Basic], string comparison
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- operators [Visual Basic], comparison
- operators [Visual Basic], short-circuiting logical
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
ms.openlocfilehash: a8a8d7898e52077fef47b91172e34ad50d7f54e7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075209"
---
# <a name="common-tasks-performed-with-visual-basic-operators"></a><span data-ttu-id="c445a-102">與 Visual Basic 運算子一起執行的一般工作</span><span class="sxs-lookup"><span data-stu-id="c445a-102">Common Tasks Performed with Visual Basic Operators</span></span>

<span data-ttu-id="c445a-103">運算子會執行許多涉及一或多個稱為 *運算元*之運算式的一般工作。</span><span class="sxs-lookup"><span data-stu-id="c445a-103">Operators perform many common tasks involving one or more expressions called *operands*.</span></span>  
  
## <a name="arithmetic-and-bit-shift-tasks"></a><span data-ttu-id="c445a-104">算術和位移位工作</span><span class="sxs-lookup"><span data-stu-id="c445a-104">Arithmetic and Bit-shift Tasks</span></span>  

 <span data-ttu-id="c445a-105">下表摘要說明可用的算術和位移位作業。</span><span class="sxs-lookup"><span data-stu-id="c445a-105">The following table summarizes the available arithmetic and bit-shift operations.</span></span>  
  
|<span data-ttu-id="c445a-106">收件者</span><span class="sxs-lookup"><span data-stu-id="c445a-106">To</span></span>|<span data-ttu-id="c445a-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="c445a-107">See</span></span>|  
|---|---|  
|<span data-ttu-id="c445a-108">將一個數值新增至另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-108">Add one numeric value to another</span></span>|[<span data-ttu-id="c445a-109">+ 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-109">+ Operator</span></span>](../../../language-reference/operators/addition-operator.md)|  
|<span data-ttu-id="c445a-110">從另一個數值減去另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-110">Subtract one numeric value from another</span></span>|[<span data-ttu-id="c445a-111">- 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c445a-111">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="c445a-112">反轉數值的正負號</span><span class="sxs-lookup"><span data-stu-id="c445a-112">Reverse the sign of a numeric value</span></span>|[<span data-ttu-id="c445a-113">- 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c445a-113">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="c445a-114">將一個數位值乘以另一個數值</span><span class="sxs-lookup"><span data-stu-id="c445a-114">Multiply one numeric value by another</span></span>|[<span data-ttu-id="c445a-115">\* 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-115">\* Operator</span></span>](../../../language-reference/operators/multiplication-operator.md)|  
|<span data-ttu-id="c445a-116">將一個數值分割成另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-116">Divide one numeric value into another</span></span>|[<span data-ttu-id="c445a-117">/運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="c445a-117">/ Operator (Visual Basic)</span></span>](../../../language-reference/operators/floating-point-division-operator.md)|  
|<span data-ttu-id="c445a-118">找出某個數值的商除以另一個不含餘數的 () </span><span class="sxs-lookup"><span data-stu-id="c445a-118">Find the quotient of one numeric value divided by another (without the remainder)</span></span>|[<span data-ttu-id="c445a-119">\ 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="c445a-119">\ Operator (Visual Basic)</span></span>](../../../language-reference/operators/integer-division-operator.md)|  
|<span data-ttu-id="c445a-120">找出一個數值的餘數除以另一個沒有商的 (，) </span><span class="sxs-lookup"><span data-stu-id="c445a-120">Find the remainder of one numeric value divided by another (without the quotient)</span></span>|[<span data-ttu-id="c445a-121">Mod 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-121">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)|  
|<span data-ttu-id="c445a-122">將一個數值提高到另一個值的乘冪</span><span class="sxs-lookup"><span data-stu-id="c445a-122">Raise one numeric value to the power of another</span></span>|[<span data-ttu-id="c445a-123">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-123">^ Operator</span></span>](../../../language-reference/operators/exponentiation-operator.md)|  
|<span data-ttu-id="c445a-124">將數值的位模式向左移位</span><span class="sxs-lookup"><span data-stu-id="c445a-124">Shift the bit pattern of a numeric value to the left</span></span>|[<span data-ttu-id="c445a-125"><\< 運算元</span><span class="sxs-lookup"><span data-stu-id="c445a-125"><\< Operator</span></span>](../../../language-reference/operators/left-shift-operator.md)|  
|<span data-ttu-id="c445a-126">將數值的位模式向右移位</span><span class="sxs-lookup"><span data-stu-id="c445a-126">Shift the bit pattern of a numeric value to the right</span></span>|[<span data-ttu-id="c445a-127">>> 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-127">>> Operator</span></span>](../../../language-reference/operators/right-shift-operator.md)|  
  
## <a name="comparison-tasks"></a><span data-ttu-id="c445a-128">比較工作</span><span class="sxs-lookup"><span data-stu-id="c445a-128">Comparison Tasks</span></span>  

 <span data-ttu-id="c445a-129">下表摘要說明可用的比較作業。</span><span class="sxs-lookup"><span data-stu-id="c445a-129">The following table summarizes the available comparison operations.</span></span>  
  
|<span data-ttu-id="c445a-130">收件者</span><span class="sxs-lookup"><span data-stu-id="c445a-130">To</span></span>|<span data-ttu-id="c445a-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="c445a-131">See</span></span>|  
|---|---|  
|<span data-ttu-id="c445a-132">判斷兩個值是否相等</span><span class="sxs-lookup"><span data-stu-id="c445a-132">Determine whether two values are equal</span></span>|<span data-ttu-id="c445a-133">`=` 運算子 ([Visual Basic 中的比較運算子](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="c445a-133">`=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="c445a-134">判斷兩個值是否不相等</span><span class="sxs-lookup"><span data-stu-id="c445a-134">Determine whether two values are unequal</span></span>|<span data-ttu-id="c445a-135">`<>` 運算子 ([Visual Basic 中的比較運算子](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="c445a-135">`<>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="c445a-136">判斷某個值是否小於另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-136">Determine whether one value is less than another</span></span>|<span data-ttu-id="c445a-137">`<` 運算子 ([Visual Basic 中的比較運算子](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="c445a-137">`<` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="c445a-138">判斷某個值是否大於另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-138">Determine whether one value is greater than another</span></span>|<span data-ttu-id="c445a-139">`>` 運算子 ([Visual Basic 中的比較運算子](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="c445a-139">`>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="c445a-140">判斷某個值是否小於或等於另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-140">Determine whether one value is less than or equal to another</span></span>|<span data-ttu-id="c445a-141">`<=` 運算子 ([Visual Basic 中的比較運算子](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="c445a-141">`<=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="c445a-142">判斷某個值是否大於或等於另一個值</span><span class="sxs-lookup"><span data-stu-id="c445a-142">Determine whether one value is greater than or equal to another</span></span>|<span data-ttu-id="c445a-143">`>=` 運算子 ([Visual Basic 中的比較運算子](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="c445a-143">`>=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="c445a-144">判斷兩個物件變數是否參考相同的物件實例</span><span class="sxs-lookup"><span data-stu-id="c445a-144">Determine whether two object variables refer to the same object instance</span></span>|[<span data-ttu-id="c445a-145">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-145">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)|  
|<span data-ttu-id="c445a-146">判斷兩個物件變數是否參考不同的物件實例</span><span class="sxs-lookup"><span data-stu-id="c445a-146">Determine whether two object variables refer to different object instances</span></span>|[<span data-ttu-id="c445a-147">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-147">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)|  
|<span data-ttu-id="c445a-148">判斷物件是否為特定類型</span><span class="sxs-lookup"><span data-stu-id="c445a-148">Determine whether an object is of a specific type</span></span>|[<span data-ttu-id="c445a-149">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-149">TypeOf Operator</span></span>](../../../language-reference/operators/typeof-operator.md)|  
  
## <a name="concatenation-tasks"></a><span data-ttu-id="c445a-150">串連工作</span><span class="sxs-lookup"><span data-stu-id="c445a-150">Concatenation Tasks</span></span>  

 <span data-ttu-id="c445a-151">下表摘要說明可用的串連作業。</span><span class="sxs-lookup"><span data-stu-id="c445a-151">The following table summarizes the available concatenation operations.</span></span>  
  
|<span data-ttu-id="c445a-152">收件者</span><span class="sxs-lookup"><span data-stu-id="c445a-152">To</span></span>|<span data-ttu-id="c445a-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="c445a-153">See</span></span>|  
|---|---|  
|<span data-ttu-id="c445a-154">將多個字串聯結成單一字串</span><span class="sxs-lookup"><span data-stu-id="c445a-154">Join multiple strings into a single string</span></span>|<span data-ttu-id="c445a-155">`&`運算子 ([Visual Basic) 中的串連運算子](concatenation-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c445a-155">`&` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
|<span data-ttu-id="c445a-156">使用字串值聯結數值</span><span class="sxs-lookup"><span data-stu-id="c445a-156">Join numeric values with string values</span></span>|<span data-ttu-id="c445a-157">`+`運算子 ([Visual Basic) 中的串連運算子](concatenation-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c445a-157">`+` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
  
## <a name="logical-and-bitwise-tasks"></a><span data-ttu-id="c445a-158">邏輯和位工作</span><span class="sxs-lookup"><span data-stu-id="c445a-158">Logical and Bitwise Tasks</span></span>  

 <span data-ttu-id="c445a-159">下表摘要說明可用的邏輯和位運算。</span><span class="sxs-lookup"><span data-stu-id="c445a-159">The following table summarizes the available logical and bitwise operations.</span></span>  
  
|<span data-ttu-id="c445a-160">收件者</span><span class="sxs-lookup"><span data-stu-id="c445a-160">To</span></span>|<span data-ttu-id="c445a-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="c445a-161">See</span></span>|  
|---|---|  
|<span data-ttu-id="c445a-162">針對布林值執行邏輯否定</span><span class="sxs-lookup"><span data-stu-id="c445a-162">Perform logical negation on a Boolean value</span></span>|[<span data-ttu-id="c445a-163">Not 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-163">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
|<span data-ttu-id="c445a-164">在兩個布林值上執行邏輯結合</span><span class="sxs-lookup"><span data-stu-id="c445a-164">Perform logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="c445a-165">And 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-165">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="c445a-166">對兩個布林值執行內含邏輯分離</span><span class="sxs-lookup"><span data-stu-id="c445a-166">Perform inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="c445a-167">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-167">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="c445a-168">對兩個布林值執行獨佔邏輯分離</span><span class="sxs-lookup"><span data-stu-id="c445a-168">Perform exclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="c445a-169">Xor 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-169">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="c445a-170">在兩個布林值上執行縮短邏輯結合</span><span class="sxs-lookup"><span data-stu-id="c445a-170">Perform short-circuited logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="c445a-171">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-171">AndAlso Operator</span></span>](../../../language-reference/operators/andalso-operator.md)|  
|<span data-ttu-id="c445a-172">在兩個布林值上執行簡短縮短內含邏輯分離</span><span class="sxs-lookup"><span data-stu-id="c445a-172">Perform short-circuited inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="c445a-173">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-173">OrElse Operator</span></span>](../../../language-reference/operators/orelse-operator.md)|  
|<span data-ttu-id="c445a-174">在兩個整數值上執行位邏輯結合</span><span class="sxs-lookup"><span data-stu-id="c445a-174">Perform bit-by-bit logical conjunction on two integral values</span></span>|[<span data-ttu-id="c445a-175">And 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-175">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="c445a-176">在兩個整數值上執行位對包含邏輯分離</span><span class="sxs-lookup"><span data-stu-id="c445a-176">Perform bit-by-bit inclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="c445a-177">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-177">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="c445a-178">在兩個整數值上執行位互斥邏輯分離</span><span class="sxs-lookup"><span data-stu-id="c445a-178">Perform bit-by-bit exclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="c445a-179">Xor 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-179">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="c445a-180">在整數值上執行位邏輯否定</span><span class="sxs-lookup"><span data-stu-id="c445a-180">Perform bit-by-bit logical negation on an integral value</span></span>|[<span data-ttu-id="c445a-181">Not 運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-181">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c445a-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c445a-182">See also</span></span>

- [<span data-ttu-id="c445a-183">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="c445a-183">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="c445a-184">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="c445a-184">Operators Listed by Functionality</span></span>](../../../language-reference/operators/operators-listed-by-functionality.md)
