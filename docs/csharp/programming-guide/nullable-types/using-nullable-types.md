---
title: "使用可為 Null 的類型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0721d9f60abc4e158135d6b050953b3e63ab8cb5
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="11f61-102">使用可為 Null 的類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="11f61-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="11f61-103">可為 Null 的型別能代表基礎類型的所有值，以及額外的 [null](../../../csharp/language-reference/keywords/null.md) 值。</span><span class="sxs-lookup"><span data-stu-id="11f61-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="11f61-104">可為 Null 的型別會以下列兩種方法之一宣告︰</span><span class="sxs-lookup"><span data-stu-id="11f61-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="11f61-105">-或-</span><span class="sxs-lookup"><span data-stu-id="11f61-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="11f61-106">`T` 是可為 Null 類型的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="11f61-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="11f61-107">`T` 可以是包括 `struct` 在內的任何實值型別，不能是參考型別。</span><span class="sxs-lookup"><span data-stu-id="11f61-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="11f61-108">如需可能使用可為 Null 類型的範例，請考慮一般的布林值變數如何能有兩個值︰true 和 false。</span><span class="sxs-lookup"><span data-stu-id="11f61-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="11f61-109">沒有任何表示「未定義」的值。</span><span class="sxs-lookup"><span data-stu-id="11f61-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="11f61-110">在許多程式設計應用程式最值得注意的資料庫互動中，變數會出現在未定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="11f61-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="11f61-111">例如，資料庫的欄位可能包含值 true 或 false，但也可能完全不包含任何值。</span><span class="sxs-lookup"><span data-stu-id="11f61-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="11f61-112">同樣地，參考型別可以設為 `null` 以表示其尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="11f61-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="11f61-113">此差異會造成額外的程式設計工作、使用額外的變數儲存狀態資訊、使用特殊值等等。</span><span class="sxs-lookup"><span data-stu-id="11f61-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="11f61-114">可為 Null 的型別修飾詞可讓 C# 建立實值型別變數，指出未定義的值。</span><span class="sxs-lookup"><span data-stu-id="11f61-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="11f61-115">可為 Null 類型的範例</span><span class="sxs-lookup"><span data-stu-id="11f61-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="11f61-116">任何實值型別皆可用為可為 Null 類型的基礎。</span><span class="sxs-lookup"><span data-stu-id="11f61-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="11f61-117">例如：</span><span class="sxs-lookup"><span data-stu-id="11f61-117">For example:</span></span>  
  
 <span data-ttu-id="11f61-118">[!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-118">[!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]</span></span>  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="11f61-119">可為 Null 類型的成員</span><span class="sxs-lookup"><span data-stu-id="11f61-119">The Members of Nullable Types</span></span>  
 <span data-ttu-id="11f61-120">每個可為 Null 類型的執行個體皆有兩個公用唯讀屬性：</span><span class="sxs-lookup"><span data-stu-id="11f61-120">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="11f61-121">`HasValue` 是 `bool` 類型。</span><span class="sxs-lookup"><span data-stu-id="11f61-121">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="11f61-122">當變數包含非 Null 值時，它會設成 `true`。</span><span class="sxs-lookup"><span data-stu-id="11f61-122">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="11f61-123">`Value` 是與基礎類型相同的類型。</span><span class="sxs-lookup"><span data-stu-id="11f61-123">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="11f61-124">如果 `HasValue` 為 `true`，則 `Value` 包含有意義的值。</span><span class="sxs-lookup"><span data-stu-id="11f61-124">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="11f61-125">如果 `HasValue` 為 `false`，存取 `Value` 將會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="11f61-125">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="11f61-126">本例使用 `HasValue` 成員先測試變數是否包含值，再嘗試顯示它。</span><span class="sxs-lookup"><span data-stu-id="11f61-126">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 <span data-ttu-id="11f61-127">[!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-127">[!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]</span></span>  
  
 <span data-ttu-id="11f61-128">您也可以如下列範例所示測試值︰</span><span class="sxs-lookup"><span data-stu-id="11f61-128">Testing for a value can also be done as in the following example:</span></span>  
  
 <span data-ttu-id="11f61-129">[!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-129">[!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]</span></span>  
  
## <a name="explicit-conversions"></a><span data-ttu-id="11f61-130">明確轉換</span><span class="sxs-lookup"><span data-stu-id="11f61-130">Explicit Conversions</span></span>  
 <span data-ttu-id="11f61-131">可為 Null 的型別可以明確轉換，或使用 `Value` 屬性轉換成一般類型。</span><span class="sxs-lookup"><span data-stu-id="11f61-131">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="11f61-132">例如：</span><span class="sxs-lookup"><span data-stu-id="11f61-132">For example:</span></span>  
  
 <span data-ttu-id="11f61-133">[!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-133">[!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]</span></span>  
  
 <span data-ttu-id="11f61-134">如果在兩種資料類別之間定義使用者定義轉換，則這些資料類型的可為 Null 版本也可使用相同的轉換。</span><span class="sxs-lookup"><span data-stu-id="11f61-134">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="11f61-135">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="11f61-135">Implicit Conversions</span></span>  
 <span data-ttu-id="11f61-136">可為 Null 類型的變數可以 `null` 關鍵字設定為 Null，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="11f61-136">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 <span data-ttu-id="11f61-137">[!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-137">[!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]</span></span>  
  
 <span data-ttu-id="11f61-138">一般類型是隱含轉換成可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="11f61-138">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 <span data-ttu-id="11f61-139">[!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-139">[!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]</span></span>  
  
## <a name="operators"></a><span data-ttu-id="11f61-140">運算子</span><span class="sxs-lookup"><span data-stu-id="11f61-140">Operators</span></span>  
 <span data-ttu-id="11f61-141">預先定義的一元和二元運算子，以及針對實值型別而存在的任何使用者定義的運算子，也能為可為 Null 的型別所用。</span><span class="sxs-lookup"><span data-stu-id="11f61-141">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="11f61-142">如果運算元是 Null，則這些運算子會產生 Null 值；否則，運算子會使用所包含的值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="11f61-142">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="11f61-143">例如：</span><span class="sxs-lookup"><span data-stu-id="11f61-143">For example:</span></span>  
  
 <span data-ttu-id="11f61-144">[!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-144">[!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]</span></span>  
  
 <span data-ttu-id="11f61-145">當您使用可為 Null 的型別執行比較時，如果其中一個可為 Null 類型的值為 Null 而另一個不是時，除 `!=` (不等於) 之外，所有的比較都會評估為 `false`。</span><span class="sxs-lookup"><span data-stu-id="11f61-145">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="11f61-146">請絕對不要因為特定的比較傳回 `false`，所以就假設相反的情況會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="11f61-146">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="11f61-147">在下列範例中，10 不大於、小於、也不等於 Null。</span><span class="sxs-lookup"><span data-stu-id="11f61-147">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="11f61-148">只有 `num1 != num2` 評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="11f61-148">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 <span data-ttu-id="11f61-149">[!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-149">[!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]</span></span>  
  
 <span data-ttu-id="11f61-150">兩個都是 Null 的可為 Null 類型的相等比較評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="11f61-150">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="11f61-151">??</span><span class="sxs-lookup"><span data-stu-id="11f61-151">The ??</span></span> <span data-ttu-id="11f61-152">運算子</span><span class="sxs-lookup"><span data-stu-id="11f61-152">Operator</span></span>  
 <span data-ttu-id="11f61-153">`??` 運算子定義的預設值，會在可為 Null 的型別指派給不可為 Null 的型別時傳回。</span><span class="sxs-lookup"><span data-stu-id="11f61-153">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 <span data-ttu-id="11f61-154">[!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-154">[!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]</span></span>  
  
 <span data-ttu-id="11f61-155">這個運算子也可以搭配多個可為 Null 的型別使用。</span><span class="sxs-lookup"><span data-stu-id="11f61-155">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="11f61-156">例如：</span><span class="sxs-lookup"><span data-stu-id="11f61-156">For example:</span></span>  
  
 <span data-ttu-id="11f61-157">[!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="11f61-157">[!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]</span></span>  
  
## <a name="the-bool-type"></a><span data-ttu-id="11f61-158">bool? 類型</span><span class="sxs-lookup"><span data-stu-id="11f61-158">The bool? type</span></span>  
 <span data-ttu-id="11f61-159">`bool?` 可為 Null 的型別可以包含三個不同的值︰[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 和 [null](../../../csharp/language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="11f61-159">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="11f61-160">如需如何從 bool? 轉換成 bool 的資訊，請參閱[如何：從 bool? 安全轉型到 bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)。</span><span class="sxs-lookup"><span data-stu-id="11f61-160">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="11f61-161">可為 Null 的布林值就像 SQL 中使用的布林值變數類型。</span><span class="sxs-lookup"><span data-stu-id="11f61-161">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="11f61-162">為確定 `&` 和 `|` 運算子所產生的結果與 SQL 的三個布林值類型一致，會提供下列預先定義的運算子︰</span><span class="sxs-lookup"><span data-stu-id="11f61-162">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="11f61-163">下表列出這些運算子的結果：</span><span class="sxs-lookup"><span data-stu-id="11f61-163">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="11f61-164">X</span><span class="sxs-lookup"><span data-stu-id="11f61-164">X</span></span>|<span data-ttu-id="11f61-165">y</span><span class="sxs-lookup"><span data-stu-id="11f61-165">y</span></span>|<span data-ttu-id="11f61-166">x&y</span><span class="sxs-lookup"><span data-stu-id="11f61-166">x&y</span></span>|<span data-ttu-id="11f61-167">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="11f61-167">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="11f61-168">true</span><span class="sxs-lookup"><span data-stu-id="11f61-168">true</span></span>|<span data-ttu-id="11f61-169">true</span><span class="sxs-lookup"><span data-stu-id="11f61-169">true</span></span>|<span data-ttu-id="11f61-170">true</span><span class="sxs-lookup"><span data-stu-id="11f61-170">true</span></span>|<span data-ttu-id="11f61-171">true</span><span class="sxs-lookup"><span data-stu-id="11f61-171">true</span></span>|  
|<span data-ttu-id="11f61-172">true</span><span class="sxs-lookup"><span data-stu-id="11f61-172">true</span></span>|<span data-ttu-id="11f61-173">false</span><span class="sxs-lookup"><span data-stu-id="11f61-173">false</span></span>|<span data-ttu-id="11f61-174">false</span><span class="sxs-lookup"><span data-stu-id="11f61-174">false</span></span>|<span data-ttu-id="11f61-175">true</span><span class="sxs-lookup"><span data-stu-id="11f61-175">true</span></span>|  
|<span data-ttu-id="11f61-176">true</span><span class="sxs-lookup"><span data-stu-id="11f61-176">true</span></span>|<span data-ttu-id="11f61-177">null</span><span class="sxs-lookup"><span data-stu-id="11f61-177">null</span></span>|<span data-ttu-id="11f61-178">null</span><span class="sxs-lookup"><span data-stu-id="11f61-178">null</span></span>|<span data-ttu-id="11f61-179">true</span><span class="sxs-lookup"><span data-stu-id="11f61-179">true</span></span>|  
|<span data-ttu-id="11f61-180">false</span><span class="sxs-lookup"><span data-stu-id="11f61-180">false</span></span>|<span data-ttu-id="11f61-181">true</span><span class="sxs-lookup"><span data-stu-id="11f61-181">true</span></span>|<span data-ttu-id="11f61-182">false</span><span class="sxs-lookup"><span data-stu-id="11f61-182">false</span></span>|<span data-ttu-id="11f61-183">true</span><span class="sxs-lookup"><span data-stu-id="11f61-183">true</span></span>|  
|<span data-ttu-id="11f61-184">false</span><span class="sxs-lookup"><span data-stu-id="11f61-184">false</span></span>|<span data-ttu-id="11f61-185">false</span><span class="sxs-lookup"><span data-stu-id="11f61-185">false</span></span>|<span data-ttu-id="11f61-186">false</span><span class="sxs-lookup"><span data-stu-id="11f61-186">false</span></span>|<span data-ttu-id="11f61-187">false</span><span class="sxs-lookup"><span data-stu-id="11f61-187">false</span></span>|  
|<span data-ttu-id="11f61-188">false</span><span class="sxs-lookup"><span data-stu-id="11f61-188">false</span></span>|<span data-ttu-id="11f61-189">null</span><span class="sxs-lookup"><span data-stu-id="11f61-189">null</span></span>|<span data-ttu-id="11f61-190">false</span><span class="sxs-lookup"><span data-stu-id="11f61-190">false</span></span>|<span data-ttu-id="11f61-191">null</span><span class="sxs-lookup"><span data-stu-id="11f61-191">null</span></span>|  
|<span data-ttu-id="11f61-192">null</span><span class="sxs-lookup"><span data-stu-id="11f61-192">null</span></span>|<span data-ttu-id="11f61-193">true</span><span class="sxs-lookup"><span data-stu-id="11f61-193">true</span></span>|<span data-ttu-id="11f61-194">null</span><span class="sxs-lookup"><span data-stu-id="11f61-194">null</span></span>|<span data-ttu-id="11f61-195">true</span><span class="sxs-lookup"><span data-stu-id="11f61-195">true</span></span>|  
|<span data-ttu-id="11f61-196">null</span><span class="sxs-lookup"><span data-stu-id="11f61-196">null</span></span>|<span data-ttu-id="11f61-197">false</span><span class="sxs-lookup"><span data-stu-id="11f61-197">false</span></span>|<span data-ttu-id="11f61-198">false</span><span class="sxs-lookup"><span data-stu-id="11f61-198">false</span></span>|<span data-ttu-id="11f61-199">null</span><span class="sxs-lookup"><span data-stu-id="11f61-199">null</span></span>|  
|<span data-ttu-id="11f61-200">null</span><span class="sxs-lookup"><span data-stu-id="11f61-200">null</span></span>|<span data-ttu-id="11f61-201">null</span><span class="sxs-lookup"><span data-stu-id="11f61-201">null</span></span>|<span data-ttu-id="11f61-202">null</span><span class="sxs-lookup"><span data-stu-id="11f61-202">null</span></span>|<span data-ttu-id="11f61-203">null</span><span class="sxs-lookup"><span data-stu-id="11f61-203">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11f61-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11f61-204">See Also</span></span>  
 <span data-ttu-id="11f61-205">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="11f61-205">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="11f61-206">[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="11f61-206">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 <span data-ttu-id="11f61-207">[對可為 Null 的型別進行 boxing](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md) </span><span class="sxs-lookup"><span data-stu-id="11f61-207">[Boxing Nullable Types](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md) </span></span>  
 [<span data-ttu-id="11f61-208">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="11f61-208">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

