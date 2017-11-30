---
title: "模式比對 (F#)"
description: "了解如何使用模式在 F # 中比較具有邏輯結構的資料、 將資料分解成構成部分，或從資料擷取資訊。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a><span data-ttu-id="ab473-104">模式比對</span><span class="sxs-lookup"><span data-stu-id="ab473-104">Pattern Matching</span></span>

<span data-ttu-id="ab473-105">模式是轉換輸入的資料的規則。</span><span class="sxs-lookup"><span data-stu-id="ab473-105">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="ab473-106">它們會使用 F # 語言來比較邏輯的結構或結構的資料、 將資料分解成構成部分，或從各種資料擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="ab473-106">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>


## <a name="remarks"></a><span data-ttu-id="ab473-107">備註</span><span class="sxs-lookup"><span data-stu-id="ab473-107">Remarks</span></span>
<span data-ttu-id="ab473-108">模式中使用許多語言建構，例如`match`運算式。</span><span class="sxs-lookup"><span data-stu-id="ab473-108">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="ab473-109">您正在處理中的函式的引數時，它們會使用`let`繫結和 lambda 運算式和相關聯的例外狀況處理常式中`try...with`運算式。</span><span class="sxs-lookup"><span data-stu-id="ab473-109">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="ab473-110">如需詳細資訊，請參閱[比對運算式](match-expressions.md)， [let 繫結](functions/let-bindings.md)， [Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)，和[例外狀況： `try...with`運算式](exception-handling/the-try-with-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="ab473-110">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="ab473-111">例如，在`match`運算式*模式*是縱線符號後面。</span><span class="sxs-lookup"><span data-stu-id="ab473-111">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="ab473-112">每個模式會做為轉換以某種方式輸入的規則。</span><span class="sxs-lookup"><span data-stu-id="ab473-112">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="ab473-113">在`match`運算式中，每個模式會接著檢查以查看是否相容的模式與輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="ab473-113">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="ab473-114">如果找到相符項目，將執行結果運算式。</span><span class="sxs-lookup"><span data-stu-id="ab473-114">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="ab473-115">如果找不到相符項目，則會測試的下一個模式規則。</span><span class="sxs-lookup"><span data-stu-id="ab473-115">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="ab473-116">選擇性當*條件*組件中會說明[比對運算式](match-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ab473-116">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="ab473-117">支援的模式下表中顯示。</span><span class="sxs-lookup"><span data-stu-id="ab473-117">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="ab473-118">在執行階段，輸入會針對每個資料表中列出的順序的下列模式來測試和模式會遞迴地套用，從第一次到最後一個出現在您的程式碼中，從左到右的模式，便在每一行。</span><span class="sxs-lookup"><span data-stu-id="ab473-118">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="ab473-119">名稱</span><span class="sxs-lookup"><span data-stu-id="ab473-119">Name</span></span>|<span data-ttu-id="ab473-120">描述</span><span class="sxs-lookup"><span data-stu-id="ab473-120">Description</span></span>|<span data-ttu-id="ab473-121">範例</span><span class="sxs-lookup"><span data-stu-id="ab473-121">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="ab473-122">常數模式</span><span class="sxs-lookup"><span data-stu-id="ab473-122">Constant pattern</span></span>|<span data-ttu-id="ab473-123">任何數值、 字元或字串常值、 列舉常數或定義常值的識別項</span><span class="sxs-lookup"><span data-stu-id="ab473-123">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="ab473-124">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="ab473-124">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="ab473-125">識別項模式</span><span class="sxs-lookup"><span data-stu-id="ab473-125">Identifier pattern</span></span>|<span data-ttu-id="ab473-126">差別等位、 例外狀況標籤或現用模式大小寫的 case 值</span><span class="sxs-lookup"><span data-stu-id="ab473-126">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="ab473-127">變數模式</span><span class="sxs-lookup"><span data-stu-id="ab473-127">Variable pattern</span></span>|<span data-ttu-id="ab473-128">*identifier*</span><span class="sxs-lookup"><span data-stu-id="ab473-128">*identifier*</span></span>|`a`|
|<span data-ttu-id="ab473-129">`as`模式</span><span class="sxs-lookup"><span data-stu-id="ab473-129">`as` pattern</span></span>|<span data-ttu-id="ab473-130">*模式*為*識別碼*</span><span class="sxs-lookup"><span data-stu-id="ab473-130">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="ab473-131">或圖樣</span><span class="sxs-lookup"><span data-stu-id="ab473-131">OR pattern</span></span>|<span data-ttu-id="ab473-132">*pattern1* &#124;*pattern2*</span><span class="sxs-lookup"><span data-stu-id="ab473-132">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="ab473-133">和模式</span><span class="sxs-lookup"><span data-stu-id="ab473-133">AND pattern</span></span>|<span data-ttu-id="ab473-134">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="ab473-134">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="ab473-135">Cons 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-135">Cons pattern</span></span>|<span data-ttu-id="ab473-136">*識別項*::*清單識別碼*</span><span class="sxs-lookup"><span data-stu-id="ab473-136">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="ab473-137">清單模式</span><span class="sxs-lookup"><span data-stu-id="ab473-137">List pattern</span></span>|<span data-ttu-id="ab473-138">[ *pattern_1*;...;*pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="ab473-138">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="ab473-139">陣列模式</span><span class="sxs-lookup"><span data-stu-id="ab473-139">Array pattern</span></span>|<span data-ttu-id="ab473-140">[&#124;*pattern_1*;..;*pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="ab473-140">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="ab473-141">括號括住模式</span><span class="sxs-lookup"><span data-stu-id="ab473-141">Parenthesized pattern</span></span>|<span data-ttu-id="ab473-142">(*模式*)</span><span class="sxs-lookup"><span data-stu-id="ab473-142">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="ab473-143">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-143">Tuple pattern</span></span>|<span data-ttu-id="ab473-144">( *pattern_1*，...， *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="ab473-144">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="ab473-145">記錄模式</span><span class="sxs-lookup"><span data-stu-id="ab473-145">Record pattern</span></span>|<span data-ttu-id="ab473-146">{ *identifier1* = *pattern_1*;...;*identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="ab473-146">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="ab473-147">萬用字元模式</span><span class="sxs-lookup"><span data-stu-id="ab473-147">Wildcard pattern</span></span>|<span data-ttu-id="ab473-148">_</span><span class="sxs-lookup"><span data-stu-id="ab473-148">_</span></span>|`_`|
|<span data-ttu-id="ab473-149">搭配類型註釋的模式</span><span class="sxs-lookup"><span data-stu-id="ab473-149">Pattern together with type annotation</span></span>|<span data-ttu-id="ab473-150">*模式*:*類型*</span><span class="sxs-lookup"><span data-stu-id="ab473-150">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="ab473-151">類型測試模式</span><span class="sxs-lookup"><span data-stu-id="ab473-151">Type test pattern</span></span>|<span data-ttu-id="ab473-152">:?</span><span class="sxs-lookup"><span data-stu-id="ab473-152">:?</span></span> <span data-ttu-id="ab473-153">*型別*[做為*識別碼*]</span><span class="sxs-lookup"><span data-stu-id="ab473-153">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="ab473-154">Null 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-154">Null pattern</span></span>|<span data-ttu-id="ab473-155">null</span><span class="sxs-lookup"><span data-stu-id="ab473-155">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="ab473-156">常數的模式</span><span class="sxs-lookup"><span data-stu-id="ab473-156">Constant Patterns</span></span>
<span data-ttu-id="ab473-157">常數的模式是 （使用包含列舉型別名稱） 的數值、 字元和字串常值、 列舉常數。</span><span class="sxs-lookup"><span data-stu-id="ab473-157">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="ab473-158">A`match`只常數模式的運算式可以與其他語言中的 case 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab473-158">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="ab473-159">輸入比較的常值和模式會比對的值是否相等。</span><span class="sxs-lookup"><span data-stu-id="ab473-159">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="ab473-160">常值類型必須與輸入的類型相容。</span><span class="sxs-lookup"><span data-stu-id="ab473-160">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="ab473-161">下列範例會示範如何使用常值模式，並也會使用變數的模式和 OR 模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-161">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="ab473-162">常值模式的另一個範例是根據列舉常數的模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-162">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="ab473-163">當您使用的列舉常數，您必須指定列舉型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ab473-163">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="ab473-164">識別項模式</span><span class="sxs-lookup"><span data-stu-id="ab473-164">Identifier Patterns</span></span>
<span data-ttu-id="ab473-165">如果模式是字元字串構成有效的識別項，識別項的格式會決定如何比對模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-165">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="ab473-166">如果識別項長度超過單一字元，且開頭為大寫的字元，編譯器會嘗試比對識別項模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-166">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="ab473-167">此模式的識別項可能是標記為常值的屬性、 差別的聯集、 例外狀況的識別項或現用模式大小寫的值。</span><span class="sxs-lookup"><span data-stu-id="ab473-167">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="ab473-168">如果不找到任何相符的識別項，則比對失敗下, 一個模式規則，該變數的模式，會與輸入。</span><span class="sxs-lookup"><span data-stu-id="ab473-168">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="ab473-169">差別等位模式可以是簡單名稱的情況下，或它們可以有一個值或包含多個值的 tuple。</span><span class="sxs-lookup"><span data-stu-id="ab473-169">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="ab473-170">如果沒有值，您必須指定值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ab473-170">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="ab473-171">Tuple，您必須提供每個元素 tuple 的識別碼或識別項具有一個欄位名稱與 tuple 模式或多個名為聯集的欄位。</span><span class="sxs-lookup"><span data-stu-id="ab473-171">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="ab473-172">請參閱本節的範例中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="ab473-172">See the code examples in this section for examples.</span></span>

<span data-ttu-id="ab473-173">`option`類型是具有兩種情況下，差別的等位`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="ab473-173">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="ab473-174">其中一個案例中 (`Some`) 具有值，但其他 (`None`) 是只具名的情況。</span><span class="sxs-lookup"><span data-stu-id="ab473-174">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="ab473-175">因此，`Some`必須有相關聯的值的變數`Some`案例，但`None`必須單獨出現。</span><span class="sxs-lookup"><span data-stu-id="ab473-175">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="ab473-176">下列程式碼變數`var1`透過比對的值會指定`Some`案例。</span><span class="sxs-lookup"><span data-stu-id="ab473-176">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="ab473-177">在下列範例中，`PersonName`差別等位包含字串和字元，表示名稱的可能表單的混合。</span><span class="sxs-lookup"><span data-stu-id="ab473-177">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="ab473-178">差別等位的情況下會`FirstOnly`， `LastOnly`，和`FirstLast`。</span><span class="sxs-lookup"><span data-stu-id="ab473-178">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="ab473-179">差別聯集已命名欄位，您可以使用等號 （=） 來擷取具名欄位的值。</span><span class="sxs-lookup"><span data-stu-id="ab473-179">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="ab473-180">例如，請考慮具有宣告，如下所示的差別等位。</span><span class="sxs-lookup"><span data-stu-id="ab473-180">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="ab473-181">您可以使用模式比對運算式中的具名的欄位，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ab473-181">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="ab473-182">具名欄位的使用是選擇性的因此在前一個範例中，同時`Circle(r)`和`Circle(radius = r)`有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="ab473-182">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="ab473-183">當您指定多個欄位時，請使用分號 （;） 做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ab473-183">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="ab473-184">現用模式可讓您定義更複雜的自訂模式比對。</span><span class="sxs-lookup"><span data-stu-id="ab473-184">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="ab473-185">如需現用模式的詳細資訊，請參閱[現用模式](active-patterns.md)。</span><span class="sxs-lookup"><span data-stu-id="ab473-185">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="ab473-186">例外狀況處理常式的內容中的比對模式中所使用的情況下，識別項例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ab473-186">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="ab473-187">模式比對中例外狀況處理的相關資訊，請參閱[例外狀況：`try...with`運算式](exception-handling/the-try-with-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="ab473-187">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>


## <a name="variable-patterns"></a><span data-ttu-id="ab473-188">變數模式</span><span class="sxs-lookup"><span data-stu-id="ab473-188">Variable Patterns</span></span>
<span data-ttu-id="ab473-189">變數模式所比對變數的名稱，然後是可用於執行運算式右邊的值指派`->`符號。</span><span class="sxs-lookup"><span data-stu-id="ab473-189">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="ab473-190">單獨變數模式會比對任何輸入，但變數模式通常出現在其他的模式，因此啟用更複雜的結構，例如 tuple 和分解成變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="ab473-190">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="ab473-191">下列範例會示範內 tuple 模式的變數模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-191">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="ab473-192">as 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-192">as Pattern</span></span>
<span data-ttu-id="ab473-193">`as`模式為模式，具有`as`子句附加至它。</span><span class="sxs-lookup"><span data-stu-id="ab473-193">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="ab473-194">`as`子句相符的值繫結可用於執行運算式中的名稱`match`運算式，或在此模式中的使用位置的情況下`let`繫結，名稱會新增為本機領域的繫結。</span><span class="sxs-lookup"><span data-stu-id="ab473-194">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="ab473-195">下列範例會使用`as`模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-195">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="ab473-196">或圖樣</span><span class="sxs-lookup"><span data-stu-id="ab473-196">OR Pattern</span></span>
<span data-ttu-id="ab473-197">OR 模式時輸入的資料可以比對多個模式，而且您想要執行相同的程式碼，如此一來使用。</span><span class="sxs-lookup"><span data-stu-id="ab473-197">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="ab473-198">OR 模式的兩邊的類型必須相容。</span><span class="sxs-lookup"><span data-stu-id="ab473-198">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="ab473-199">下列範例會示範 OR 模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-199">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="ab473-200">和模式</span><span class="sxs-lookup"><span data-stu-id="ab473-200">AND Pattern</span></span>
<span data-ttu-id="ab473-201">AND 模式需要輸入符合兩個模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-201">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="ab473-202">AND 模式的兩邊的類型必須相容。</span><span class="sxs-lookup"><span data-stu-id="ab473-202">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="ab473-203">下列範例很相似`detectZeroTuple`示[Tuple 模式](https://msdn.microsoft.com/library/#tuple)> 一節稍後在本主題中，但這裡`var1`和`var2`取得方式是使用 AND 模式做為值。</span><span class="sxs-lookup"><span data-stu-id="ab473-203">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="ab473-204">Cons 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-204">Cons Pattern</span></span>
<span data-ttu-id="ab473-205">Cons 模式用來將清單分解成第一個項目， *head*，和包含其餘的項目，清單*結尾*。</span><span class="sxs-lookup"><span data-stu-id="ab473-205">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="ab473-206">清單模式</span><span class="sxs-lookup"><span data-stu-id="ab473-206">List Pattern</span></span>
<span data-ttu-id="ab473-207">清單模式可讓清單來分解成一些項目。</span><span class="sxs-lookup"><span data-stu-id="ab473-207">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="ab473-208">在清單模式可以比對僅特定數目的項目清單。</span><span class="sxs-lookup"><span data-stu-id="ab473-208">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="ab473-209">陣列模式</span><span class="sxs-lookup"><span data-stu-id="ab473-209">Array Pattern</span></span>
<span data-ttu-id="ab473-210">陣列模式類似於清單模式，而且可用來將分解的特定長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="ab473-210">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="ab473-211">括號括住模式</span><span class="sxs-lookup"><span data-stu-id="ab473-211">Parenthesized Pattern</span></span>
<span data-ttu-id="ab473-212">括號可以分組模式來達成所需的順序關聯性。</span><span class="sxs-lookup"><span data-stu-id="ab473-212">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="ab473-213">在下列範例中，括號用來控制 AND 模式和 cons 模式之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ab473-213">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="ab473-214">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-214">Tuple Pattern</span></span>
<span data-ttu-id="ab473-215">Tuple 模式比對中 tuple 形式的輸入，並可讓 tuple 來分解成其組成的項目使用模式比對 tuple 中的每個位置的變數。</span><span class="sxs-lookup"><span data-stu-id="ab473-215">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="ab473-216">下列範例示範的 tuple 模式，並也會使用常值的模式、 變數的模式和萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-216">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="ab473-217">記錄模式</span><span class="sxs-lookup"><span data-stu-id="ab473-217">Record Pattern</span></span>
<span data-ttu-id="ab473-218">記錄模式用來將分解記錄擷取欄位的值。</span><span class="sxs-lookup"><span data-stu-id="ab473-218">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="ab473-219">模式沒有參考所有欄位的記錄。只要任何省略的欄位不會參與比對，並不會擷取。</span><span class="sxs-lookup"><span data-stu-id="ab473-219">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="ab473-220">萬用字元模式</span><span class="sxs-lookup"><span data-stu-id="ab473-220">Wildcard Pattern</span></span>
<span data-ttu-id="ab473-221">萬用字元模式由底線 (`_`) 字元和符合任何輸入，就像該變數的模式，不同之處在於輸入會捨棄而不是指派給變數。</span><span class="sxs-lookup"><span data-stu-id="ab473-221">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="ab473-222">萬用字元模式通常用於在其他模式內才能做為預留位置值右邊的運算式中不需要`->`符號。</span><span class="sxs-lookup"><span data-stu-id="ab473-222">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="ab473-223">萬用字元模式也經常使用的模式清單的結尾來比對任何不相符的輸入。</span><span class="sxs-lookup"><span data-stu-id="ab473-223">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="ab473-224">本主題中的許多程式碼範例會示範萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-224">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="ab473-225">請參閱上述的程式碼的其中一個範例。</span><span class="sxs-lookup"><span data-stu-id="ab473-225">See the preceding code for one example.</span></span>


## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="ab473-226">有類型註釋的模式</span><span class="sxs-lookup"><span data-stu-id="ab473-226">Patterns That Have Type Annotations</span></span>
<span data-ttu-id="ab473-227">模式可以有類型註釋。</span><span class="sxs-lookup"><span data-stu-id="ab473-227">Patterns can have type annotations.</span></span> <span data-ttu-id="ab473-228">這些行為與其他類型註釋一樣，引導推斷像其他類型註釋。</span><span class="sxs-lookup"><span data-stu-id="ab473-228">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="ab473-229">模式中的型別註解前後需要加括號。</span><span class="sxs-lookup"><span data-stu-id="ab473-229">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="ab473-230">下列程式碼會示範具有類型註釋的模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-230">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="ab473-231">類型測試模式</span><span class="sxs-lookup"><span data-stu-id="ab473-231">Type Test Pattern</span></span>
<span data-ttu-id="ab473-232">類型測試模式用來比對輸入對型別。</span><span class="sxs-lookup"><span data-stu-id="ab473-232">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="ab473-233">如果輸入的類型是符合項目 （或衍生型別） 在模式中，比對指定的型別將會成功。</span><span class="sxs-lookup"><span data-stu-id="ab473-233">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="ab473-234">下列範例會示範類型測試模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-234">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="ab473-235">Null 模式</span><span class="sxs-lookup"><span data-stu-id="ab473-235">Null Pattern</span></span>
<span data-ttu-id="ab473-236">Null 模式比對您正在使用 允許 null 值的類型，可能會出現 null 值。</span><span class="sxs-lookup"><span data-stu-id="ab473-236">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="ab473-237">與.NET Framework 程式碼交互作用時，通常會使用 null 的模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-237">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="ab473-238">.NET API 的傳回值，例如可能的輸入`match`運算式。</span><span class="sxs-lookup"><span data-stu-id="ab473-238">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="ab473-239">您可以控制是否傳回的值為 null，以及傳回值的其他特性為基礎的程式流程。</span><span class="sxs-lookup"><span data-stu-id="ab473-239">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="ab473-240">若要防止 null 的值傳播到其他的程式，您可以使用 null 的模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-240">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="ab473-241">下列範例會使用 null 的模式和變數的模式。</span><span class="sxs-lookup"><span data-stu-id="ab473-241">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="ab473-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab473-242">See Also</span></span>
[<span data-ttu-id="ab473-243">比對運算式</span><span class="sxs-lookup"><span data-stu-id="ab473-243">Match Expressions</span></span>](match-expressions.md)

[<span data-ttu-id="ab473-244">使用中模式</span><span class="sxs-lookup"><span data-stu-id="ab473-244">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="ab473-245">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="ab473-245">F# Language Reference</span></span>](index.md)
