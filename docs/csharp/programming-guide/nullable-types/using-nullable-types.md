---
title: 使用可為 Null 的類型 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2fe0f34c45d3de0516a71ca5ed4dc807df4bf93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="a1f8d-102">使用可為 Null 的類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a1f8d-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="a1f8d-103">可為 Null 的型別能代表基礎類型的所有值，以及額外的 [null](../../../csharp/language-reference/keywords/null.md) 值。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="a1f8d-104">可為 Null 的型別會以下列兩種方法之一宣告︰</span><span class="sxs-lookup"><span data-stu-id="a1f8d-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="a1f8d-105">-或-</span><span class="sxs-lookup"><span data-stu-id="a1f8d-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="a1f8d-106">`T` 是可為 Null 類型的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="a1f8d-107">`T` 可以是包括 `struct` 在內的任何實值型別，不能是參考型別。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="a1f8d-108">如需可能使用可為 Null 類型的範例，請考慮一般的布林值變數如何能有兩個值︰true 和 false。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="a1f8d-109">沒有任何表示「未定義」的值。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="a1f8d-110">在許多程式設計應用程式最值得注意的資料庫互動中，變數會出現在未定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="a1f8d-111">例如，資料庫的欄位可能包含值 true 或 false，但也可能完全不包含任何值。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="a1f8d-112">同樣地，參考型別可以設為 `null` 以表示其尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="a1f8d-113">此差異會造成額外的程式設計工作、使用額外的變數儲存狀態資訊、使用特殊值等等。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="a1f8d-114">可為 Null 的型別修飾詞可讓 C# 建立實值型別變數，指出未定義的值。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="a1f8d-115">可為 Null 類型的範例</span><span class="sxs-lookup"><span data-stu-id="a1f8d-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="a1f8d-116">任何實值型別皆可用為可為 Null 類型的基礎。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="a1f8d-117">例如: </span><span class="sxs-lookup"><span data-stu-id="a1f8d-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="a1f8d-118">可為 Null 類型的成員</span><span class="sxs-lookup"><span data-stu-id="a1f8d-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="a1f8d-119">每個可為 Null 類型的執行個體皆有兩個公用唯讀屬性：</span><span class="sxs-lookup"><span data-stu-id="a1f8d-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="a1f8d-120">`HasValue` 是 `bool` 類型。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="a1f8d-121">當變數包含非 Null 值時，它會設成 `true`。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="a1f8d-122">`Value` 是與基礎類型相同的類型。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="a1f8d-123">如果 `HasValue` 為 `true`，則 `Value` 包含有意義的值。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="a1f8d-124">如果 `HasValue` 為 `false`，存取 `Value` 將會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="a1f8d-125">本例使用 `HasValue` 成員先測試變數是否包含值，再嘗試顯示它。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="a1f8d-126">您也可以如下列範例所示測試值︰</span><span class="sxs-lookup"><span data-stu-id="a1f8d-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="a1f8d-127">明確轉換</span><span class="sxs-lookup"><span data-stu-id="a1f8d-127">Explicit Conversions</span></span>  
 <span data-ttu-id="a1f8d-128">可為 Null 的型別可以明確轉換，或使用 `Value` 屬性轉換成一般類型。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="a1f8d-129">例如: </span><span class="sxs-lookup"><span data-stu-id="a1f8d-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="a1f8d-130">如果在兩種資料類別之間定義使用者定義轉換，則這些資料類型的可為 Null 版本也可使用相同的轉換。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="a1f8d-131">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="a1f8d-131">Implicit Conversions</span></span>  
 <span data-ttu-id="a1f8d-132">可為 Null 類型的變數可以 `null` 關鍵字設定為 Null，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="a1f8d-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="a1f8d-133">一般類型是隱含轉換成可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="a1f8d-134">運算子</span><span class="sxs-lookup"><span data-stu-id="a1f8d-134">Operators</span></span>  
 <span data-ttu-id="a1f8d-135">預先定義的一元和二元運算子，以及針對實值型別而存在的任何使用者定義的運算子，也能為可為 Null 的型別所用。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="a1f8d-136">如果運算元是 Null，則這些運算子會產生 Null 值；否則，運算子會使用所包含的值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="a1f8d-137">例如: </span><span class="sxs-lookup"><span data-stu-id="a1f8d-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="a1f8d-138">當您使用可為 Null 的型別執行比較時，如果其中一個可為 Null 類型的值為 Null 而另一個不是時，除 `!=` (不等於) 之外，所有的比較都會評估為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="a1f8d-139">請絕對不要因為特定的比較傳回 `false`，所以就假設相反的情況會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="a1f8d-140">在下列範例中，10 不大於、小於、也不等於 Null。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="a1f8d-141">只有 `num1 != num2` 評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="a1f8d-142">兩個都是 Null 的可為 Null 類型的相等比較評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="a1f8d-143">??</span><span class="sxs-lookup"><span data-stu-id="a1f8d-143">The ??</span></span> <span data-ttu-id="a1f8d-144">運算子</span><span class="sxs-lookup"><span data-stu-id="a1f8d-144">Operator</span></span>  
 <span data-ttu-id="a1f8d-145">`??` 運算子定義的預設值，會在可為 Null 的型別指派給不可為 Null 的型別時傳回。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="a1f8d-146">這個運算子也可以搭配多個可為 Null 的型別使用。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="a1f8d-147">例如: </span><span class="sxs-lookup"><span data-stu-id="a1f8d-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="a1f8d-148">bool? 類型</span><span class="sxs-lookup"><span data-stu-id="a1f8d-148">The bool? type</span></span>  
 <span data-ttu-id="a1f8d-149">`bool?` 可為 Null 的型別可以包含三個不同的值︰[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 和 [null](../../../csharp/language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="a1f8d-150">如需如何從 bool? 轉換成 bool 的資訊，請參閱[如何：從 bool? 安全轉型到 bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="a1f8d-151">可為 Null 的布林值就像 SQL 中使用的布林值變數類型。</span><span class="sxs-lookup"><span data-stu-id="a1f8d-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="a1f8d-152">為確定 `&` 和 `|` 運算子所產生的結果與 SQL 的三個布林值類型一致，會提供下列預先定義的運算子︰</span><span class="sxs-lookup"><span data-stu-id="a1f8d-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="a1f8d-153">下表列出這些運算子的結果：</span><span class="sxs-lookup"><span data-stu-id="a1f8d-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="a1f8d-154">X</span><span class="sxs-lookup"><span data-stu-id="a1f8d-154">X</span></span>|<span data-ttu-id="a1f8d-155">y</span><span class="sxs-lookup"><span data-stu-id="a1f8d-155">y</span></span>|<span data-ttu-id="a1f8d-156">x&y</span><span class="sxs-lookup"><span data-stu-id="a1f8d-156">x&y</span></span>|<span data-ttu-id="a1f8d-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="a1f8d-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="a1f8d-158">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-158">true</span></span>|<span data-ttu-id="a1f8d-159">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-159">true</span></span>|<span data-ttu-id="a1f8d-160">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-160">true</span></span>|<span data-ttu-id="a1f8d-161">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-161">true</span></span>|  
|<span data-ttu-id="a1f8d-162">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-162">true</span></span>|<span data-ttu-id="a1f8d-163">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-163">false</span></span>|<span data-ttu-id="a1f8d-164">false</span><span class="sxs-lookup"><span data-stu-id="a1f8d-164">false</span></span>|<span data-ttu-id="a1f8d-165">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-165">true</span></span>|  
|<span data-ttu-id="a1f8d-166">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-166">true</span></span>|<span data-ttu-id="a1f8d-167">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-167">null</span></span>|<span data-ttu-id="a1f8d-168">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-168">null</span></span>|<span data-ttu-id="a1f8d-169">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-169">true</span></span>|  
|<span data-ttu-id="a1f8d-170">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-170">false</span></span>|<span data-ttu-id="a1f8d-171">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-171">true</span></span>|<span data-ttu-id="a1f8d-172">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-172">false</span></span>|<span data-ttu-id="a1f8d-173">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-173">true</span></span>|  
|<span data-ttu-id="a1f8d-174">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-174">false</span></span>|<span data-ttu-id="a1f8d-175">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-175">false</span></span>|<span data-ttu-id="a1f8d-176">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-176">false</span></span>|<span data-ttu-id="a1f8d-177">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-177">false</span></span>|  
|<span data-ttu-id="a1f8d-178">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-178">false</span></span>|<span data-ttu-id="a1f8d-179">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-179">null</span></span>|<span data-ttu-id="a1f8d-180">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-180">false</span></span>|<span data-ttu-id="a1f8d-181">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-181">null</span></span>|  
|<span data-ttu-id="a1f8d-182">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-182">null</span></span>|<span data-ttu-id="a1f8d-183">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-183">true</span></span>|<span data-ttu-id="a1f8d-184">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-184">null</span></span>|<span data-ttu-id="a1f8d-185">true</span><span class="sxs-lookup"><span data-stu-id="a1f8d-185">true</span></span>|  
|<span data-ttu-id="a1f8d-186">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-186">null</span></span>|<span data-ttu-id="a1f8d-187">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-187">false</span></span>|<span data-ttu-id="a1f8d-188">False</span><span class="sxs-lookup"><span data-stu-id="a1f8d-188">false</span></span>|<span data-ttu-id="a1f8d-189">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-189">null</span></span>|  
|<span data-ttu-id="a1f8d-190">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-190">null</span></span>|<span data-ttu-id="a1f8d-191">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-191">null</span></span>|<span data-ttu-id="a1f8d-192">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-192">null</span></span>|<span data-ttu-id="a1f8d-193">null</span><span class="sxs-lookup"><span data-stu-id="a1f8d-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1f8d-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1f8d-194">See Also</span></span>  
 [<span data-ttu-id="a1f8d-195">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a1f8d-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a1f8d-196">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="a1f8d-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="a1f8d-197">對可為 Null 的型別進行 boxing</span><span class="sxs-lookup"><span data-stu-id="a1f8d-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="a1f8d-198">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="a1f8d-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
