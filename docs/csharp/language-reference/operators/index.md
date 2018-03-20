---
title: "C# 運算子"
ms.date: 03/09/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f18c2332f3576847800423c5c0bf7471bf37aafc
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="c-operators"></a><span data-ttu-id="09785-102">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-102">C# Operators</span></span>
<span data-ttu-id="09785-103">C# 提供許多運算子，也就是指定要在運算式中執行哪些作業 (數學、索引化、函式呼叫等) 的符號。</span><span class="sxs-lookup"><span data-stu-id="09785-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span>  <span data-ttu-id="09785-104">您可以[多載](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)許多運算子，以便在套用至使用者定義型別時變更它們的意義。</span><span class="sxs-lookup"><span data-stu-id="09785-104">You can [overload](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>  
  
 <span data-ttu-id="09785-105">列舉 (`enum`) 型別上通常會允許整數型別上的作業 (例如 `==`、`!=`、`<`、`>`、`&`、`|`)。</span><span class="sxs-lookup"><span data-stu-id="09785-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>  
  
 <span data-ttu-id="09785-106">這些區段列出 C# 運算子，從最高優先順序開始到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="09785-106">The sections lists the C# operators starting with the highest precedence to the lowest.</span></span>  <span data-ttu-id="09785-107">每個區段中的運算子會共用相同的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="09785-107">The operators within each section share the same precedence level.</span></span>  
  
## <a name="primary-operators"></a><span data-ttu-id="09785-108">主要運算子</span><span class="sxs-lookup"><span data-stu-id="09785-108">Primary Operators</span></span>  
 <span data-ttu-id="09785-109">這些是最高優先順序的運算子。</span><span class="sxs-lookup"><span data-stu-id="09785-109">These are the highest precedence operators.</span></span>  <span data-ttu-id="09785-110">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-110">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-111">[x.y](../../../csharp/language-reference/operators/member-access-operator.md) – 成員存取。</span><span class="sxs-lookup"><span data-stu-id="09785-111">[x.y](../../../csharp/language-reference/operators/member-access-operator.md) – member access.</span></span>  
  
 <span data-ttu-id="09785-112">[x?.y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null 條件成員存取。</span><span class="sxs-lookup"><span data-stu-id="09785-112">[x?.y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null conditional member access.</span></span>  <span data-ttu-id="09785-113">如果左運算元為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="09785-113">Returns `null` if the left-hand operand is `null`.</span></span>  
 
 <span data-ttu-id="09785-114">[x?[y]](../../../csharp/language-reference/operators/null-conditional-operators.md) - null 條件式索引存取。</span><span class="sxs-lookup"><span data-stu-id="09785-114">[x?[y]](../../../csharp/language-reference/operators/null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="09785-115">如果左運算元為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="09785-115">Returns `null` if the left-hand operand is `null`.</span></span>
 
 <span data-ttu-id="09785-116">[f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – 函式引動過程。</span><span class="sxs-lookup"><span data-stu-id="09785-116">[f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – function invocation.</span></span>  
  
 <span data-ttu-id="09785-117">[a&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) – 彙總物件索引化。</span><span class="sxs-lookup"><span data-stu-id="09785-117">[a&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) – aggregate object indexing.</span></span>  
   
 <span data-ttu-id="09785-118">[x++](../../../csharp/language-reference/operators/increment-operator.md) – 後置遞增。</span><span class="sxs-lookup"><span data-stu-id="09785-118">[x++](../../../csharp/language-reference/operators/increment-operator.md) – postfix increment.</span></span>  <span data-ttu-id="09785-119">傳回 x 的值，然後利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="09785-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>  
  
 <span data-ttu-id="09785-120">[x--](../../../csharp/language-reference/operators/decrement-operator.md) – 後置遞減。</span><span class="sxs-lookup"><span data-stu-id="09785-120">[x--](../../../csharp/language-reference/operators/decrement-operator.md) –  postfix decrement.</span></span>  <span data-ttu-id="09785-121">傳回 x 的值，然後利用小於 x 值的值 (通常會減去整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="09785-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>  
  
 <span data-ttu-id="09785-122">[new](../../../csharp/language-reference/keywords/new-operator.md) – 型別執行個體化。</span><span class="sxs-lookup"><span data-stu-id="09785-122">[new](../../../csharp/language-reference/keywords/new-operator.md) – type instantiation.</span></span>  
  
 <span data-ttu-id="09785-123">[typeof](../../../csharp/language-reference/keywords/typeof.md) – 傳回代表運算元的 System.Type 物件。</span><span class="sxs-lookup"><span data-stu-id="09785-123">[typeof](../../../csharp/language-reference/keywords/typeof.md) – returns the System.Type object representing the operand.</span></span>  
  
 <span data-ttu-id="09785-124">[checked](../../../csharp/language-reference/keywords/checked.md) – 啟動整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="09785-124">[checked](../../../csharp/language-reference/keywords/checked.md) – enables overflow checking for integer operations.</span></span>  
  
 <span data-ttu-id="09785-125">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) – 停用整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="09785-125">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) – disables overflow checking for integer operations.</span></span>  <span data-ttu-id="09785-126">這是預設編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="09785-126">This is the default compiler behavior.</span></span>  
  
 <span data-ttu-id="09785-127">[default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – 傳回 T 型別的預設值，參考型別為 `null`、數字型別為零，而結構型別的成員則填入零/`null`。</span><span class="sxs-lookup"><span data-stu-id="09785-127">[default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – returns the default value of type T, `null` for reference types, zero for numeric types, and zero/`null` filled in members for struct types.</span></span>  
  
 <span data-ttu-id="09785-128">[delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="09785-128">[delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>  
  
 <span data-ttu-id="09785-129">[sizeof](../../../csharp/language-reference/keywords/sizeof.md) – 傳回型別運算元的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="09785-129">[sizeof](../../../csharp/language-reference/keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>  
  
 <span data-ttu-id="09785-130">[->](../../../csharp/language-reference/operators/dereference-operator.md) – 指標取值結合成員存取。</span><span class="sxs-lookup"><span data-stu-id="09785-130">[->](../../../csharp/language-reference/operators/dereference-operator.md) – pointer dereferencing combined with member access.</span></span>  
  
## <a name="unary-operators"></a><span data-ttu-id="09785-131">一元運算子</span><span class="sxs-lookup"><span data-stu-id="09785-131">Unary Operators</span></span>  
 <span data-ttu-id="09785-132">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-132">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-133">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-133">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-134">[+x](../../../csharp/language-reference/operators/addition-operator.md) – 傳回 x 的值。</span><span class="sxs-lookup"><span data-stu-id="09785-134">[+x](../../../csharp/language-reference/operators/addition-operator.md) – returns the value of x.</span></span>  
  
 <span data-ttu-id="09785-135">[-x](../../../csharp/language-reference/operators/subtraction-operator.md) – 數值否定。</span><span class="sxs-lookup"><span data-stu-id="09785-135">[-x](../../../csharp/language-reference/operators/subtraction-operator.md) – numeric negation.</span></span>  
  
 <span data-ttu-id="09785-136">[\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – 邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="09785-136">[\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – logical negation.</span></span>  
  
 <span data-ttu-id="09785-137">[~x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – 位元補數。</span><span class="sxs-lookup"><span data-stu-id="09785-137">[~x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – bitwise complement.</span></span>  
  
 <span data-ttu-id="09785-138">[++x](../../../csharp/language-reference/operators/increment-operator.md) – 前置遞增。</span><span class="sxs-lookup"><span data-stu-id="09785-138">[++x](../../../csharp/language-reference/operators/increment-operator.md) – prefix increment.</span></span>  <span data-ttu-id="09785-139">傳回 x 的值之前，利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="09785-139">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>  
  
 <span data-ttu-id="09785-140">[--x](../../../csharp/language-reference/operators/decrement-operator.md) – 前置遞減。</span><span class="sxs-lookup"><span data-stu-id="09785-140">[--x](../../../csharp/language-reference/operators/decrement-operator.md) – prefix decrement.</span></span>  <span data-ttu-id="09785-141">更新儲存體位置之後，傳回 x 減一的 x 值 (通常減去整數 1)。</span><span class="sxs-lookup"><span data-stu-id="09785-141">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>  
  
 <span data-ttu-id="09785-142">[(T)x](../../../csharp/language-reference/operators/invocation-operator.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="09785-142">[(T)x](../../../csharp/language-reference/operators/invocation-operator.md) – type casting.</span></span>  
  
 <span data-ttu-id="09785-143">[await](../../../csharp/language-reference/keywords/await.md) – 等候 `Task`。</span><span class="sxs-lookup"><span data-stu-id="09785-143">[await](../../../csharp/language-reference/keywords/await.md) – awaits a `Task`.</span></span>  
  
 <span data-ttu-id="09785-144">[&x](../../../csharp/language-reference/operators/and-operator.md) – 位址。</span><span class="sxs-lookup"><span data-stu-id="09785-144">[&x](../../../csharp/language-reference/operators/and-operator.md) – address of.</span></span>  
  
 <span data-ttu-id="09785-145">[\*x](../../../csharp/language-reference/operators/multiplication-operator.md) – 取值。</span><span class="sxs-lookup"><span data-stu-id="09785-145">[\*x](../../../csharp/language-reference/operators/multiplication-operator.md) – dereferencing.</span></span>  
  
## <a name="multiplicative-operators"></a><span data-ttu-id="09785-146">乘法類運算子</span><span class="sxs-lookup"><span data-stu-id="09785-146">Multiplicative Operators</span></span>  
 <span data-ttu-id="09785-147">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-147">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-148">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-148">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-149">[x \* y](../../../csharp/language-reference/operators/multiplication-operator.md) – 乘法。</span><span class="sxs-lookup"><span data-stu-id="09785-149">[x \* y](../../../csharp/language-reference/operators/multiplication-operator.md) – multiplication.</span></span>  
  
 <span data-ttu-id="09785-150">[x / y](../../../csharp/language-reference/operators/division-operator.md) – 除法。</span><span class="sxs-lookup"><span data-stu-id="09785-150">[x / y](../../../csharp/language-reference/operators/division-operator.md) – division.</span></span>  <span data-ttu-id="09785-151">如果運算元都是整數，則結果會截斷趨近於零的整數 (例如，`-7 / 2 is -3`)。</span><span class="sxs-lookup"><span data-stu-id="09785-151">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>  
  
 <span data-ttu-id="09785-152">[x % y](../../../csharp/language-reference/operators/modulus-operator.md) – 模數。</span><span class="sxs-lookup"><span data-stu-id="09785-152">[x % y](../../../csharp/language-reference/operators/modulus-operator.md) – modulus.</span></span>  <span data-ttu-id="09785-153">如果運算元都是整數，這會傳回 x 除以 y 的餘數。</span><span class="sxs-lookup"><span data-stu-id="09785-153">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="09785-154">若為 `q = x / y` 和 `r = x % y`，則為 `x = q * y + r`。</span><span class="sxs-lookup"><span data-stu-id="09785-154">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>  
  
## <a name="additive-operators"></a><span data-ttu-id="09785-155">加法類運算子</span><span class="sxs-lookup"><span data-stu-id="09785-155">Additive Operators</span></span>  
 <span data-ttu-id="09785-156">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-156">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-157">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-157">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-158">[x + y](../../../csharp/language-reference/operators/addition-operator.md) – 加法。</span><span class="sxs-lookup"><span data-stu-id="09785-158">[x + y](../../../csharp/language-reference/operators/addition-operator.md) – addition.</span></span>  
  
 <span data-ttu-id="09785-159">[x – y](../../../csharp/language-reference/operators/subtraction-operator.md) – 減法。</span><span class="sxs-lookup"><span data-stu-id="09785-159">[x – y](../../../csharp/language-reference/operators/subtraction-operator.md) – subtraction.</span></span>  
  
## <a name="shift-operators"></a><span data-ttu-id="09785-160">移位運算子</span><span class="sxs-lookup"><span data-stu-id="09785-160">Shift Operators</span></span>  
 <span data-ttu-id="09785-161">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-161">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-162">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-162">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-163">[x <\<  y](../../../csharp/language-reference/operators/left-shift-operator.md) – 位元向左移位並使用右邊的零填滿。</span><span class="sxs-lookup"><span data-stu-id="09785-163">[x <\<  y](../../../csharp/language-reference/operators/left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>  
  
 <span data-ttu-id="09785-164">[x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – 位元向右移位。</span><span class="sxs-lookup"><span data-stu-id="09785-164">[x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – shift bits right.</span></span>  <span data-ttu-id="09785-165">如果左運算元是 `int` 或 `long`，則以正負號位元填入左位元。</span><span class="sxs-lookup"><span data-stu-id="09785-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span>  <span data-ttu-id="09785-166">如果左運算元是 `uint` 或 `ulong`，則以零填入左位元。</span><span class="sxs-lookup"><span data-stu-id="09785-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>  
  
## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="09785-167">關係和類型測試運算子</span><span class="sxs-lookup"><span data-stu-id="09785-167">Relational and Type-testing Operators</span></span>  
 <span data-ttu-id="09785-168">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-169">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-169">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-170">[x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – 小於 (如果 x 小於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="09785-170">[x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – less than (true if x is less than y).</span></span>  
  
 <span data-ttu-id="09785-171">[x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – 大於 (如果 x 大於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="09785-171">[x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – greater than (true if x is greater than y).</span></span>  
  
 <span data-ttu-id="09785-172">[x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – 小於或等於。</span><span class="sxs-lookup"><span data-stu-id="09785-172">[x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – less than or equal to.</span></span>  
  
 <span data-ttu-id="09785-173">[x >= y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – 大於或等於。</span><span class="sxs-lookup"><span data-stu-id="09785-173">[x >= y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – greater than or equal to.</span></span>  
  
 <span data-ttu-id="09785-174">[is](../../../csharp/language-reference/keywords/is.md) – 型別相容性。</span><span class="sxs-lookup"><span data-stu-id="09785-174">[is](../../../csharp/language-reference/keywords/is.md) – type compatibility.</span></span>  <span data-ttu-id="09785-175">如果評估的左運算元可以轉換成右運算元中指定的類型 (靜態類型)，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="09785-175">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>  
  
 <span data-ttu-id="09785-176">[as](../../../csharp/language-reference/keywords/as.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="09785-176">[as](../../../csharp/language-reference/keywords/as.md) – type conversion.</span></span>  <span data-ttu-id="09785-177">傳回的左運算元轉型為右運算元指定的類型 (靜態類型)，但 `as` 傳回 `null`，其中 `(T)x` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="09785-177">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="09785-178">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="09785-178">Equality Operators</span></span>  
 <span data-ttu-id="09785-179">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-179">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-180">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-180">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-181">[x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – 相等。</span><span class="sxs-lookup"><span data-stu-id="09785-181">[x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – equality.</span></span>  <span data-ttu-id="09785-182">根據預設，對於 `string` 以外的參考類型，這會傳回參考相等 (識別測試)。</span><span class="sxs-lookup"><span data-stu-id="09785-182">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span>  <span data-ttu-id="09785-183">不過，類型可以多載 `==`，因此如果您的目的是要測試識別，最好使用 `object` 上的 `ReferenceEquals` 方法。</span><span class="sxs-lookup"><span data-stu-id="09785-183">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>  
  
 <span data-ttu-id="09785-184">[x != y](../../../csharp/language-reference/operators/not-equal-operator.md) – 不等於。</span><span class="sxs-lookup"><span data-stu-id="09785-184">[x != y](../../../csharp/language-reference/operators/not-equal-operator.md) – not equal.</span></span>  <span data-ttu-id="09785-185">請參閱 `==` 的註解。</span><span class="sxs-lookup"><span data-stu-id="09785-185">See comment for `==`.</span></span>  <span data-ttu-id="09785-186">如果類型多載 `==`，則它必須多載 `!=`。</span><span class="sxs-lookup"><span data-stu-id="09785-186">If a type overloads `==`, then it must overload `!=`.</span></span>  
  
## <a name="logical-and-operator"></a><span data-ttu-id="09785-187">邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-187">Logical AND Operator</span></span>  
 <span data-ttu-id="09785-188">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-188">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-189">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-189">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-190">[x & y](../../../csharp/language-reference/operators/and-operator.md) – 邏輯或位元 AND。</span><span class="sxs-lookup"><span data-stu-id="09785-190">[x & y](../../../csharp/language-reference/operators/and-operator.md) – logical or bitwise AND.</span></span>  <span data-ttu-id="09785-191">通常允許將整數類型和 `enum` 類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="09785-191">Use with integer types and `enum` types is generally allowed.</span></span>  
  
## <a name="logical-xor-operator"></a><span data-ttu-id="09785-192">邏輯 XOR 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-192">Logical XOR Operator</span></span>  
 <span data-ttu-id="09785-193">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-193">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-194">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-194">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-195">[x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – 邏輯或位元 XOR。</span><span class="sxs-lookup"><span data-stu-id="09785-195">[x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – logical or bitwise XOR.</span></span>  <span data-ttu-id="09785-196">您通常可以將整數類型和 `enum` 類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="09785-196">You can generally use this with integer types and `enum` types.</span></span>  
  
## <a name="logical-or-operator"></a><span data-ttu-id="09785-197">邏輯 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-197">Logical OR Operator</span></span>  
 <span data-ttu-id="09785-198">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-198">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-199">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-199">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-200">[x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – 邏輯或位元 OR。</span><span class="sxs-lookup"><span data-stu-id="09785-200">[x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – logical or bitwise OR.</span></span>  <span data-ttu-id="09785-201">通常允許將整數類型和 `enum` 類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="09785-201">Use with integer types and `enum` types is generally allowed.</span></span>  
  
## <a name="conditional-and-operator"></a><span data-ttu-id="09785-202">條件 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-202">Conditional AND Operator</span></span>  
 <span data-ttu-id="09785-203">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-204">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-204">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-205">[x && y](../../../csharp/language-reference/operators/conditional-and-operator.md) – 邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="09785-205">[x && y](../../../csharp/language-reference/operators/conditional-and-operator.md) – logical AND.</span></span>  <span data-ttu-id="09785-206">如果第一個運算元為 false，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="09785-206">If the first operand is false, then C# does not evaluate the second operand.</span></span>  
  
## <a name="conditional-or-operator"></a><span data-ttu-id="09785-207">條件 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-207">Conditional OR Operator</span></span>  
 <span data-ttu-id="09785-208">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-208">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-209">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-209">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-210">[x &#124;&#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – 邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="09785-210">[x &#124;&#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – logical OR.</span></span>  <span data-ttu-id="09785-211">如果第一個運算元為 true，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="09785-211">If the first operand is true, then C# does not evaluate the second operand.</span></span>  
  
## <a name="null-coalescing-operator"></a><span data-ttu-id="09785-212">Null 聯合運算子</span><span class="sxs-lookup"><span data-stu-id="09785-212">Null-coalescing Operator</span></span>  
 <span data-ttu-id="09785-213">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-213">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-214">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-214">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-215">[x ?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="09785-215">[x ?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>  
  
## <a name="conditional-operator"></a><span data-ttu-id="09785-216">條件運算子</span><span class="sxs-lookup"><span data-stu-id="09785-216">Conditional Operator</span></span>  
 <span data-ttu-id="09785-217">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-217">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-218">請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-218">NOTE, you can click on the operator to go the details page with examples.</span></span>  
  
 <span data-ttu-id="09785-219">[t ? x : y](../../../csharp/language-reference/operators/conditional-operator.md) – 如果測試 `t` 為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="09785-219">[t ? x : y](../../../csharp/language-reference/operators/conditional-operator.md) – if test `t` is true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>  
  
## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="09785-220">指派和 Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="09785-220">Assignment and Lambda Operators</span></span>  
 <span data-ttu-id="09785-221">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="09785-221">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>  <span data-ttu-id="09785-222">請注意，您可以按一下運算子以移至內附範例的詳細頁面。</span><span class="sxs-lookup"><span data-stu-id="09785-222">NOTE, you can click on the operators to go the detailed pages with examples.</span></span>  
  
 <span data-ttu-id="09785-223">[x = y](../../../csharp/language-reference/operators/assignment-operator.md) – 指派。</span><span class="sxs-lookup"><span data-stu-id="09785-223">[x = y](../../../csharp/language-reference/operators/assignment-operator.md) – assignment.</span></span>  
  
 <span data-ttu-id="09785-224">[x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – 遞增。</span><span class="sxs-lookup"><span data-stu-id="09785-224">[x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – increment.</span></span>  <span data-ttu-id="09785-225">將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-225">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>  <span data-ttu-id="09785-226">如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以新增。</span><span class="sxs-lookup"><span data-stu-id="09785-226">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>  
  
 <span data-ttu-id="09785-227">[x -= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – 遞減。</span><span class="sxs-lookup"><span data-stu-id="09785-227">[x -= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – decrement.</span></span>  <span data-ttu-id="09785-228">將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-228">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span>  <span data-ttu-id="09785-229">如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以移除。</span><span class="sxs-lookup"><span data-stu-id="09785-229">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>  
  
 <span data-ttu-id="09785-230">[x \*= y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – 乘法指派。</span><span class="sxs-lookup"><span data-stu-id="09785-230">[x \*= y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – multiplication assignment.</span></span>  <span data-ttu-id="09785-231">將 `y` 的值乘以 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-231">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-232">[x /= y](../../../csharp/language-reference/operators/division-assignment-operator.md) – 除法指派。</span><span class="sxs-lookup"><span data-stu-id="09785-232">[x /= y](../../../csharp/language-reference/operators/division-assignment-operator.md) – division assignment.</span></span>  <span data-ttu-id="09785-233">將 `x` 的值除以 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-233">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-234">[x %= y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – 模數指派。</span><span class="sxs-lookup"><span data-stu-id="09785-234">[x %= y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – modulus assignment.</span></span>  <span data-ttu-id="09785-235">將 `x` 的值除以 `y` 的值，將餘數儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-235">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-236">[x &= y](../../../csharp/language-reference/operators/and-assignment-operator.md) – AND 指派。</span><span class="sxs-lookup"><span data-stu-id="09785-236">[x &= y](../../../csharp/language-reference/operators/and-assignment-operator.md) – AND assignment.</span></span>  <span data-ttu-id="09785-237">將 `y` 的值和 `x` 的值進行 AND 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-237">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-238">[x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – OR 指派。</span><span class="sxs-lookup"><span data-stu-id="09785-238">[x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – OR assignment.</span></span>  <span data-ttu-id="09785-239">將 `y` 的值和 `x` 的值進行 OR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-239">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-240">[x ^= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR 指派。</span><span class="sxs-lookup"><span data-stu-id="09785-240">[x ^= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR assignment.</span></span>  <span data-ttu-id="09785-241">將 `y` 的值和 `x` 的值進行 XOR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-241">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-242">[x <<= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – 左移指派。</span><span class="sxs-lookup"><span data-stu-id="09785-242">[x <<= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – left-shift assignment.</span></span>  <span data-ttu-id="09785-243">將 `x` 的值向左移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-243">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-244">[x >>= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – 右移指派。</span><span class="sxs-lookup"><span data-stu-id="09785-244">[x >>= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – right-shift assignment.</span></span>  <span data-ttu-id="09785-245">將 `x` 的值向右移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="09785-245">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>  
  
 <span data-ttu-id="09785-246">[=>](../../../csharp/language-reference/operators/lambda-operator.md) – lambda 宣告。</span><span class="sxs-lookup"><span data-stu-id="09785-246">[=>](../../../csharp/language-reference/operators/lambda-operator.md) – lambda declaration.</span></span>  
  
## <a name="arithmetic-overflow"></a><span data-ttu-id="09785-247">算術溢位</span><span class="sxs-lookup"><span data-stu-id="09785-247">Arithmetic Overflow</span></span>  
 <span data-ttu-id="09785-248">算術運算子 ([+](../../../csharp/language-reference/operators/addition-operator.md)、[-](../../../csharp/language-reference/operators/subtraction-operator.md)、[\*](../../../csharp/language-reference/operators/multiplication-operator.md)、[/](../../../csharp/language-reference/operators/division-operator.md)) 可產生數值型別所涉及之可能值範圍以外的結果。</span><span class="sxs-lookup"><span data-stu-id="09785-248">The arithmetic operators ([+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md)) can produce results that are outside the range of possible values for the numeric type involved.</span></span> <span data-ttu-id="09785-249">您應該參考特定運算子一節以取得詳細資料，但一般而言：</span><span class="sxs-lookup"><span data-stu-id="09785-249">You should refer to the section on a particular operator for details, but in general:</span></span>  
  
- <span data-ttu-id="09785-250">整數算術溢位可能會擲回 <xref:System.OverflowException> 或捨棄結果的最高有效位元。</span><span class="sxs-lookup"><span data-stu-id="09785-250">Integer arithmetic overflow either throws an <xref:System.OverflowException> or discards the most significant bits of the result.</span></span> <span data-ttu-id="09785-251">整數除以零一定會擲回 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="09785-251">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>  

   <span data-ttu-id="09785-252">發生整數溢位時，會發生的事取決於執行內容，可以是 [checked 或 unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="09785-252">When integer overflow occurs, what happens depends on the execution context, which can be [checked or unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="09785-253">在 checked 內容中，會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="09785-253">In a checked context, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="09785-254">在 unchecked 內容中，會捨棄結果的最高有效位元並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="09785-254">In an unchecked context, the most significant bits of the result are discarded and execution continues.</span></span> <span data-ttu-id="09785-255">因此，C# 可讓您選擇處理或忽略溢位。</span><span class="sxs-lookup"><span data-stu-id="09785-255">Thus, C# gives you the choice of handling or ignoring overflow.</span></span> <span data-ttu-id="09785-256">根據預設，*unchecked* 內容中會發生算術運算。</span><span class="sxs-lookup"><span data-stu-id="09785-256">By default, arithmetic operations occur in an *unchecked* context.</span></span> 

   <span data-ttu-id="09785-257">除了算術運算之外，整數類資料型別至整數類資料型別的轉換可能會造成溢位 (例如，當您將 [long](../../../csharp/language-reference/keywords/long.md) 轉換為 [int](../../../csharp/language-reference/keywords/int.md) 時)，且有可能受 checked 或 unchecked 執行的限制。</span><span class="sxs-lookup"><span data-stu-id="09785-257">In addition to the arithmetic operations, integral-type to integral-type casts can cause overflow (such as when you cast a [long](../../../csharp/language-reference/keywords/long.md) to an [int](../../../csharp/language-reference/keywords/int.md)), and are subject to checked or unchecked execution.</span></span> <span data-ttu-id="09785-258">不過，位元運算子和移位運算子永遠不會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="09785-258">However, bitwise operators and shift operators never cause overflow.</span></span>  
   
-   <span data-ttu-id="09785-259">浮點算術溢位或除以零永遠不會擲回例外狀況，因為浮點類型以 IEEE 754 為基礎，所以具有代表無限與 NaN (而非數字) 的佈建。</span><span class="sxs-lookup"><span data-stu-id="09785-259">Floating-point arithmetic overflow or division by zero never throws an exception, because floating-point types are based on IEEE 754 and so have provisions for representing infinity and NaN (Not a Number).</span></span>  
  
-   <span data-ttu-id="09785-260">[十進位](../../../csharp/language-reference/keywords/decimal.md)算術溢位一律會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="09785-260">[Decimal](../../../csharp/language-reference/keywords/decimal.md) arithmetic overflow always throws an <xref:System.OverflowException>.</span></span> <span data-ttu-id="09785-261">十進位除以零一定會擲回 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="09785-261">Decimal division by zero always throws a <xref:System.DivideByZeroException>.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="09785-262">請參閱</span><span class="sxs-lookup"><span data-stu-id="09785-262">See Also</span></span>  
 [<span data-ttu-id="09785-263">C# 參考</span><span class="sxs-lookup"><span data-stu-id="09785-263">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="09785-264">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="09785-264">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 <span data-ttu-id="09785-265">[C#](../../../csharp/index.md) [多載運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)</span><span class="sxs-lookup"><span data-stu-id="09785-265">[C#](../../../csharp/index.md) [Overloadable Operators](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)</span></span>  
 [<span data-ttu-id="09785-266">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="09785-266">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
